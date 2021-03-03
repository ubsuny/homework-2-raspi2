## Homework 2  Hardware : Raspi-2
## Akash

### Problem 1

In this problem I used *Schroedinger.ipynb* file and made some modification to it. First part was about adding the cubic potential to our SHO problem. so I did that by putting *schroedinger.pert1 = 0.05*. so now the potential becomes $V(x) = \frac{1}{2}m\omega^2 (x^2 + \frac{1}{20} x^3) $. 

during the harmonic potential as we know the energy levels were increasing by the same number.

below are the observation i did for the cubic potential

* Energy levels shifted little down.
* potential is no longer harmonic. It's anharmonic
* Difference  between the enegy levels is decreasing as we go higher.
* Eigun functions are not that changing compare to SHO.

below are the observation i did for the quartic potential $V(x) = \frac{1}{2}m\omega^2 (x^2 + \frac{1}{20}  x^4) $

* Energy levels shifted little up, I can think of this as I am titlening the boundary, energy levels are raising up. 
* The difference between the energy levels are incresing as well as we go high.  
* Eigun functions are more tightier around the edges. 

There wasn't much difficulty in executing the code as it was all given. but it took time to understand the code. Especially Scipy.Optimize module. It took me some time why we are using $ X_0 $ and $ x_1 $ in the root_scalar, but then I understood it is because of the secant method we are using in it. 


### Problem 2

In this one for the  first part i changed the code slightly to get the desired code for the two charges of the dipole. where one charge is at co=ordiantes (0.25,0.5) and another charge is at (0.75,0.5). Then I used the same structure of the code to get the potential in the grounded rectangular box and plot in 3D.

below is the code I changed in the *poisson.ipynb* 

```

L = 14
N = L+2
q = 10.0                # point charge
i = N // 4     # for the x cordinate of the positive charge of the dipole
j = N//2       # for the Y cordinate of the both charges
k = 3*i         # for the x cordinate of the negative charge of the dipole
h = 1/(L+1)
rho = np.zeros( (N,N))
rho[j,i] = q / h**2    # charge density
rho[j,k] = -q /h**2
nsteps = 100
steps = np.arange(nsteps)
p = Poisson(L,rho, 'Jacobi')
for i in steps : 
    p()

```
in the **Part (b)** to get the exact solution of the dipole potential in the grounded box. I used the following code in vectorized form.

* here I am simply using the potential form $\phi(x) = \frac{q_1}{4*\pi*\epsilon_0} + \frac{q_2}{4*\pi*\epsilon_0}$, where the $q_1$ is positive, while $q_2$ is negative. I wrote the cordinates in cartezian form  to get the right graph.

```

# Exact Solution
q1 = 10.0
q2 = -10.0

Phi_exact = np.zeros( (N,N))
Phi_exact = q1 / ( 4 * np.pi *  ( ( X - 0.25 ) ** 2 + ( Y - 0.5 ) ** 2 ) ** ( 1 / 2 ) ) \
          + q2 / ( 4 * np.pi *  ( ( X - 0.75 ) ** 2 + ( Y - 0.5 ) ** 2 ) ** ( 1 / 2 ) )
fig_e = plt.figure(1)
ax_e = fig_e.gca(projection='3d')
sur_e = ax_e.plot_surface( X, Y, Phi_exact, rstride=1, cstride=1, cmap=cm.gnuplot2,
                        linewidth=0, antialiased=False )
plt.xlabel("x")
plt.ylabel("y")

ax.view_init(elev=10., azim=-45)



```
* we are not getting the same result between the exact and jacobi method. The Exact result has higher peak compare to Jacobi method, I guess the reason behind that is jacobi method solution is still converging. so as WE increse the number of grids in 2D we will get smaller and smaller **h** value. so the peak value will increase. 