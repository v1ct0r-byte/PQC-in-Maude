# Post-Quantum Cryptography in Maude

This repository stores Maude's system modules that construct the symbolic models of three postquantum cryptography schemes. Specifically, the selected schemes are Key Encapsulation Mechanisms (KEMs). The symbolic modules allow us to perform invariant analysis, find a Man In The Middle (MITM) attack, and model checking of Liveness, Fairness and Security properties. The analyzed KEMs are:

- [Kyber](https://pq-crystals.org/kyber/)
- [Bike](https://bikesuite.org/)
- [Classic McEliece](https://classic.mceliece.org/)

Please check the corresponding [publication](https://ceur-ws.org/Vol-3280/paper3.pdf) for further insights on the symbolic specification and verification of Kyber.

For a complete detailed explanation of the framework along with three use cases with the above mechanisms, please see the [journal paper]() of PeerJ Computer Science.

## Structure

The repository is divided into three main folders, one for each of the specified KEMs. Each folder stores two kinds of files: one `txt` file and four `maude` files. The `txt` file contains basic information and a series of notations on the specified KEM. The `maude` files are:

- `KEM.maude`: Contains the full specification using the framework.
- `KEM-PREDS` & `KEM-CHECK`: Contain the necessary modules to perform model checking with Maude. 
- `KEM-test.maude`: Stores a series of commands to (i) perform invariant analysis through the `search` command and (ii) verify three properties with the LTL Model Checker.

where `KEM` is either `kyber`, `bike` or `cm` respectively for each selected protocol.

## Reproduction of experiments 

In order to perform invariant analysis and model checking one has to:

1. Have Maude 3.3 installed. It can be downloaded from the official [download](http://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation) page.
2. Download [this](https://github.com/v1ct0r-byte/PQC-in-Maude) repository and extract the contents.
3. Open a terminal in the parent folder of the downloaded repository.
4. Start Maude by following the [instructions](https://maude.lcc.uma.es/maude-manual/maude-manualch2.html#x13-220002.2). Maude can be initiated by running the `./maude.darwin64`
5. Load an instruction file with the command `load KEM-instructions.maude`, where `KEM` has to be either `kyber`, `bike` or `cm`. The instructions inside that file will perform the following:
    1. Invariant analysis with the `search` commands.
    2. Model checking with the `reduce` commands.

<!---
## Results

The following table summarizes the results of each of the analyses.

<center>

| KEM | Correctness | MITM | SECURITY | KEY-SHARING | FAIRNESS |
| :- | :-: | :-: | :-: | :-: | :-: |
| KYBER | :heavy_check_mark: | :heavy_check_mark: | :x: | :x: | :x: |
| BIKE | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Classic McEliece | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

</center>
