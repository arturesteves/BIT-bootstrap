# BIT bootstrap

## Instructions to setup the environment
Open docker terminal and move to desired working directory
```
$ cd "desired/path/..."
```
Build an image from the dockerfile and run the container with a mounted volume on current folder
```
$ docker build -t bit github.com/arturesteves/bit-bootstrap && docker run --privileged --rm -it -v "$(pwd):/usr/src/my-app" bit bash
```
Just to run the container
```
$ docker run --privileged --rm -it -v "$(pwd):/usr/src/my-app" bit bash
```


### Usage
##### Execute a BIT tool

Move to the directory that contain some implementations of bit tools
```
$ cd /tmp/cnv/BIT/samples
```
Run a bit tool, for example the ICount, and output the result to a directory.
```
$ java ICount /tmp/cnv/BIT/examples /tmp/cnv/BIT/examples/output
```
Attention that each bit tool receives a different arguments, but they tend to follow as specified above:
##### java [Bit tool class] [class or directory to analyze or instrument] [directory to place intrumented classes]
Move to the directory where the instrumented code is
```
$ cd /tmp/cnv/BIT/examples/output
```
Execute instrumented code of class Hello
```
$ java Hello
```


#### Disassemble a java class

Get the signature of a class and its methods and the attibutes.
```
$ javap Hello
```
Get the java byte code of a class and output the result to a file.
```
$ javap -c Hello > helloByteCode.txt
```
  
 
## Setup the environment to develop your own bit tool
#### With Docker
1. Create a directory dedicated to the tool 
2. Build a docker image with BIT on the directory <br/> Follow instructions from section **Instructions to setup the environment**
3. Create the java class(es) 
4. Compile java class 
5. Execute instrumentation code (tool created, with the java command)
6. Execute the output of the instrumentation code (with the java command)

#### Without Docker 
1. Create a directory dedicated to the tool 
2. Copy the BIT directory (which contains the directories highBIT and lowBIT) to the directory created 
3. Create the java class(es) 
4. Compile java class 
5. Execute instrumentation code (tool created, with the java command)
6. Execute the output of the instrumentation code (with the java command)
