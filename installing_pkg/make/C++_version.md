## package: lobSTR
* Ubuntu 20.04.3 LTS
* Release: 20.04
* Codename: focal

### given codes for installation from source
~~~bashscript
wget http://files.teamerlich.org/lobSTR/lobSTR-X.X.X.tar.gz
tar -xzf lobSTR-X.X.X.tar.gz
cd lobSTR-X.X.X/
./configure  
make           # <- error occurs
make check
sudo make install
~~~

### error message
~~~
common.cpp:195:10: error: cannot convert 'std::ifstream' {aka 'std::basic_ifstream<char>'} to 'bool' in return
195 |   return ifile;
    |          ^~~~~
~~~

* since GCC 6 defaulting to C++14 mode instead of C++03 mode, cannot covert 'std::ostream' to 'bool'

*  fix the common.cpp line 195
*  original code
~~~c
bool fexists(const char *filename) {
  ifstream ifile(filename);
  return ifile;
}
~~~
* corrected code
~~~c
bool fexists(const char *filename) {
  return (bool)ifstream(filename);
}
~~~


