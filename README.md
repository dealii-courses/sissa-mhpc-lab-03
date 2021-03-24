#  Lab 03 - Poisson Problem
## Theory and Practice of Finite Elements

**Luca Heltai** <luca.heltai@sissa.it>

* * * * *

### Instructions

For each of the point below, extend the `step-3` class with functions that 
perform the indicated tasks, trying to minimize the amount of code you copy
and paste, possibly restructuring existing code by adding arguments to existing
functions, and generating wrappers similar to the `run` method (e.g., 
`run_exercise_3`).

Once you created a function that performs the given task, add it to the 
`step-3-tester.cc` file, and make sure all the exercises are run through
the `gtest` executable, e.g., adding a test for each exercise, as in the 
following snippet: 

```C++
TEST_F(Step3Tester, Exercise3) {
   run_exercise_3();
}
```

### Lab-03: step-3 and ParameterHandler

1.  See documentation of step-3 at
    <https://www.dealii.org/current/doxygen/deal.II/step_3.html>

2.  Compile and run step-3.

3.  Open the vtk output and visualize the solution in paraview or visit. 
    Figure out how to warp the solution by the solution variable. Save a picture
    of your visualization on the `figures` subdirectory, named `step-3-0.png`, 
    and commit it to your repository.

4.  Follow the instructions in “Modify the type of boundary condition”
    in the description of the tutorial, plot your output, and save a figure in
    the `figures`  subdirectory, named `step-3-1.png`, and commit it to your
    repository. Make sure the test is run through `gtest`.

5.  Now also do “A slight variation of the last point” but use the value
    -0.5 for the boundary with indicator 1. Save your output as `step-3-2.png`, 
    and commit it to the `figures` directory in your repository. Make sure the
    test is run through `gtest`.

6.  Change the setup to have $f=0$. Save your output as `step-3-3.png`, 
    and commit it to the `figures` directory in your repository. Make sure the
    test is run through `gtest`.

7.  Switch to an L-shaped domain and experiment with a combination of
    Dirichlet and Neumann boundary conditions. By experimentation, identify
    the faces adjacent to the re-entrant corner and apply Dirichlet conditions
    only there. Save your output as `step-3-4.png`, 
    and commit it to the `figures` directory in your repository. Make sure the
    test is run through `gtest`.

8.  Bonus: Do “Convergence of the mean” (read through the end of the 
    documentation of ). Can you see the order $h^2$?
    Increase the polynomial order (you need to increase all orders of
    the quadratures in the program!) and check the convergence of the
    mean now. Make sure the test is run through `gtest`.

### ParameterHandler

1.  Follow the documentation of the class `ParameterAcceptor` (from "A typical 
    usage of this class"). Derive your `Step3` class from `ParameterAcceptor`, 
    and add a function that initializes the class given a parameter
    file name, i.e., `initialize("parameters.prm")`, by calling 
    `ParameterAcceptor::initialize(...)`
    
    
2.  Add the following parameters to your `Step3` class, and make sure they 
    are used throughout your code

      - Finite element degree
      - Number of global refinements
      - Output filename

    Make sure that the degree of the quadrature formula you use is adequate 
    w.r.t. to the degree of the finite element (i.e., at least `fe.degree+1`).

3.  Add two `FunctionParser<2>` members to your `Step3` class, one for the 
    boundary conditions, and one for the forcing term. Add two `std::string` 
    members, representing their mathematical expressions, and a 
    `std::map<std::string, double>` representing the constants to use in your
    mathematical expression, and make sure they are added as parameters of your 
    class as
    
      - Forcing term expression
      - Boundary condition expression
      - Problem constants
    
    and initialize the two `FunctionParser<2>` objects with the given 
    expressions and the given constants. Make sure your `Step3` class uses 
    these two functions where the boundary conditions are computed and where
    the right hand side is assembled

4.  Following the ideas in `step-70`, add two additional parameters to the 
    `Step3` class to select at run time what grid to create, and with what 
    arguments. Use as parameters

      - Grid generator function
      - Grid generator arguments

5.  Test your application with all the files in the `parameters` subdirectory,
    (running the test through the `gtest` application), and create a 
    visualization for each of the given parameters, with the same
    name of the parameter file, i.e., the visualization of the test that runs
    `parameters/hyper-shell.prm` should be saved on an image named `figures/hyper-shell.png`. Commits all your generated figures.