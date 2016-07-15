# qc-testsuite
The continuous integration testsuite for TOPAS

### Installation
Testing is performed using [nrtest](https://github.com/davidchall/nrtest) and the TOPAS-specific plugins contained in [nrtest-topas](https://github.com/davidchall/nrtest-topas).
These are both Python packages, so you need a Python installation to run the testsuite.
If working on a Mac, I recommend installing Python with [Homebrew](http://brew.sh) to avoid messing up your system Python.

1. Once you have Python, you can install the packages using pip:

        pip install nrtest
        pip install git+https://github.com/davidchall/nrtest-topas.git

2. Now download the tests themselves:

        git clone https://github.com/topasmc/qc-testsuite.git
        cd qc-testsuite
    
### Basic usage
1. Create a metadata file for your local TOPAS installation in the `apps` directory (look [here](https://github.com/topasmc/qc-testsuite/blob/master/apps/topas-1.0-beta8.json) for an example).
The setup script should set environment variables needed to run TOPAS (e.g. Geant4 data paths, `DYLD_LIBRARY_PATH`, etc).

2. Now you can execute the entire testsuite:

        nrtest execute apps/myTopas.json tests/ -o benchmarks/today
        
  or just a few tests:
        
      nrtest execute apps/myTopas.json tests/TimeFeature*.json -o benchmarks/today-timefeature
        
3. You can also compare the results to an old benchmark:

        nrtest compare benchmarks/today benchmarks/yesterday

