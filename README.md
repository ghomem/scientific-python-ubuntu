# scientific-python-ubuntu
Reproducible process for Scientific Python on Ubuntu LTS.

**Goal**: the goal of this repository is helping to setup a reproducible Python environment on Ubuntu LTS releases. Currently it supports Ubuntu 20.04 and Ubuntu 22.04.

**Status:** work in progress.


**Preparing the environment**

In order to prepare the environment we need to execute in the Ubuntu LTS system:
```
APT_PACKAGES="python3-matplotlib python3-pandas python3-numpy python3-scipy python3-jinja2 python3-prettytable
              python3-dateutil python3-markupsafe python3-typing-extensions python3-requests python3-distutils git"

sudo apt-get update
sudo apt-get install -y $APT_PACKAGES
```

In order to test the environment we can clone and test a couple of simple Python repositories such as

Menudo (outputs text tables made with PrettyTable)
```
git clone https://github.com/ghomem/menudo.gi
cd menudo
python3 menudo.py 1
cd ..
```

Viraly (output plots made with Matplotlib)
```
git clone https://github.com/ghomem/viraly.git
cd viraly
python3 viraly.py "4,0.1145,15,3,1,2,0.02,120,120,10276617,4,0.03"
cd ...
```

Covid-pt-utils (fetches remote data with Requests)
```
git clone https://github.com/ghomem/covid-pt-utils.git
cd covid-pt-utils
mkdir output
python3 fetch-dssg-data.py output opendata.ecdc.europa.eu
cd ..
```
If all the tests worked the environment is ready for simple Python programs that use Pandas, Numpy and Scipy, that fetch external data with Requests and output the result in text (with or without PrettyTable) or plots (using Matplotlib).

**Extending the environment**

In order to extend the environment additional apt packages can be installed. Usually they follow the pattern python3-LIBNAME where LIBNAME is the name by which the library is known inside python programs. For example, if your program needs to:

```
import xgboost
```

you will need to execute once:

```
sudo apt-get install -y python3-xgboost
```

After this command is executed your python programs would be able to use the XGBoost library.
