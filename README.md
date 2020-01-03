# pystark

Lineshape models for spectral emission from fusion plasma. Four line models are implemented. Not optimised!

Authorship:

- Joseph Allcock (joseph.allcock@durham.ac.uk for contact)
- James Harrison


### Prerequisites

Python 3 only.

- numpy
- scipy
- matplotlib
- pandas
- f2py (used to wrap fortran90 code in python. This comes with numpy, but if there are any problems, check you are 
able to run 'f2py' from the terminal. When i run locally on macOS, i use the GNU Compiler Collection for the Fortran backend, which can be installed easily using homebrew: 'brew install gcc')

### Installation

In the top-level cloned pystark directory run terminal command:

```
pip install -e . --user
```
Then from python try:
```
import pystark
pystark.demo()
```
to see if it is all working.

### Objects

- **pystark.demo():** Run this to see what is and isn't working. Demonstrates how to use each of the lineshape models, produces an example plot. 
- **pystark.BalmerLineshape():** Main class, see docstring and demo() for usage. 


### Line models

- **Voigt:** Using Griem's empirical scaling for Stark profile FWHM, assuming a Lorentzian lineshape. Quick, but 
inaccurate in the wings.
- **Rosato:** interpolates Rosato tabulated profiles (Stark-Zeeman), convolved with Doppler profile. Narrow parameter range but fine tabulated grid and self-consistent treatment of Stark-Zeeman effects. [paper](https://www.sciencedirect.com/science/article/pii/S0022407316305325).
- **Stehle:** interpolates Stehle tabulated profiles (Stark-Doppler), convolved with Zeeman split lines (simple, 
strong-Zeeman approximation). This is SLOW (~0.5 sec to evaluate) and the tabulated grid is coarse -- included for its wide input parameter range.  [paper](https://lerma.obspm.fr/~stehle/Articles/1999AAS140Stehle.pdf)
- **Stehle param:** [B. Lomanowski's parameterised model](http://iopscience.iop.org/article/10.1088/0029-5515/55/12/123028/meta "Bart's paper") of the tabulated Stehle data. Quick AND accurate, thanks Bart!


