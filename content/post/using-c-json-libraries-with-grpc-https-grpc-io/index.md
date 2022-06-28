---
title: Using C++ JSON Libraries with [gRPC](https://grpc.io/)
date: 2022-06-28T02:37:00.574Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
There are several separate C++ libraries that provide functionality for handling JSON data, namely [JsonCpp](https://github.com/open-source-parsers/jsoncpp) and [nlohmann/json](https://github.com/nlohmann/json). Until recently I had only been exposed to nlohmann/json, but I had to get up and running with JsonCpp due to its integration in the [Drogon](https://github.com/drogonframework/drogon) web development framework. Here are some of my thoughts on the matter.

**An introduction to gRPC is beyond the scope of what I intend to explain here**

## Context
The whole reason I am utilizing Drogon in my work is to build a RESTful interface to a gRPC client. Drogon provides the API endpoints that can be accessed from any device capable of sending a HTTP request, and behind-the-scenes a function call is made using gRPC. My implementation expects that the user sending the HTTP request passes a JSON representation of the gRPC message in the request. 
In Drogon it is possible to retrieve this JSON payload and store it for later use. 

```c++
//include JsonCpp and Drogon from somewhere
#include <json/json.h>
#include <drogon/drogon.h>

// Your handler function definition
void customHandleHttpRequest(const HttpRequestPtr &req,
std::function<void (const HttpResponsePtr &)> &&callback)

//store the json into a variable
Json::Value req_json = req->getJsonObject();

std::string string_json = req_json.toStyledString();
```
Once we have the JSON in a variable, we convert it into a string representation of the JSON object (see above), and then parse it into a gRPC message using a helper function provided by gRPC:
```c++ 
#include <google/protobuf/util/json_util.h>
util::Status google::protobuf::util::JsonStringToMessage(StringPiece input, 
	Message * message,const JsonParseOptions & options)
```
This function can take in a stringified version of a JSON object and populate a gRPC message. This is extremely powerful for uses in C++ where the "normal" API for adding to message fields is tedious (nested messages, many fields, etc.).

Later, when parsing a gRPC response, we can use the sister function to return to a JSON string:
```c++ 
util::Status google::protobuf::util::MessageToJsonString(const Message & message, 
	std::string * output, const JsonOptions & options)
```
In my work, I have found that specifying the (optional) JsonOptions is useful. By default, the `MessageToJsonString()` function only parses fields with non-null/empty data into the JSON string. In my case, I want these fields that are empty to be explicitly shown as empty so that they are returned in the HTTP response as empty.
The setting we need to edit to get this behavior is `always_print_primitive_fields`
```c++ 
google::protobuf::util::JsonOptions opts;
opts->always_print_primitive_fields = true;

std::string response_str;

MessageToJsonString(message, &response_str, opts);
```
Now we get all fields from the message parsed into the JSON string, even if they are null/empty.

From here, we need to parse this string back into a (JsonCpp) `Json::Value` object, and then send it to the user in the HTTP response.
```cpp
#include <json/reader.h>
//Make a Json::Reader (depricated but still working?
//Maybe use Json::CharReader instead)
Json::Reader reader;

Json::Value response;

//parse the JSON string into a Json::Value object
reader.parse(response_str,response);

//create the HTTP Response here
auto resp=HttpResponse::newHttpJsonResponse(response);

//Drogon will send the response
callback(response)
```
