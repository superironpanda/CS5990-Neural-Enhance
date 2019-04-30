# CS5990-Neural-Enhance
This project is based on alexjc's neural-enhance repo from github, link: https://github.com/alexjc/neural-enhance

Assignment: Enhance your own images

## Tutorial:
1. Download the repo from the link above
2. Download Docker for your system and make sure it works
3. Enhance

### For step 2 and 3
Using Docker Image [recommended]
The easiest way to get up-and-running is to install Docker. Then, you should be able to download and run the pre-built image using the docker command line tool. Find out more about the alexjc/neural-enhance image on its Docker Hub page.

Here's the simplest way you can call the script using docker, assuming you're familiar with using -v argument to mount folders you can use this directly to specify files to enhance:

### Download the Docker image and show the help text to make sure it works.
```
docker run --rm -v `pwd`:/ne/input -it alexjc/neural-enhance --help
```
Single Image — In practice, we suggest you setup an alias called enhance to automatically expose the folder containing your specified image, so the script can read it and store results where you can access them. This is how you can do it in your terminal console on OSX or Linux:

### Setup the alias. Put this in your .bashrc or .zshrc file so it's available at startup.
```
alias enhance='function ne() { docker run --rm -v "$(pwd)/`dirname ${@:$#}`":/ne/input -it alexjc/neural-enhance ${@:1:$#-1} "input/`basename ${@:$#}`"; }; ne'
```
### Now run any of the examples above using this alias, without the `.py` extension.
```
enhance --zoom=1 --model=repair images/broken.jpg
```
Multiple Images — To enhance multiple images in a row (faster) from a folder or wildcard specification, make sure to quote the argument to the alias command:

### Process multiple images, make sure to quote the argument!
```
enhance --zoom=2 "images/*.jpg"
```
If you want to run on your NVIDIA GPU, you can instead change the alias to use the image alexjc/neural-enhance:gpu which comes with CUDA and CUDNN pre-installed. Then run it within nvidia-docker and it should use your physical hardware!


## Important model files: https://github.com/alexjc/neural-enhance/releases
