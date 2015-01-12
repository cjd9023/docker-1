This Dockerfile represents a Docker image that encapsulates the [pescanner](https://code.google.com/p/malwarecookbook/source/browse/trunk/3/8/pescanner.py) tool created by Michael Ligh and [modified by Glenn P. Edwards Jr.](https://github.com/hiddenillusion/AnalyzePE/blob/master/pescanner.py) to introduce imphash support. The original version was distributed with the book [Malware Analyst Cookbook](http://www.malwarecookbook.com/). The Dockerfile was contributed to the [REMnux](https://REMnux.org) collection by [Adric Net](http://adric.net/). The Docker image built by this file includes: 

 - Ubuntu base
 - apt in python-magic, yara, python-yara, pip, clamav (all in multiverse) 
 - capabilities.yara, userdb.txt, pescanner.py, pefile
 - pydams via libdasm (needed for imphash calculations)
 
To run this image, use a command like this to scan a specific files, replacing *~/workdir* with the path to your working directory on the underlying host:

```
sudo docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/pescanner pescanner [target file]
```

Alternatively, you can laynch a bash shell in the container and then run pescanner within it:

```
sudo docker run --rm -it -v ~/workdir:/home/nonroot/workdir remnux/pescanner bash
```

Before running the application, create *~/workdir* on your host and make it world-accessible (`chmod a+xwr`).