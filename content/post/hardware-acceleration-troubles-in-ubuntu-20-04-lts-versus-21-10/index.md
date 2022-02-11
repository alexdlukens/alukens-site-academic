---
title: Hardware Acceleration Troubles in Ubuntu (20.04 LTS versus 21.10)
date: 2022-02-11T18:17:24.097Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
I have recently come across difficulties in utilizing hardware acceleration on Ubuntu 20.04. There are several guides online on how to enable acceleration on Intel GPUs, but in the end I did a distribution upgrade to Ubuntu 21.10 which immediately rectified my issues. Upon switching, hardware acceleration worked perfectly in Firefox. 

I believe this has something to do with Ubuntu's switch from X.Org to Wayland by default, and how this interacts with the GPU. Needless to say, I will remain on 20.04 LTS for my desktop where hardware acceleration is less of an issue, but 21.10 on my laptop where power savings is critical. Hopefully the next LTS release of Ubuntu clears this all up.