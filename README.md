# Summary

Much research on automated program debugging often assumes that bug fix location(s) indicate the faults’ root causes and that root causes of faults lie within single code elements (statements).
It is also often assumed that the number of statements a developer would need to inspect before finding the first faulty statement reflects debugging effort.
Although intuitive, these three assumptions are typically used (55% of experiments in surveyed publications make at least one of these three assumptions) without any consideration of their effects on the debugger’s effectiveness and potential impact on developers in practice.
To deal with this issue, we perform controlled experimentation, split testing in particular, using 352 bugs from 46 open-source C programs, 19 Automated Fault Localization (AFL) techniques (18 statistical debugging formulas and dynamic slicing), two (2) state-of-the-art automated program repair (APR) techniques (GenProg and Angelix) and 76 professional developers.
Our results show that these assumptions conceal the difficulty of debugging.
They make AFL techniques appear to be (up to 38%) more effective, and make APR tools appear to be (2X) less effective.
We also find that most developers (83%) consider these assumptions to be unsuitable for debuggers and, perhaps worse, that they may inhibit development productivity.
The majority (66%) of developers prefer debugging diagnoses without these assumptions twice as much as with the assumptions.
Our findings motivate the need to assess debuggers conservatively, i.e., without these assumptions.

<p style="position:fixed; left: 50%; top: 300px; transform: translate(-515px, 0%); width: 170px; padding: 0px">
<a href="#faq">FAQ</a><br/>
<a href="#short-abstract">Short Abstract</a><br/>
<a href="#setup">Setup</a><br/>
<a href="#cite">How to cite</a><br/>
<a href="artifact/ARTIFACT">Artifact Readme</a><br/>
<a href="artifact/DOCKER">Docker Readme</a><br/>
<a href="https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743">Download the Artifact</a><br/>
<a href="https://drive.google.com/file/d/1Q0lqaZtoC_rKP41RxyWshaNU-z9x49Wa/view?usp=sharing" target="_blank"><img src="screenshots/paper.png" alt="Paper" style="width: 170px;"/></a></p>

<br/>


# <a name="faq" /> FAQ

* [Where can I **download the ICSE 2023 presentation slides**?](slides/ICSE_2023_short.pptx)

