# Digital Yeast : A Digital Model Organism for SLiM 3

## What is "Digital Yeast"?

Digital Yeast (DY) is the first functional virtual model organism created for SLiM 3. It encompasses the the GAL Switch of Saccharomyces cerevisiae as the chosen model network. While only the GAL Switch is explicitly modelled in terms of focal genes and network structure, this system operates within the biological constraints of S. cerevisiae and reproduces sexually in a density-dependent matter as diploid yeast would. 

Essentially, you can think of individual simulation runs of DY as monitoring a petridish of S. cerevisiae in the lab! 

## Why use Digital Yeast?

The GAL switch is a complex but well-studied network that regulates the uptake of extracellular galactose when the main metabolic substrate, glucose, is at low levels or unavailable. It consists of 8 core genes of which four are cis-acting and four are trans-acting. This network structure lends itself to studies exploring genetic network function, polygenic trait adaptation, cis/trans element function, environmental selection pressure and many more areas! 

A genetic modeling approach enables faster data generation in a highly customizable framework made for exploration of genetic theory. DY may serve as a null model / null hypothesis to understand expected behaviour before discriminating observed behaviour, or DY may be used as a data generation tool of it's own. Not to mention, that this approach is more accessible to a wide variety of researchers to due it's ease of use and ability to be used anywhere. Especially in the current world state, with COVID-19 forcing many of us to isolate at home, the accessibility of genetic modeling is more apparent than ever. 

## Functions and Features

* A wide range of initial model parameters that may be set by the user (see Using Digital Yeast, Initial Parameters), including but not limited to: 
    * Initial population size
    * Carrying capacity
    * Extracellular levels of glucose and galactose (leading to environment dependent fitness scaling)
    * Selective pressure scalar (environment independent)
    * Cis mutation rate
    * Trans mutation rate
    * Ratio of beneficial:deleterious:neutral mutations
* Spatial Visualisation of individials, fashioned to resemble a petridish in a lab
* Extracellular environment impacts selection pressure (levels of glucose and galactose present)
* Each individual is assigned an individual ID, allowing for tracking of focal individuals if so desired
* Density-dependent mortality, representing competition for resources
* Density-dependent reproduction, where success is based on spatial distance between closest neighbouring individual
* Genome structures after S. cerevisiae chromosomes, with visually and mechanistically distinct cis- and trans-acting genes
* Fitness-based mortality as a balance of beneficial and delterious mutations 
* Individual gene-based lethal and semi-lethal mutations fashioned after real life S. cerevisiae using reported lethal knockout genes
* Output generation if any of these lethal or semi-lethal mutations occur with individual ID and generation of death
* Conditional mortality if the entire network accumulates too many deleterious mutations, representing a decline in binding affinity
* Live plotting graph of generation time vs network function ie total network binding affinity (plot may be exported)


## Getting Started

Digital Yeast is extremely easy to use for your own projects and studies. 

### Prerequisites

* R (latest Release)
* SLiM 3 (DY is incompatible with SLiM 2 or SLiM 1)

SLiMGui is recommended for best user experience. 

Once everything is installed, open SLiMGui (or SLiM from your command line if not using SLiMGui) and open "nonWF Model (Completed).slim" from this repository (found in the Completed Code folder). 


## Using Digital Yeast

### Initial Parameters

Explain what these tests test and why

```
Give an example
```

### Sample Output

Explain what these tests test and why

```
Give an example
```


## Additonal Notes 

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc

-----------------------------------------------------------------------------------------------------------------------------------
