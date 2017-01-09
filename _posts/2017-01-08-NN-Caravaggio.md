---
layout: post
title: Can AI easily mimic Caravaggio?
tags: [Blog]
---
Artificial Intelligence technology performed an awesome show last year. Mimicking artistic style of Fine Art is surprisingly successful, which can be obviously proved by the popularity of a photo-editing application, [Prisma](http://prisma-ai.com/){:target="_blank"} .


<center><img src="http://gytcrt.github.io/public/img/01-18-nn/prisma.jpg" alt="Prisma Image" style="width: 500px;"/></center>
<center> Picture edited by Prisma</center><br>

The key algorithm of mimicking artistic style is [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network){:target="_blank"} , and this paper, [Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576){:target="_blank"} , elaborates the details of implementing neural networks. There are some open-source implementations of this algorithm on Github, like [this](https://github.com/jcjohnson/neural-style){:target="_blank"}  and [this](https://github.com/anishathalye/neural-style){:target="_blank"} . These guys have done good job, and most of images they got are pretty fancy and fantastic.

For example, [Anish Athalye](http://www.anishathalye.com/2015/12/19/an-ai-that-can-mimic-any-artist/){:target="_blank"} used these two images to produce a new image with [Leonid Afremov](https://afremov.com/){:target="_blank"}  style.

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/rain-princess.jpg" alt="Rain Princess" style="width: 500px;"/></center>
<center> Rain Princess by Leonid Afremov</center><br>

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/dome.jpg" alt="Demo" style="width: 500px;"/></center>
<center> A photo of a dome</center><br>

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/dome-afremov.png" alt="Demo with Afremov's style" style="width: 500px;"/></center>
<center> The dome with Afremov's style</center><br>

Given the open-source implementation and the amazing result, I was definitely eager to mimic more masterpieces. Therefore, I installed [neural style](https://github.com/anishathalye/neural-style){:target="_blank"} , and tried to combine my picture with [Caravaggio](https://en.wikipedia.org/wiki/Caravaggio){:target="_blank"} ’s style.

The original photo: my teammates and I were working for [Datafest competition 2016](http://www2.stat.duke.edu/datafest/){:target="_blank"}

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/datafest.jpg" alt="datafest" style="width: 500px;"/></center>
<br>

Caravaggio's work, which I used to learn his style from:

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/Cena_in_Emmaus.jpg" alt="supper" style="width: 500px;"/></center>
<center> The Supper at Emmaus </center><br>
<center><img src="http://gytcrt.github.io/public/img/01-18-nn/John.jpg" alt="john" style="width: 500px;"/></center>
<center> John in the Wilderness </center><br>
<center><img src="http://gytcrt.github.io/public/img/01-18-nn/Taking_of_Christ.jpg" alt="datafest" style="width: 500px;"/></center>
<center> The Taking of Christ </center>
<br>

However, it took my mac pro about 12 hours to run 100 iterations, and I don’t think the result is similar to any Caravaggio’s work at all (

<center><img src="http://gytcrt.github.io/public/img/01-18-nn/neural-datafest.jpg" alt="neural datafest" style="width: 500px;"/></center>


I think the problem is this algorithm is good at capturing styles of modern artists like Van Gogh and Claude Monet because the way they used color and brush are very characteristic. While what makes Caravaggio stand out is how he portrayed varies religious figures by realistic observation of physical and emotional human states and dramatic use of lighting. In addition, Caravaggio is also the best story teller in Fine Art history. Therefore, the styles of classical artists are harder to mimic for present AI technology because of their intricacy and delicacy.

Can AI easily easily mimic artists like Caravaggio? My answer is: we still have a long way to go.
