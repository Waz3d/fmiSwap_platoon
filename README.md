Credit goes to "Dynamic Runtime Integration of New Models in Digital Twins" [H. Ejersbo, K. Lausdahl, M. Frasheri, L. Esterle] for developing and explaining the fmiSwap artifact. This repository contains modifications made to test the fmiSwap artifact with a different case study.

## Clone this repo

Clone this repo locally

```bash
$ git clone https://github.com/Waz3d/fmiSwap_platoon
```

Change to the repo directory before going to the next step.

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
