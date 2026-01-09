# Post-Quantum Cryptography in Maude

This repository stores Maude's system modules that construct the symbolic models of four postquantum cryptography schemes. The selected schemes can be divided in two groups: Key Encapsulation Mechanisms (KEMs) and Digital Signature Algorithms (DSAs). The framework allows the user to perform invariant analysis, search of a Man In The Middle (MITM) attack, and model checking. The user can check *Liveness*, *Fairness* and *Security* for KEMs, and *Authentication*, *Integrity* and *Non-Repudiation* for DSAs.

The analyzed KEMs are:

- [Kyber](https://pq-crystals.org/kyber/)
- [Bike](https://bikesuite.org/)
- [Classic McEliece](https://classic.mceliece.org/)

The analyzed DSAs are:

- [Falcon](https://falcon-sign.info/)

Please check the corresponding [publication](https://ceur-ws.org/Vol-3280/paper3.pdf) for further insights on the symbolic specification and verification of Kyber. For a complete detailed explanation of the framework along with three use cases on KEMs, please see the [journal paper](https://peerj.com/articles/cs-1547/) of PeerJ Computer Science.

## Structure

The repository is divided into folders, one for each of the specified schemes. Each folder stores two kinds of files: one `txt` file and four `maude` files. The `txt` file contains basic information and a series of notations on the specified scheme. As an example, the `maude` files are:

- `SCH.maude`: Contains the full specification of a scheme using the framework.
- `SCH-PREDS` & `SCH-CHECK`: Contain the necessary modules to perform model checking with Maude. 
- `SCH-test.maude`: Stores a series of commands to (i) perform invariant analysis through the `search` command and (ii) verify properties with Maude's LTL Model Checker.

where `SCH` is either `kyber`, `bike`, `cm` or `falcon`, respectively, for each scheme.

## Reproducibility of experiments 

In order to perform invariant analysis and model checking one has to:

1. Install Maude 3.5. It can be downloaded from the official [Get Maude](https://maude.cs.illinois.edu/get-maude) webpage.
2. Download [this](https://github.com/v1ct0r-byte/PQC-in-Maude) repository and extract the contents.
3. Open a terminal in the parent folder of the downloaded repository.
4. Start Maude by following the [instructions](https://maude.lcc.uma.es/maude-manual/maude-manualch2.html#x13-220002.2). Maude can be initiated by running the `./maude.darwin64` on macOS.
5. Load a testing file with the command `load SCH-test.maude`, where `SCH` has to be either `kyber`, `bike`, `cm` or `falcon`. The code inside that file will perform the following commands.
    1. Invariant analysis with `search` commands.
    2. Model checking with `reduce` commands.
6. You can now check the results and compare.

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
