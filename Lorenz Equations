#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Thu Nov 14 22:17:54 2019

@author: gabriel
"""

from mpl_toolkits import mplot3d
from scipy.integrate import solve_ivp
from scipy.optimize import least_squares
import matplotlib.pyplot as plt
import numpy as np

#Parameters
sigma = 10.0
beta = 2.7
rho = 28
#Initial Conditions
y0 = [-15, #x
      -15, #y
      20] #z

def lorenz(t,y):
    return(sigma*(y[1]-y[0]),
           rho*y[0]-y[1]-(y[0]*y[2]),
           (y[0]*y[1])-beta*y[2]) 
t = np.linspace(0,20,8000)
sol = solve_ivp(lorenz,[0,300,20000],y0,t_eval = t,rtol=1e-13)

#Initial Conditions 2
sigma = 10.0
beta = 2.7
rho = 28
y2 = [-15, #x
      -15, #y
      20.0000001] #z

def lorenz2(t,y):
    return(sigma*(y[1]-y[0]),
           rho*y[0]-y[1]-(y[0]*y[2]),
           (y[0]*y[1])-beta*y[2])   
solution = solve_ivp(lorenz2,[0,300,20000],y2,t_eval = t,rtol=1e-13)

plt.plot(t,sol.y[0])
plt.plot(t,solution.y[0])
plt.xlim(0,30)
plt.xlabel("time")
plt.ylabel("motion(x)")
plt.show()

#(y-y0)^2
pun=np.sqrt((solution.y[0]-sol.y[0])**2 + (solution.y[1]-sol.y[1])**2 + (solution.y[2]-sol.y[2])**2)

sf = np.polyfit(t,np.log(pun),1)
y_2 = sf[0]*t +sf[1] #y = mx+b

plt.semilogy(t,pun)#log plot 
plt.semilogy(t,np.exp(y_2),"k--")
plt.grid()
#plt.xlim(0,20)
plt.ylabel("||y2(t)-y(t)||")
plt.xlabel("time")
plt.show()
print("Slope of dashed line")
print(sf[0])#slope 

"""
#3-D Plotting
fig = plt.figure()
ax = plt.axes(projection="3d")
x_line = (sol.y[0])
y_line = (sol.y[1])
z_line = (sol.y[2])
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.plot3D(x_line, y_line, z_line)
plt.show()
"""
