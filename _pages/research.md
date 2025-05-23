---
layout: page
title: research
permalink: /research/
description: Thoughs on foundations that I'm trying to build my research upon.
nav: true
nav_order: 3
---

### Preface

Take a good look at your surroundings. A lot of things probably could be defined as _smart_, and if not yet defined as smart, there is a great probability that it will be in near future. From the other point of view, it seems that artificial intelligence-related buzzwords such as machine learning, neural network, and whatnot gained so much traction that they are practically unavoidable if one is trying to do something in the world of computer science. The bottom line is the following: for something to be _smart_, there has to be some processing that makes it that way, be it machine learning models, neural networks, and whatnot. Data being processed is acquired from our environment, and as we advance as humanity, the amount of data that we collect per unit of time gets bigger and bigger. Translated, smartness requires processing power. A lot of it. This brings up two ground topics: performance and energy efficiency.

### Parallelism

According to its creator, Moore's law is dead \[1\]. Furthermore, the perceived exponential growth of the effective computing power faded away by hitting three walls: The power wall, the Instruction-Level Parallelism wall, and the Memory wall \[2\]. We have basically become limited by the bare physics models that we are aware of at this point in time. To stretch the silicon as we know it today further and increase performance, we, therefore, have to go multicore and to efficiently exploit those multicores, we have to go parallel. But (there is always a "but"), this is far from easy. Algorithms developed so far usually do not imply parallel execution, and computer science curricula in universities usually teach sequential thinking and programming \[3\].

These are some of the reasons why I try to incorporate parallelism in my research. I do so by studying parallel processing both on the hardware and software layers and parallel programming as means to increase the performance and energy efficiency of the available silicon.

### Heterogeneous computing systems

Heterogeneous as a word, stemming both from Latin and Greek, by definition means _consisting of dissimilar or diverse ingredients or constituents_ \[4\]. Diverse or dissimilar components in the context of computing systems usually imply processing units of different purposes, most commonly combinations of a general-purpose processor paired with a general-purpose graphics processing unit or a customized accelerator for a specific application. Heterogeneity is according to some authors one of the key development points in reaching and maintaining the efficient Exascale domain \[5\]. Nearly 30% of the systems featured by the Top500 list use the accelerator or co-processor technology \[6\].

While providing much value to performance and energy efficiency, such systems bear their own set of problems, the first of which is programmability. Often, low-level knowledge of architectural details of the system programmed is needed, and more than often such systems are being programmed in low-level languages with little to none of the nowadays standard programming aids. Regarding heterogeneous systems, I'm mostly aiming for research that eases the development of a wide variety of such systems, with the ultimate goal of providing a _lingua franca_.

### Software engineering

As I stated before, one of the main challenges that highly parallel and / or heterogeneous systems bear with them is programmability. In the field of software engineering, I'm interested in delivering programming models that allow programmers to efficiently express themselves with respect to the computations that need to be done on systems while abstracting their low-level architectural details. That can be achieved by numerous ways, some of them being by the means of augmenting existing languages with constructs that aid programming of such systems, delivering a domain-specific language which is for me of particular interest, or by developing a completely new language. I'm also interested in developing and optimizing software for high-performance computers, and development of applications for heterogeneous systems.

While I still develop software for conventional machines ocasionally, I'm not particularly interested in it in a scientific way.

### Embedded computing

Embedded computing is a field in which energy efficiency is of particular importance. Embedded computers often drive modules and systems that are battery-powered and thus significantly energy-constrained. In that context, I'm interested in developing and utilizing energy-efficient systems for edge computing that do not serve as data collectors or actuators exclusively but process some of the data on themselves. Accelerators for specific applications which make the most out of the available energy are one possible way to achieve such a paradigm.

#### Note: Open systems

I'm not scientifically interested in open systems, but I have to mention that all of the aforementioned paradigms and technologies should be driven by open standards and permissive licenses, cherishing the values of personal liberty and privacy.

#### Refs

\[1\] IEEE Spectrum, “Gordon Moore: The Man Whose Name MeansProgress”, \[Online\]. Available: https://spectrum.ieee.org/gordon-moore-the-man-whose-name-means-progress (July 9 2022.).

\[2\] Manferdelli, J., Govindaraju, N., and Crall, C., “Challenges and Opportunities in Many-Core Computing”, Proceedings of the IEEE, vol. 96, no. 5, may 2008, pp. 808–815, \[Online\]. Available: http://ieeexplore.ieee.org/document/4484943/

\[3\] Silver, A., “Rethinking CS101 \[Resources_Education\]”, IEEE Spectrum, vol. 54, no. 4, apr 2017, pp. 23–23, \[Online\]. Available: http://ieeexplore.ieee.org/document/7880452/

\[4\] https://www.merriam-webster.com/dictionary/heterogeneous

\[5\] Schulte, M. J., Ignatowski, M., Loh, G. H., Beckmann, B. M., Brantley, W. C., Gurumurthi, S., Jayasena, N., Paul, I., Reinhardt, S. K., and Rodgers, G., “Achieving Exascale Capabilities through Heterogeneous Computing”, IEEE Micro, vol. 35, no. 4, 2015, pp. 26–36.

\[6\] TOP500.org, “TOP500 Expands Exaflops Capacity Amidst Low Turnover", \[Online\]. Available: https://www.top500.org/news/top500-expands-exaflops-capacity-amidst-low-turnover/ (December 9 2021.).