* [Where can I **download the paper**?](https://drive.google.com/file/d/1Q0lqaZtoC_rKP41RxyWshaNU-z9x49Wa/view)

* [How do I **cite this paper/artifact**?](#cite)

* [How can I **learn more** about your research?](#learn)

* [I am in the **ICSE 23 AEC**. How do I **navigate this artifact**?](artifact/ARTIFACT)

* [How do I **install the Docker Image**?](artifact/DOCKER)

* [How do I **use the Docker Image**?](https://drive.google.com/file/d/17m_FcJZW3LxP9LrV16d-A5wdcfEvOhDu/view?usp=sharing)

* [How can I **reproduce this study** with other subjects, AFL/APR Tools, Programming languages or developers?](artifact/DOCKER)


* [Where can I **read about the artifact**?](https://drive.google.com/file/d/17m_FcJZW3LxP9LrV16d-A5wdcfEvOhDu/view?usp=sharing)



<br/> 

## <a name="short-abstract" /> Short Abstract

### Main Objective

A major challenge in automated debugging research is the practical evaluation of debuggers, e.g., automated fault localization (AFL) methods. Researchers make several experimental assumptions about debugging practice when evaluating debuggers *in the lab*. These includes assumptions about the debugging settings, e.g., bugs, programs and developers. Most common experimental assumptions include (a) perfect bug understanding (PBU), (b) using fix locations as root cause bug diagnosis, and (c) assuming a single fault location. These assumptions may impact the measured effectiveness of debuggers. Besides, they do not often align with debugging practice (e.g., developer’s expectations). Consequently, these assumptions often lead to a mismatch between debugging evaluations *in the lab* versus *software practice*.

To address these concerns, we study the impact of experimental assumptions in debugging practice using controlled experimentation. We conduct a large empirical study to evaluate the impact of the three aforementioned assumptions in debugging practice using controlled experimentation.

<br/>
 
### Experimental Approach
The main research method employed in this work is *controlled experimentation* (aka *split or A/B testing*). Our experiments involved controlled experiments with debuggers and developers. Controlled experimentation is widely used to test new features in software companies (e.g., Netflix and Google) to guide product development and data-driven decisions. To determine the prevalence of each assumption (RQ1), we perform data analysis and manual in-depth study of the literature and bug datasets. 

Here is a workflow of our experimental approach:

<p style="text-align: center;">
<img src="screenshots/workflow.png" alt="Workflow" width="800"/><br />
<i>Workflow of our approach</i>
</p>

<br/>

### Prevalence analysis
To evaluate the prevalence of the three assumptions in literature, we surveyed a large number of publications related to the topics of automated fault localization and automated program repair.

<p style="text-align: center;">
<img src="screenshots/venues.png" alt="Venues the examined literature was taken from" width="250"/><br />
<i>Venues we examined and collected literature from</i>
</p>


**Prevalence in Debugging Literature:** We found those assumptions to be highly prevalent in the existing literature: 55% of experiments in the surveyed publications make at least one of the three assumptions.

<p style="text-align: center;">
<img src="screenshots/assumption_prevalence.png" alt="Prevalence in experiments" width="500"/><br />
<i>Prevalence in Literature</i>
</p>

<br/>

**Prevalence in Bug Datasets:** Similarly, about half (49%) of the bugs in the bug datasets are impacted by at least one of the three assumptions.

<p style="text-align: center;">
<img src="screenshots/assumption_bugs.png" alt="Prevalence in bugs" width="500"/><br />
<i>Prevalence of in Bug Datasets</i>
</p>

<br/>

### AFL and APR Experiments

In a controlled experiment, we analyzed the effectiveness of 19 fault localization techniques under the presence and absence of these assumptions. We analyzed the impact of the assumptions on 2 popular automated program repair (APR) tools. We employed 4 bug datasets (CoreBench, SIR, IntroCLass and Codeflaws) including a high variance of bugs (real, seeded, mutated) and a varying complexity and maturity of programs.

<p style="text-align: center;">
<img src="screenshots/benchmarks.png" alt="Benchmarks that were used in the AFL and APR experiments" width="500"/><br />
<i>Benchmarks that were used in the AFL and APR experiments</i>
</p>

<br/>

### User Study

We conducted a user study with 76 developers to measure the *soundness*, *severity* and *utility* of these assumptions in practice.

In our [artifact](https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743), we provide the user study questionnaire containing the questions posed to developers about debugging eight (8) buggy programs and 16 debugging diagnoses. We also provide the responses of participants from the user study
as well as our analysis of developers’ responses.

<br/>

## <a name="setup" /> Setup and Infrastructure

See _[how to set up and run the artifact (Artifact README)](artifact/ARTIFACT.md)_.

* **Download** the [artifact and datasets](https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743) (MIT licensed)
* **Read** the [full paper](https://drive.google.com/file/d/1Q0lqaZtoC_rKP41RxyWshaNU-z9x49Wa/view?usp=sharing) (ICSE 2023)

<br/>

## <a name="cite" /> How to cite?


### Cite the Paper

```bibtex
@inproceedings{debug-assumptions, 
    author = {Soremekun, Ezekiel and Kirschner, Lukas and B\"{o}hme, Marcel and Papadakis, Mike}, 
    title = {Evaluating the Impact of Experimental Assumptions in Automated Fault Localization}, 
    booktitle = {Proceedings of the ACM/IEEE 45th International Conference on Software Engineering}, 
    series = {ICSE 2023}, 
    pages = {1-13}, 
    year = {2023},
}
```

### Cite the Artifact

```bibtex
@article{Soremekun2023,
    author = "Ezekiel Soremekun and Lukas Kirschner and Marcel Böhme and Mike Papadakis",
    title = "{Artifact for Evaluating the Impact of Experimental Assumptions in Automated Fault Localization}",
    year = "2023",
    month = "1",
    url = "https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743",
    doi = "10.6084/m9.figshare.21786743.v6"
} 
```
<br/>

#  <a name="learn" /> Who are we?

* [Ezekiel Soremekun](https://ezekiel-soremekun.github.io/), [Royal Holloway, University of London (RHUL)](https://www.royalholloway.ac.uk/), Egham, United Kingdom (UK) 
* [Lukas Kirschner](https://www.lukaskirschner.de), [Saarland University](https://www.uni-saarland.de/en/home.html), Saarbrücken, Germany
* [Marcel Böhme](https://mboehme.github.io/), [Max Planck Institute for Security and Privacy (MPI-SP)](https://www.mpi-sp.org/), Bochum, Germany
* [Mike Papadakis](https://mpapad.github.io/), [Interdisciplinary Centre for Security, Reliability and Trust (SnT)](https://wwwfr.uni.lu/snt), Luxembourg

<br/> 


# Links

The [ICSE 2023 presentation slides](slides/ICSE_2023_short.pptx), [artifact](https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743) and [abstract for the artifact](https://drive.google.com/file/d/17m_FcJZW3LxP9LrV16d-A5wdcfEvOhDu/view?usp=sharing) are publicly available. 

Previous related works on Automated Debugging:

* [EMSE 21: Locating Faults with Program Slicing: An Empirical Analysis](https://arxiv.org/pdf/2101.03008)

* [FSE 17: DBGBench](https://publications.cispa.saarland/1468/1/FSE17.pdf)

* [ICSE 23: Debugging Inputs](https://publications.cispa.saarland/3060/1/camera-ready-submission.pdf)



