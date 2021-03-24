#  Lab 03 - Poisson Problem
## Theory and Practice of Finite Elements

**Luca Heltai** <luca.heltai@sissa.it>

* * * * *

### Lab-03: step-3/step-4 and ParameterHandler

1.  See documentation of step-3 at
    <https://www.dealii.org/current/doxygen/deal.II/step_3.html>

2.  Compile and run step-3.

3.  Switch to vtk output and visualize in paraview. Figure out how to warp the
    solution by the solution variable. Save a picture of your visualization
    on the `figures` subdirectory, named `step-3-0.png`, and commit it to your
    repository.

4.  Follow the instructions in “Modify the type of boundary condition”
    in the description of the tutorial, plot your output, save a figure in
    the `figures`  subdirectory, named `step-3-1.png`, and commit it to your
    repository.

5.  Now also do “A slight variation of the last point” but use the value
    -0.5 for the boundary with indicator 1. Save your output as `step-3-2.png`, 
    and commit it to the `figures` directory in your repository.

6.  Change the setup to have $f=0$. Save your output as `step-3-3.png`, 
    and commit it to the `figures` directory in your repository.

7.  Switch to an L-shaped domain and experiment with a combination of
    Dirichlet and Neumann boundary conditions. By experimentation, identify
    the faces adjacent to the re-entrant corner and apply Dirichlet conditions
    only there. Save your output as `step-3-4.png`, 
    and commit it to the `figures` directory in your repository.

8.  Bonus: Do “Convergence of the mean”. Can you see the order $h^2$?
    Increase the polynomial order (you need to increase all orders of
    the quadratures in the program!) and check the convergence of the
    mean now.