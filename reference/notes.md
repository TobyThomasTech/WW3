## Setting up the repository

Clone the repository and get the large files that are not stored in the repository.

```bash
git clone https://github.com/TobyThomasTech/WW3.git
cd WW3
./model/bin/w3_setup model
./model/bin/ww3_from_ftp.sh
./model/bin/w3_setup ./model -c gnu -s NCEP_st2
./model/bin/w3_automake
```



## Prerequisites

`gfortran` is required for compiling the source code and `texlive` is required for compiling the manual.



## Reference

https://polar.ncep.noaa.gov/waves/workshop/pdfs/wwws_1.1.pdf

