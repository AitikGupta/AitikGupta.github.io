---
title: VSCode GitHub Projects
layout: post
date: 2021-02-27 15:10
tag:
- TypeScript
- GraphQL
- Svelte
- Extension
image: https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/412/509/datas/original.png
headerImage: true
projects: true
description: Bringing GitHub Projects into VSCode - using GraphQL and Svelte
category: project
author: aitikgupta
about: true
code: https://github.com/MLH-Fellowship/vscode-github-projects
externalLink: false
---

#### This project was completed as a part of [Sprint 0 Hackathon](https://fellowship-explorer-0-batch-2.devpost.com/) conducted during the [MLH-Fellowship](http://fellowship.mlh.io/) (Spring 2021).
## Insipiration
There are several utilities from GitHub that makes collaboration easy, GitHub Projects is one of them. 

Currently, there is no UI-based extension that integrates GitHub Projects in VSCode. Hence, our team (Me, [Dean Gladish](https://github.com/gladishd), [Samuel Yuan](https://github.com/yuansamuel) and [Shrill Shrestha](https://github.com/shrillshrestha)) decided to make one.

#### A quick spoiler: we [won](https://devpost.com/software/vscode-github-projects)!
## Video Demonstration (YouTube)
<iframe width="100%" height="597" src="https://www.youtube.com/embed/MycrfrHHz18" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
## What are GitHub Projects?
GitHub Projects are divided into 3 scopes:
- User Scope
- Repository Scope
- Organisation Scope

One can create Kanban boards with any of these scopes to track the progress of a project. A typical card maintained on a project board can contain anything from a simple note to linked Issues and Pull Requests.
## What does the extension do?
The [extension](https://marketplace.visualstudio.com/items?itemName=Pod212.vscode-github-projects) we built communicates with GitHub's backend using GraphQL API - Queries and Mutations, to render a WebView built by Svelte on VSCode with it's native UI.
<p align="center">
 <img alt="Extension Screenshot" src="https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/412/508/datas/gallery.jpg"/>
</p>
<figcaption>Sample Screenshot</figcaption>
The result is an integration of realtime communication between VSCode native UI and GitHub Projects. It allows a user to:
1. View the Projects (with filtered scopes)
2. View the Project Boards
3. Add a Project Card
4. Delete a Project Card
5. Archive a Project Card
6. Move a Project Card to a different Column
7. Edit a Project Card (Only if it is a Note)
8. Convert a Project Card ** into an Issue**
9. Visit the web version of the linked Issues/Pull Requests

<p align="center">
 <img alt="Extension Screenshot" src="https://challengepost-s3-challengepost.netdna-ssl.com/photos/production/software_photos/001/412/509/datas/original.png"/>
</p>
<figcaption>Editing a Project Card</figcaption>
## How is it built?
- WebViews built with **Svelte**
- Queries/Mutations with GitHub using **GraphQL** (**Apollo client**)
- **Session-based** GitHub OAuth
- Communication with native VSCode APIs with **TypeScript**

<p align="center">
	<img alt="Extension Architecture" src="https://user-images.githubusercontent.com/43996118/108566810-06d0c580-732d-11eb-9d06-44023673c0db.png"/>
</p>
<figcaption>Software Architecture</figcaption>

<p align="center">
	<img alt="GraphQL Schema" src="https://user-images.githubusercontent.com/43996118/108566899-2c5dcf00-732d-11eb-8782-7862b3e3a32b.png"/>
</p>
<figcaption>GraphQL Schema</figcaption>
## How do I use it?
`VSCode-GitHub-Projects` is published to VSCode's Marketplace at this URL: [https://marketplace.visualstudio.com/items?itemName=Pod212.vscode-github-projects](https://marketplace.visualstudio.com/items?itemName=Pod212.vscode-github-projects)
## Roadmap/Code/Documentation
The repository is open sourced at MLH-Fellowship's [GitHub](https://github.com/MLH-Fellowship/vscode-github-projects).
