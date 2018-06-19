# Interior Control of the Poisson Equation with the Steepest Descent Method in OpenFOAM

In this work we solve the optimal control problem

<p align="center">
  <img src="https://latex.codecogs.com/gif.latex?%5Cmin%20_%7Bu%20%5Cin%20L%5E2%20%5Cleft%28%20%5COmega%20%5Cright%29%7D%20%5Cmathcal%7BJ%7D%5Cleft%28%20u%5Cright%29%20%3D%20%5Cmin%20_%7Bu%20%5Cin%20L%5E2%20%5Cleft%28%20%5COmega%20%5Cright%29%7D%20%5Cfrac%7B1%7D%7B2%7D%20%5Cint_%7B%5COmega%7D%20%5Cleft%28%20y%20-%20y_d%20%5Cright%29%20%5E2%20%5Cmathrm%7Bd%7D%20%5COmega%20&plus;%20%5Cfrac%7B%5Cbeta%7D%7B2%7D%20%5Cint_%7B%5COmega%7D%20u%20%5E2%20%5Cmathrm%7Bd%7D%20%5COmega%2C">
</p>

where <img src="https://latex.codecogs.com/gif.latex?u"> is the control variable, <img src="https://latex.codecogs.com/gif.latex?y"> the state variable and <img src="https://latex.codecogs.com/gif.latex?y_d"> a target function. The minimization problem is subject to the elliptic partial differential equation

<p align="center">
    <img src="https://latex.codecogs.com/gif.latex?%5Cbegin%7Bcases%7D%20-%5CDelta%20y%20%3D%20f%20&plus;%20u%20%26%20%5Ctext%7Bin%20%7D%20%5COmega%2C%20%5C%5C%20y%20%3D%200%20%26%20%5Ctext%7Bon%20%7D%20%5CGamma.%20%5Cend%7Bcases%7D">
</p>

In order to use the conjugate gradient method, the state variable is separated in two terms as

<p align="center">
    <img src="https://latex.codecogs.com/gif.latex?y%20%3D%20y_u%20&plus;%20y_%7Bf%7D%2C">
</p>

where <img src="https://latex.codecogs.com/gif.latex?y_u"> solves the state equation with zero Dirichlet boundary conditions,

<p align="center">
    <img src="https://latex.codecogs.com/gif.latex?%5Cbegin%7Bcases%7D%20-%5CDelta%20y_u%20%3D%20u%20%26%20%5Ctext%7Bin%20%7D%20%5COmega%2C%20%5C%5C%20y_u%20%3D%200%20%26%20%5Ctext%7Bon%20%7D%20%5CGamma%2C%20%5Cend%7Bcases%7D">
</p>

and <img src="https://latex.codecogs.com/gif.latex?y_f"> is the control-free solution to the state equation,

<p align="center">
    <img src="https://latex.codecogs.com/gif.latex?%5Cbegin%7Bcases%7D%20-%5CDelta%20y_%7Bf%7D%20%3D%20f%20%26%20%5Ctext%7Bin%20%7D%20%5COmega%2C%20%5C%5C%20y_%7Bf%7D%20%3D%200%20%26%20%5Ctext%7Bon%20%7D%20%5CGamma.%20%5Cend%7Bcases%7D">
</p>

## Getting Started

The solver must be compiled in the terminal. It is advisable to first clean previous compilations with

```
wclean
```

and then use

```
wmake
```

### Prerequisites

OpenFOAM C++ library must be installed in order to compile the code.

The OpenFOAM distribution provided by the [OpenFOAM Foundation](https://openfoam.org/) was used.

## Running a Case

In order to run the solver move to the case folder _poissonCGAdjoinFoamCase_ and type in the command line

```
./Allprepare

poissonCGAdjointFoam
```

<p align="center">
  <img src="poissonCGAdjointFoamCase/cg_J.png">
</p>

<p align="center">
  <img src="poissonCGAdjointFoamCase/cg_Jy.png">
</p>

### Warning

It might be needed to use 

```
sed -i -e 's/\r$//' filename
```

and

```
chmod +x filename
```

in order to be able to execute 

```
./filename
```

## Author

* **Jose Lorenzo Gomez**
* **Víctor Hernández-Santamaría**

## Acknowledgments

This project has received funding from the European Research Council (ERC) under the European  Union’s Horizon 2020 research and innovation programme (grant agreement No. 694126-DyCon).
 
[DyCon Webpage](http://cmc.deusto.eus/dycon/)

## References

* F. Tröltzsch. _Optimal control of partial differential equations: theory, methods, and applications_. American Mathematical Soc., 2010.
