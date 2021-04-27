---
title: SocioMark
layout: post
date: 2021-04-16 19:10
tag:
- FastAPI
- ReactJS
- MongoDB
- OpenCV
image: https://user-images.githubusercontent.com/43996118/115142703-cb1e5780-a060-11eb-8d85-79b35ee889a2.png
headerImage: true
projects: true
description: A social media platform that secures assets by embedding a personalised
  hash using steganography
category: project
author: aitikgupta
about: true
code: https://github.com/MLH-Fellowship/SocioMark
externalLink: false
---

#### This project was completed as a part of [Sprint 2 Hackathon](https://fellowship-explorer-2-batch-2.devpost.com/) conducted during the [MLH-Fellowship](http://fellowship.mlh.io/) (Spring 2021).
## Insipiration
##### Ending LinkedIn's famous HR story (38K - 25K) once and for all!
Data Authenticity on social media platforms these days is a joke. Plagiarism is widespread, as it takes almost no efforts to re-post someone else's post without their knowledge.

And that is precisely where SocioMark fits in.

> Imagine a social media platform that lets you upload images and secures them by embedding a personalised hash - such that your asset will always remain your asset, regardless of who posts it!

To build such a platform, our team (Me, [Bodhisha Thomas](https://github.com/bodhisha), [Deepak Agrawal](https://github.com/DebugAgrawal) and [Sumi Kolli](https://github.com/sgkolli535)) decided to collaborate over the last sprint of the MLH-Fellowship.
#### A quick spoiler: we [won](https://devpost.com/software/sociomark)!

<p align="center">
 <img alt="SocioMark Landing Page" src="https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/472/914/datas/gallery.jpg"/>
</p>
<figcaption>SocioMark Landing Page</figcaption>
## Video Demonstration (YouTube)
<iframe width="100%" height="597" src="https://www.youtube.com/embed/1J6-tyKmhdc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
## Generic Social Media Features
Like any other social media platform, SocioMark provides users ability to:
- Register
- Login/Logout
- Search Profiles
- Visit Profiles
- Edit own Profile
- Create Posts
- Edit own Post
- Like/Dislike Posts
- Comment on Posts
- Report Posts

<p align="center">
 <img alt="User Profile" src="https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/472/922/datas/gallery.jpg"/>
</p>
<figcaption>User Profile (and Post)</figcaption>

However, apart from these generic features, one special feature that SocioMark provides is:
- **Verify Posts**

## What does Verify do?
When a user creates a post with an image asset, the user's unique id from the database is encrypted via SHA and a `unique 256-bit binary number` is generated, which is ultimately embedded onto the image.

#### Embedding is done using a combined DCT-DWT Algorithm via an Arnold Transformation on the image. 

### Why DCT-DWT?
Watermarking an image (embedding some information) can be done via 2 ways:
1. Spatial Domain (**Least Significant Bits** - *LSB*)
2. Frequency Domain (**Discrete Cosine Transform** - *DCT*, **Discrete Wavelet Transform** - *DWT*)

In the spatial domain, the classic LSB supports a large amount of watermark information and has little impact on the original image. However, the **`anti-interference ability is relatively poor and cannot resist image cropping, scaling and jpg compression`.**

In the frequency domain, such as DCT and DWT, the algorithms have **`strong anti-interference ability`**.

> Which means even if we attack the image by compressing/adding artifacts to the image - the information embedded in the image will still retain!

<p align="center">
 <img alt="Information Retention" src="https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/472/915/datas/gallery.jpg"/>
</p>
<figcaption>Information retained even after an attack</figcaption>

## Tech Stack
To give birth to this platform, we used FARM Stack:-

`(Fa)stAPI - Server, (R)eactJS - Client, (M)ongoDB - Database`

Being a Python backend and a Javascript frontend, both are deployed and maintained separately
on [Heroku](http://sociomark-backend.herokuapp.com/) and [Netlify](https://sociomark.netlify.app/) respectively.

- `Cloudinary` - The database to store the images
- `MongoDB Atlas` - The database to store the users, posts, comments and likes 

<p align="center">
 <img alt="Database Schema" src="https://user-images.githubusercontent.com/43996118/113485308-74dedf80-94ca-11eb-859d-baf1858d743f.png"/>
</p>
<figcaption>Database Schema</figcaption>

The backend endpoints, their routes, their model schemas, and their controllers are all implemented in Python using [FastAPI](https://fastapi.tiangolo.com/).

<p align="center">
 <img alt="Server Endpoints" src="https://user-images.githubusercontent.com/43996118/113442161-2fa8a800-940d-11eb-8e3c-87d1184a9f8e.png"/>
</p>
<figcaption>Server Endpoints</figcaption>

## End Notes
SocioMark is a <ins>Progressive Web Application</ins> (it can be *installed* on devices!), is completely <ins>Responsive</ins> (it works on mobile devices!) - and *ensures* Data Authenticity throughout the platform.

<p align="center">
  <img alt="Mobile PWA" src="https://user-images.githubusercontent.com/34866653/114988100-8dc89700-9eb3-11eb-892a-217aa0b5622c.jpg" width="45%">
  <img alt="Desktop PWA" src="https://user-images.githubusercontent.com/34866653/114988153-a0db6700-9eb3-11eb-81d8-1a84eae83aa3.png" width="45%">
</p>
<figcaption>PWA Setup (Mobile/Desktop)</figcaption>

## Roadmap/Code/Documentation
With more than ~60 closed Pull Requests and ~70 closed Issues across 4 core developers and 5 contributors, the repository is open sourced at MLH-Fellowship's [GitHub](https://github.com/MLH-Fellowship/SocioMark).
