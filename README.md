# Post-Quantum Cryptography in Maude

This repository stores Maude's system modules that construct the symbolic models of three postquantum cryptography schemes. Specifically, the selected schemes are Key Encapsulation Mechanisms (KEMs). The symbolic modules allow to perform invariant analysis, finding a MITM attack, and model checking of a Safety, Liveness and Fairness property. The analyzed KEMs are:

- [Kyber](https://pq-crystals.org/kyber/)
- [Bike](https://bikesuite.org/)
- [Classic McEliece](https://classic.mceliece.org/)

Please check the corresponding [publication](https://ceur-ws.org/Vol-3280/paper3.pdf) for further insights on the symbolic specification and verification of Kyber.

## Structure

==WIP==

The repository is divided in three main folders, one for each of the specified KEMs. Each folder stores two kinds of files: one txt file and three maude files. The txt file contains basic information and a series of commands to load the corresponding symbolic model, invariant analyisis and perform model checking. The maude files are the symbolic model and the required modules to carry on model checking.

## Reproduction of experiments 

==WIP==

In order to perform invariant analysis and model checking one has to:

1. Have Maude 3.3 installed. It can be downloaded from the oficial [download](http://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation) page.
2. Download [this](https://github.com/v1ct0r-byte/PQC-in-Maude) repository and extract the contents.
3. Open a terminal in the parent folder of the downloaded repository.
4. Start Maude by following the [instructions](https://maude.lcc.uma.es/maude-manual/maude-manualch2.html#x13-220002.2). Maude can be initiated by running the `./maude.darwin64`
5. Load an instruction file with command `load KEM-instructions.maude`, where `KEM` has to be either `kyber`, `bike` or `cm`. The instructions inside thta file will perform the following:
    1. Invariant analysis with the `search` commands.
    2. Model checking with the `reduce` commands.

## Results

==WIP==

The following table summarizes the results on each of the analysis.

<center>

| KEM | Correctness | MITM | SECURITY | KEY-SHARING | FAIRNESS |
| :- | :-: | :-: | :-: | :-: | :-: |
| KYBER | :heavy_check_mark: | :heavy_check_mark: | :x: | :x: | :x: |
| BIKE | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Classic McEliece | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

</center>
