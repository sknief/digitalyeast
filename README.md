# Digital Yeast : A Digital Model Organism for SLiM 3

 - - - -

## For SCIE3241 Assessment Purposes: Record Keeping

At the start of the semester, Daniel and I agreed that my lab notebook would be a good way for me to keep track of my project, but noew that the project is completed, I have decided to submit my repository and github history in addition to a scan of my labnotebook, which can be found [Here](addlinklater). 

My project is pretty much 90% coding, as such, my [GitHub commit history]() (which shows every update and every change I have made to my code since I started working on the code) is an accurate reflection of my work effort and the process that lead to the creation of "Digital Yeast". My project is not based in a physical lab, so I cannot write down experimental procedures and concrete results - instead my work process was conceptualizing what I wanted to achieve, trying to understand how I could turn this concept into code, and then a lot of trial and error, and repeat. 

The coding language used (Eidos) and the program used (SLiM) was completely new to me, so the first month of my research was trying to understand the basics of the language and program and understand the biological background for my genetic model. A lot of the learning period and all of my conceptualizing and thought processes are recorded in my lab notebook. The code and the physical evidence of my work is recorded here - my GitHub is what experts in this field would look at, whereas my lab notebook is important only for people who want to follow my conceptualization process (and as such has turned a little bit messy at time, I apologize). Therefore, the complete picture can only be painted when considering both. 

Also, there is a marked gap in my lab notebook around mid to late April. At the height of the initial COVID-19 uncertainty, I had a very hard time focusing and my mental health took quite a hit. I could not work on research in this time period, so please excuse the gap - it is not a lack of record keeping but a lack of research activities. 

The rest of this page is the Read Me for my code, and may provide a good introduction to my project / code before exploring my GitHub history and my labnotebook scan. 

- Stella

 - - - -

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

DY is highly customizable without even having to modify the core coding body. At the start of the SLiM script, you will find this block of code:

```
//CONSTANTS TO DEFINE : USER INPUT here
    defineConstant("P", 10); //initial population size
    defineConstant("K", 100); //carrying capacity
    defineConstant("glucose", 0.5); //extracellular glucose
    defineConstant("galactose", 20.0); //High: >25, Low <5, None = 0
    defineConstant("SP", 0.1); //Selective pressure scalar, 0.1 is standard, increase for higher selective pressure
    defineConstant("L", 3); //lethal mutation cutoff number for individual gene binding affinity
     defineConstant("LL", 7); //lethal mutation cutoff number for network function
    defineConstant("CisMu", 1e-5); //mutation rate of cis element
    defineConstant("TransMu", 1e-5); //mutation rate of trans ELEMENTS
    defineConstant("G1Mu", 1e-5); //mutation rate of noncoding regions
    //note: the next three have to add up to 1
    defineConstant("PDelRatio", 0.25); //proportion of deleterious mutations generated in promoter region
    defineConstant("PBenRatio", 0.15); //proportion of beneficial mutations generated in promoter region
    defineConstant("PNeuRatio", 0.6); // proportion of neutral mutations generated in promoter region
    //note: these next three also have to add up to 1
    defineConstant("CDelRatio", 0.25); //proportion of deleterious mutations generated in coding region
    defineConstant("CBenRatio", 0.15); //proportion of beneficial mutations generated in coding region
    defineConstant("CNeuRatio", 0.6); // proportion of neutral mutations generated in coding region

```
To change any of these parameters, simply edit the number within the brackets. Each line of code is annotated with the function and any important information relating to these parameters. At the start of each simulation run, these parameters are printed - this makes it easier for users to save the total output of a simulation run including the parameters that led to this output. 

Take care to not remove the // of each line; if you do, the simulation will display an error message. 


### Sample Output

Any given simulation run might produce output similar to the following. Note that this is not the complete output, but simply a fraction of the output. 

```
// Starting run at generation <start>:
1 

List of Parameters: 

Initial Population Size: 10
Carrying Capacity: 100
Initial Extracellular Glucose Level: 0.5
Initial Extracellular Galactose Level: 20
Selective Pressure Scalar: 0.1
Lethal Mutation Cut Off #: 3
Lethal Total Network Cut Off #: 7
Cis Mutation Rate: 1e-05
Trans Mutation Rate: 1e-05
Non Coding Mutation Rate: 1e-05
Ratio of N:D:B mutations in promoter regions : 0.60.250.15
Ratio of N:D:B mutations in coding regions : 0.60.250.15


End initial output


Generation: 100
Mean network binding affinity: 1.1




Generation: 200
Mean network binding affinity: 0.683333


GAL1 lethal mutation. Individual 777 died in generation 243
Network functionality too low. 777 died in generation 243
GAL3 semi-lethal mutation. Individual 830 reduced fitness after generation 250
GAL3 semi-lethal mutation. Individual 830 reduced fitness after generation 251
GAL4 lethal mutation. Individual 854 died in generation 254
GAL4 lethal mutation. Individual 854 died in generation 255
GAL4 lethal mutation. Individual 854 died in generation 256
GAL4 lethal mutation. Individual 854 died in generation 257
GAL4 lethal mutation. Individual 854 died in generation 258
GAL4 lethal mutation. Individual 1093 died in generation 285
GAL4 lethal mutation. Individual 1093 died in generation 286


Generation: 300
Mean network binding affinity: 0.53012


GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 302
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 303
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 304
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 305
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 306
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 307
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 307
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 308
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 308
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 309
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 309
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 310
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 310
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 311
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 311
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 312
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 312
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 313
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 313
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 313
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 314
GAL3 semi-lethal mutation. Individual 1262 reduced fitness after generation 314
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 314
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 315
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 315
GAL3 semi-lethal mutation. Individual 1214 reduced fitness after generation 316
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 316
GAL3 semi-lethal mutation. Individual 1333 reduced fitness after generation 316
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 317
GAL3 semi-lethal mutation. Individual 1333 reduced fitness after generation 317
GAL3 semi-lethal mutation. Individual 1347 reduced fitness after generation 317
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 318
GAL3 semi-lethal mutation. Individual 1333 reduced fitness after generation 318
GAL3 semi-lethal mutation. Individual 1347 reduced fitness after generation 318
GAL3 semi-lethal mutation. Individual 1315 reduced fitness after generation 319
GAL3 semi-lethal mutation. Individual 1333 reduced fitness after generation 319
GAL4 lethal mutation. Individual 1369 died in generation 319

```





## Additonal Notes 

This project was created for SCIE3241, a research course offered at the University of Queensland. I am part of the Ortiz-Barrientos Lab Group at UQ, under supervision of Daniel Ortiz-Barrientos. This code is currently a pre-release and as such might be modified / gain a few additional features before public release. 

## Built With

* [SLiM 3](https://github.com/MesserLab/SLiM)

## Contributing

Currently I do not accept any contributions to this project. This section will be updated if that changes. 

## Versioning

I use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/sknief/digitalyeast/tags). 

The current version is v1.0-alpha.

## Authors

* **Stella Maria Sophie Knief** - *Sole Author and IP Holder* - [GitHub](https://github.com/sknief)

## License

No license as of yet. 

## Acknowledgments

* Nick O'brien for his helpful feedback.
* Daniel Ortiz-Barrientos for his feedback and for taking me on as a supervisor.


-----------------------------------------------------------------------------------------------------------------------------------
