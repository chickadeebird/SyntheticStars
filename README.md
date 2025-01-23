# SyntheticStars

This is a Pixinsight script for detecting the stars in an image and using the detected stars to create a synthetic starfield using the parameters of the detected stars.

Star detection performance is greatly enhanced by denoising the image prior to detection using the script. There is also an option on the interface to apply an MMT-based denoising operation prior to detection.

The algorithm steps are:

1. Use the Pixinsight StarDetector to find all of the stars in the image.
2. Use DynamicPSF to characterize all of the stars that have been detected. This will find the rotation angles of the stars as well as the width of the major and minor axes.
3. Create a new synthetic star based on the Moffat function that has the same star location but the major and minor axes are now artifically made to both be the smaller of the two, thus creating rounded stars.

This will create a separate image of stars that can be used to replace any stars that have been removed using other tools such as StarNet2. This will likely remove any small galaxies not detected by the Pixinsight star detector.

# Usage

The star detector tab permits adjustment of the Pixinsight Star Detector. Testing of the star detector is made possible with this tab. It may be difficult to capture all of the stars, especially in crowded starfields where stars are clustered together. The tool seems to work best on linear images, but also works on nonlinear images.

Each parameter that can be adjusted has its own tool tip that describes the use of the parameter.

While optimizing the number of stars detected, shutting off the "Replace stars with synthetic stars" and "Keep synthetic stars" options initially and then keying off the number of stars returned by the star detector in the console window may help to optimize the detection parameter tuning.

This script relies on the StarNet2 process to replace the original stars with the detected stars and StarNet2 must be installed to be able replace the stars. Otherwise, the rest of the functionality should stand on its own.

## Uses

The script is used to simulate a starfield based on an existing image. It should work on linear and nonlinear images as well as mono and multi-channel/RGB images.

## Images

This is a sample pair of an original image (left), and an image where the stars are replaced with synthetic stars (right).

<img src="./figs/SyntheticStars replaced.png" text='Synthetic stars script - left original stars, right replaced with synthetic stars' align=left />

<img src="./figs/SyntheticStars kept.png" text='Synthetic stars script - left original stars, right synthetic starfield created' align=left />

## Script

This is the script interface for the SyntheticStars script.

<img src="./figs/SyntheticStars script.png" text='SyntheticStars script' align=left />

This can be found here: ChickadeeScripts > SyntheticStars after installation.

## Manage repository location

In order to automatically install and subsequently refresh script updates in Pixinsight, add the following URL to Resources > Updates > Manage repositories

https://raw.githubusercontent.com/chickadeebird/SyntheticStars/main/

After this has been added to the repositories, Resources > Updates > Check for updates should place the new SyntheticStars script in Scripts > ChickadeeScripts


