## Dependency

```
sudo apt install gfortran libnetcdff-dev libnetcdf-dev ncview netcdf-bin nco
```



## Setting up the repository

Clone the repository and get the large files that are not stored in the repository.

```bash
git clone https://github.com/TobyThomasTech/WW3.git
cd WW3
./model/bin/w3_setup model
./model/bin/ww3_from_ftp.sh
./model/bin/w3_setup ./model -c gnu -s Katrina
./model/bin/w3_automake
```

## Compilation errors

To avoid the error `Error: Type mismatch between actual argument at (1) and actual argument at (2) (REAL(4)/INTEGER(4)).`

```
export FCFLAGS="-w -fallow-argument-mismatch -O2"
export FFLAGS="-w -fallow-argument-mismatch -O2"
```



## Prerequisites

`gfortran` is required for compiling the source code and `texlive` is required for compiling the manual.



## Reference

https://polar.ncep.noaa.gov/waves/workshop/pdfs/wwws_1.1.pdf

`wget ftp://140.90.101.132/history/waves/T03_Tutorial/T03_WWSS2018_Katrina_final.pdf`



## Setting up the environment

Set the path to the bin and exe folders in the path



~/.zshrc

```
# Append WaveWatch III bin and exe folders to the path
path+=(/home/toby/Projects/WW3/model/bin)
path+=(/home/toby/Projects/WW3/model/exe)
export PATH
```



~/.bashrc

```
# Append WaveWatch III bin and exe folders to the path
export PATH="$PATH:/home/toby/Projects/WW3/model/bin:/home/toby/Projects/WW3/model/exe"
```

## Wind data
For the case where the wind data was collected from [Climate Data Store](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview) the following modifications are necessary:
1. Rename variables `u10` and `v10` to `UGRD_10maboveground` and `VGRD_10maboveground`.
2. Reverse the latitudes. 
These changes can ge achived as follows:
```
ncrename -v u10,UGRD_10maboveground -v v10,VGRD_10maboveground file.nc
ncpdq -h -O -a -latitude input.nc output.nc
```
