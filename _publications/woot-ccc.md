---
title: "Distributed Password Hash Computation on Commodity Heterogeneous Programmable Platforms"
collection: publications
permalink: /publication/woot-ccc
#excerpt: 'This paper is about the number 1. The number 2 is left for future work.'
date: 2019-08-13
venue: '13th {USENIX} Workshop on Offensive Technologies ({WOOT} 19)'
paperurl: 'https://www.usenix.org/conference/woot19/presentation/pervan'
#citation: 'Your Name, You. (2009). &quot;Paper Title Number 1.&quot; <i>Journal 1</i>. 1(1).'
---
<!--[Download paper here](https://www.usenix.org/conference/woot19/presentation/pervan)-->

In this paper, we present the Cool Cracker Cluster cCc: a heterogeneous distributed system for parallel, energy-efficient, and high-speed bcrypt password hash computation. The cluster consists of up to 32 heterogeneous nodes with Zynq-7000-based SoCs featuring a dual-core, general-purpose ARM processor coupled with FPGA programmable logic. Each node uses our custom bcrypt accelerator which executes the most costly parts of the hash computation in programmable logic.

We integrated our bcrypt implementation into John the Ripper, an open source password cracking software. Message Passing interface (MPI) support in John the Ripper is used to form a distributed cluster. We tested the cluster, trying different configurations of boards (Zedboards and Pynq boards), salt randomness, and cost parameters finding out that password cracking scales linearly with the number of nodes. In terms of performance (number of computed hashes per second) and energy efficiency (performance per Watt), cCc outperforms current systems based on high-end GPU cards, namely Nvidia Tesla V100, by a factor of 2.72 and 5 respectively.

    @inproceedings{WOOT19,
        title={Distributed Password Hash Computation on Commodity Heterogeneous Programmable Platforms},
        author={Pervan, Branimir and Knezovic, Josip and Pericin, Katja},
        booktitle={13th $\{$USENIX$\}$ Workshop on Offensive Technologies ($\{$WOOT$\}$ 19)},
        year={2019},
        organization={USENIX}
    }