# Summary

Much research on automated program debugging often assumes that bug fix location(s) indicate the faults’ root causes and that root causes of faults lie within single code elements (statements).
It is also often assumed that the number of statements a developer would need to inspect before finding the first faulty statement reflects debugging effort.
Although intuitive, these three assumptions are typically used (55% of experiments in surveyed publications make at least one of these three assumptions) without any consideration of their effects on the debugger’s effectiveness and potential impact on developers in practice.
To deal with this issue, we perform controlled experimentation, split testing in particular, using 392 bugs from 46 open-source C programs, 19 Automated Fault Localization (AFL) techniques (18 statistical debugging formulas and dynamic slicing), two (2) state-of-the-art automated program repair (APR) techniques (GenProg and Angelix) and 76 professional developers.
Our results show that these assumptions conceal the difficulty of debugging.
They make AFL techniques appear to be (up to 38%) more effective, and make APR tools appear to be (2X) less effective.
We also find that most developers (83%) consider these assumptions to be unsuitable for debuggers and perhaps worse that they may inhibit development productivity.
The majority (66%) of developers prefer debugging diagnoses without these assumptions twice as much as with the assumptions.
Our findings motivate the need to assess debuggers conservatively, i.e., without these assumptions.

<p style="position:fixed; left: 50%; top: 300px; transform: translate(-515px, 0%); width: 170px; padding: 0px">
<a href="#faq">FAQ</a><br/>
<a href="#setup">Setup</a><br/>
<a href="#cite">How to cite</a><br/>
<a href="artifact/ARTIFACT">Artifact Readme</a><br/>
<a href="artifact/DOCKER">Docker Readme</a><br/>
<a href="TODO">Download the Artifact</a><br/>
<a href="https://TODO" target="_blank"><img src="screenshots/paper.png" alt="Paper" style="width: 170px;"/></a></p>

<p align="center"><img src="mainobjective.png" alt="Main Objectives" width="100%" /></p>
<br/>

<p style="text-align: center;">
<img src="screenshots/workflow.png" alt="Workflow" width="500"/><br />
<i>Workflow of our approach</i>
</p>

<p style="text-align: center;">
<img src="screenshots/assumption_prevalence.png" alt="Prevalence in experiments" width="500"/><br />
<img src="screenshots/assumption_bugs.png" alt="Prevalence in bugs" width="500"/><br />
<i>Prevalence of the examined debugging assumptions in experiments (top) and bugs (bottom) in practice</i>
</p>

<p style="text-align: center;">
<img src="screenshots/venues.png" alt="Venues the examined literature was taken from" width="250"/><br />
<i>Venues we examined and collected literature from</i>
</p>

<p style="text-align: center;">
<img src="screenshots/benchmarks.png" alt="Benchmarks that were used in the AFL and APR experiments" width="500"/><br />
<i>Benchmarks that were used in the AFL and APR experiments</i>
</p>

## <a name="setup" /> Setup and Infrastructure

See _[how to set up and run the artifact (Artifact README)](artifact/ARTIFACT.md)_.

* **Download** the [artifact and datasets](todo) (MIT licensed)
* **Read** the [full paper](todo) (ICSE 2023)

# <a name="cite" /> How to cite?

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

### Cite the artifact

```bibtex
@article{debug-assumptions-artifact,
    author = "Ezekiel Soremekun and Lukas Kirschner and Marcel Böhme and Mike Papadakis",
    title = "{Debugging Assumptions Artifact}",
    year = "2023",
    month = "1",
    url = "https://figshare.com/articles/conference_contribution/Debugging_Assumptions_Artifact/21786743",
    doi = "10.6084/m9.figshare.21786743.v1"
} 
```

# Who are we?

# <a name="faq" /> FAQ

# Links
