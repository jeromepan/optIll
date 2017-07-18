# Designing illuminant spectral power distribution for surface classification

There are many application areas where users have full control over the illumination, and have the ability to shape its spectral power distribution. In those cases spectrally optimal light can accentuate features in images and hence improve image classification tasks.

<p align="center"> 
<img width="500px" src="https://github.com/hblasins/optIll/blob/master/Figures/Overview.png">
</p>

In this project we propose two approaches that estimate the optimal spectral power distribution of the illuminant. The unsupervised approach uses nonnegative sparse Principal Component Analysis to derive optimal, and physically realizable illuminant spectra. The supervised approach incorporates linear image formation model directly into classification algorithm and uses alternating minimization to simultaneously search for classifier decision boundaries and optimal lights.

If you use these tools please cite
```
@inproceedings{blasinski2017optIll,
    title={Designing illuminant spectral power distribution for surface classification},
    author={Blasinski, Henryk and Farrell, Joyce and Wandell, Brian},
    booktitle={IEEE Computer Vision and Pattern Recognition, CVPR},
    year={2017},
    organization={IEEE}
}
```

## Dependencies

To succesffuly run the scripts in this project the following dependencies need to be 
installed.

* MATLAB - we tested the code with MATLAB 2015 and 2016. The illuminant selection algorithms do not require additional toolboxes, but some evaluation scripts do, specifically: Image Processing and Statistics and Machine Learning.
* [ISET](http://imageval.com) - Image Systems Engineering Toolbox for camera sensor simulations. A light version of ISET is provided with this code repository.
* [CVX](http://cvxr.com/) - a Matlab toolbox for convex optimization. As an alternative MATLAB Optimization Toolbox can also be used. **As of 06/2017 CVX is only supported on MATLAB 2016b and older.**

## Data

Sample data used in our experimens can be downloaded from the [Stanford Digital Repository](https://purl.stanford.edu/rq453qp3526). The `Images.zip` file contains all images captured using the experimental setup. The `Results.zip` contains pixel classification results, this data should be reproducible by running the appropriate `classify***.m` scripts. Note that given the extensive cross-validation these results will take long to generate, which is why we are also releasing them.

## Getting started

Once you start MATLAB please run the `install.m` script from the `./Code` directory. This script adds all the relevant project sub-directories to MATLAB path.

To see the algorithms in action you can have a look at `s_simulationExample.m` or `s_simulationNumChannels.` scripts. These use the ISET toolbox to simulate camera captures and compare conventional RGB cameras and broadband illuminants to using monochrome cameras and optimal lights. 

The supervised and unsupervised illuminant selection algorithms are in `./Code/Algorithms` folder which also contains test scripts `t_***.m` that illustrate how these functions should be used and where possible (`sparsePCA.m`) compare the iterative ADMM implementation with that of `cvx`.


