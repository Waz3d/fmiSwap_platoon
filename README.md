Credit goes to "Dynamic Runtime Integration of New Models in Digital Twins" [H. Ejersbo, K. Lausdahl, M. Frasheri, L. Esterle] for developing and explaining the fmiSwap artifact. This repository contains modifications made to test the fmiSwap artifact with a different case study.

This repository elongs to Alessio Vivani.
The file fmiSwap-Questions.pdf contains a brief explanation of the system under analysis together with a set of questions that aim at better understanding how to properly use the fmiSwap artifact.

## Remember to read the pdf fmiSwap-withQuestions.pdf!

## The test
This repository contains a set of FMUs related to a platoon of 4 vehicles, one of which being the leader. Each vehicle, expect for the leader, is composed of 2 FMUs, one for the plant (SimpleCarX.fmu) and one for the controller (__caccAlg_X.fmu), which implements the CACC Algorithm in order to ensure that each vehicle can follow the platoon but keeping a safe distance with respect to the preceding car.

In the test we created 2 multi models, found in mm1.json and mm2.json. The case study refers to a platoon that, after some time, gets attacked and through the swapFmi artifact we would like to swap to a system that has a mitigation mechanism to contrast the attacker. The attack under analysis consists in the alteration of the value of the acceleration sent by the leader to the SimpleCar1. The mitigation, implemented in cacc1_mitigated, consists simply in assuming the values obtained by the sensors to be sufficiently accurate and trustworthy, thus making it possible to simply change the value of the acceleration obtained by the leader to the value observed through the sensors.

The attack should be injected using the wt_fault.xml file (yet to implent).

mm2.json contains informations related to the required swap, that will change __caccAlg_01.fmu with cacc1_mitigated.fmu.

## Repeat the test on your device

## Clone this repo

Clone this repo locally

```bash
$ git clone https://github.com/Waz3d/fmiSwap_platoon
```

Change to the repo directory before going to the next step:

```bash
$ cd fmiSwap_platoon
```

## Build the image

```bash
$ docker build . --tag lausdahl/maestro:2.3.0-model-swap
```

## Run the example

```bash
$ docker run -it -v ${PWD}:/work/model/post  lausdahl/maestro:2.3.0-model-swap
```

After this step completes, you should see in the containing folder two files ```result.png``` and ```result.pdf```, showing the plot included in the paper. 

# Details of usage

For futher information about the image content see the `README_dockerhub.md`.
