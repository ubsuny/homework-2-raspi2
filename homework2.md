## Homework 2  Hardware : Raspi-2
## Akash

### Problem 1

In this problem I used *Schroedinger.ipynb* file and made some modification to it. First part was about adding the cubic potential to our SHO problem. so I did that by putting *schroedinger.pert1 = 0.05*. so now the potential becomes $V(x) = \frac{1}{2}m \omega^2 (x^2 + \frac{1}{20} x^3)$.

during the harmonic potential as we know the energy levels were increasing by the same number.

below are the observation i did for the cubic potential

* Energy levels shifted little down.
* potential is no longer harmonic. It's anharmonic
* Difference  between the enegy levels is decreasing as we go higher.
* Eigun functions are not that changing compare to SHO.

below are the observation i did for the quartic potential $V(x) = \frac{1}{2}m \omega^2 (x^2 + \frac{1}{20} x^4)$

* Energy levels shifted little up, I can think of this as I am titlening the boundary, energy levels are raising up. 
* The difference between the energy levels are incresing as well as we go high.  
* Eigun functions are more tightier around the edges. 

There wasn't much difficulty in executing the code as it was all given. but it took time to understand the code. Especially Scipy.Optimize module. It took me some time why we are using *$X_0$ and $x_1$* in the root_scalar, but then I understood it is because of the secant method we are using in it. 