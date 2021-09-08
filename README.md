# Semantic Segmentation

This repository contains a SingularityNET service to do semantic segmentation on images.

Currently it just supports the Mask_RCNN approach, pulling in Matterport's Mask_RCNN implementation.

## Setup

Requires Python 3.6 and NodeJS/npm

```
pip install -r requirements.txt
git clone git@github.com:singnet/snet-cli.git
cd snet-cli
./scripts/blockchain install
pip install -e .
```

## Calling the published service

```
snet channel open-init snet semantic-segmentation  0.001 +10days
snet --print-traceback client call snet semantic-segmentation segment '{"img": {"file@content":"test.jpg", "mimetype": "image/jpeg"}, "visualise":true}'
```

Extracting the contents of the response currently can't easily be done with the CLI.

## Issues

If you get an ImportError ending with `cytoolz/functoolz.cpython-36m-x86_64-linux-gnu.so: undefined symbol: PyFPE_jbuf`,
this [can be solved](https://github.com/pytoolz/cytoolz/issues/120) with:

`pip install --no-cache-dir cytoolz`
