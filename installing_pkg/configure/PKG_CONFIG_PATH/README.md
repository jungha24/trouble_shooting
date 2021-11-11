## package: lobSTR
* Ubuntu 20.04.3 LTS
* Release: 20.04
* Codename: focal

### given codes for installation from source
~~~bashscript
wget http://files.teamerlich.org/lobSTR/lobSTR-X.X.X.tar.gz
tar -xzf lobSTR-X.X.X.tar.gz
cd lobSTR-X.X.X/
./configure   # <- error occurs
make
make check
sudo make install
~~~

### error message
~~~
configure: error: Package requirements (gsl) were not met:
No package 'gsl' found
~~~

* installing gsl can be done like... *download .tar.gz -> ./configure -> make -> make install*
* but gsl was already installed in **/usr/local/include** 
  * there were header files in gsl folder (.h)
  * pkg config files were in **/usr/local/lib/pkgconf** (.pc)
  * downloading pkg from source seems to install it to /usr/local

*  set PKG_CONFIG_PATH envrionment variavle
~~~bashscript
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
export PKG_CONFIG_PATH
~~~

### error message
~~~
configure: error: Package requirements (cppunit) were not met:
No package 'cppunit' found
~~~

* there was no cppunit 
* intall cppunit
~~~bashscript
sudo apt install libcppunit-dev
~~~
* cppunit folder was in **/usr/include**
  * there were header files and folders of config, extensions, plugin, ...
  * pkg config file was in /usr/lib/x86_64-linux-gnu/pkgconfig/cppunit.pc 
  * the path to pc file can be indentified through 
  ~~~bashscript
  # sudo apt-get install apt-file
  # apt-file update   # <- error occurs. can be solved by removing ppa
  apt-file search cppunit.pc
  ~~~

*  set PKG_CONFIG_PATH envrionment variavle
~~~bashscript
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib/x86_64-linux-gnu/pkgconfig/cppunit.pc
export PKG_CONFIG_PATH
~~~ 
  
