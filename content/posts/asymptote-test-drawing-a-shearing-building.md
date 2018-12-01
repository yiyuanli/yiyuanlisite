---
author: liyiyuan
comments: true
date: 2016-11-23 09:36:46+00:00
title: Asymptote Test - Drawing a Shearing Building
---

In order to test Asymptote, an 18-story shear building is created. 
The code and the graph it generated are shown below.

```asymptote
size(200);
int n=18;

for(int i=0;i<n;++i){
draw((0,(i-1))--(0,(i-0.2))--(4,(i-0.2))--(4,(i-1)),black+0.2mm);
filldraw((0,(i-0.2))--(0,i)--(4,i)--(4,(i-0.2))--cycle,
fillpen=grey,drawpen=black+0.2mm);
}

draw((-2,-1)--(6,-1),black+0.2mm);

import patterns;
add("hatch",hatch(2.5m,NW,black+0.15mm));
fill((-2,-1.5)--(-2,-1)--(6,-1)--(6,-1.5)--cycle,pattern("hatch"));
```

Run the program, then the shear building graph is shown below:    

![18-story shear building](https://raw.githubusercontent.com/yiyuanli/markdown_image/master/img/18story_shear_building.png)

