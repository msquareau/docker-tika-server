# docker-tika-server
This repo contains the Dockerfile to create a docker image that contains the latest [Azul Zulu](https://hub.docker.com/r/azul/zulu-openjdk-debian/) Debian running the Apache Tika 1.18 Server on Port 9998 using Java 8.
Modified fork of [docker-tikaserver](https://github.com/LogicalSpark/docker-tikaserver)

Credits to David Meikle (<david@logicalspark.com>)

Out-of-the-box the container also includes dependencies for the GDAL and Tesseract OCR parsers.  To balance showing functionality versus the size of the image, this file currently installs the language packs for the following languages:
* English
* French
* German
* Italian
* Spanish.

To install more languages simply update the apt-get command to include the package containing the language you required, or include your own custom packs using an ADD command.

## Usage

First you need to pull down the build from Dockerhub, which can be done by invoking:

    docker pull msquare/docker-tika-server

Then to run the container, execute the following command:

    docker run -d -p 9998:9998 msquare/docker-tika-server
    
Setting custom JVM_OPTIONS
     
    docker run -d -e JVM_OPTIONS='-server -Xms1g -Xmx1g -XX:+UseG1GC' -p 9998:9998 msquare/docker-tika-server

## Building

To build the image from scratch, simply invoke:

    docker build -t 'docker-tika-server' github.com/msquareau/docker-tika-server
   
You can then use the following command (using the name you allocated in the build command as part of -t option):

    docker run -d -p 9998:9998 docker-tika-server
    
## More

For more info on Apache Tika Server, go to the [Apache Tika Server documentation](http://wiki.apache.org/tika/TikaJAXRS).

## Author

  * Credits David Meikle (<david@logicalspark.com>)
  * Modified for Azul JDK by M-SQUARE Pty Ltd (contact@m-square.com.au)

## Licence

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
