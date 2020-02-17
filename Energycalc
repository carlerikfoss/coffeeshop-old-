import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

E = 3.6  # Potential in V (J/C or W/A) (average operating potential) for Si/ X full cell
Ec = 4  # potential in V for carbon / x full cell
# I=(C*L*0.001) # Areal capacity mAh/cm2
x=np.linspace(0,1,11) # values between 0 to 1 , 11 values - Loading in mg/cm2
A = 1.54  # area of electrode in cm2
L = [0.5, 1, 2]  # Loading in mg/cm2
C = 1000  # capacity in mAh/g or Ah/kg
Cc = 372  #
W = 0.000010  # total weight of all cell components in kg- Seperator/electrolyte/casings etc should provide input for this as well
n = 22  # electrons transferred
z = 5  # amount of Si in the alloy
Mw = 28  # Molecular weight of Si g/mol
F = 96485  # Faradays constant C/mol
QtheoSi = (1000 * n * F) / (3600 * Mw * z)  # convert from A to mA and s to h so the units will be [mAh/g]
QtheoCarbon = (1000 * F) / (3600 * 12 * 6)  # convert from A to mA and s to h so the units will be [mAh/g]

QSnO2ir = (1000 * F * 4) / (3600 * 150.7)  # convert from A to mA and s to h so the units will be [mAh/g]
QSnOir = (1000 * F * 2) / (3600 * 134.7)  # convert from A to mA and s to h so the units will be [mAh/g]
QSnO2rev = (1000 * F * 4.4) / (3600 * 150.7)  # convert from A to mA and s to h so the units will be [mAh/g]
QSnOrev = (1000 * F * 4.4) / (3600 * 134.7)  # convert from A to mA and s to h so the units will be [mAh/g]

a = 1  # fraction Si in SiaNx

Mwsi = 28.08
MwN = 14

# Irreversible loss (not including SEI) SiNx+nLi+ne-->Matrix+ Si ,   where matrix is suggested to be Li2SiN2, Li3N, Si3N4
# SiNx+3*xLi+3*xe--->x*(Li3N)+Si

QLi3N = (1000 * F * (3 * x)) / (
            3600 * (Mwsi * a + MwN * x))  # convert from A to mA and s to h so the units will be [mAh/g]


def f(x):
    res = (1000 * F * (3 * x)) / (3600 * (Mwsi * a + MwN * x))  # for Li3N

    return res


def f1(x):
    res = (1000 * F * x) / (3600 * ((Mwsi * a + MwN * x)))  # for Li2SiN2

    return res


def f2(x):  # reversible Li3N
    res = (1000 * F * 3.5) / (3600 * ((Mwsi * a + MwN * x)))
    return res


def f3(x):  # reversible Li2SiN2
    res = (1000 * F * 3.5) / (3600 * 2 * (Mwsi * a + MwN * x))
    # res=(1000*F*3.5)/(3600*(Mwsi*a))-(1000*F*2*x)/(3600*(2*(Mwsi*a+MwN*x)))    #for Li2SiN2
    return res


x = np.linspace(0, 2, 14)  # values between 0 to 1 , 11 values - x in SiNx
y = np.empty_like(x)  # define empty cell
y2 = np.empty_like(x)
y3 = np.empty_like(x)
y4 = np.empty_like(x)
# print(x)
i = 0
for xi in x:  # x=L
    y[i] = f(xi)  # fill up empty cell calling on function f with imput L*i
    y2[i] = f1(xi)
    y3[i] = f2(xi)
    y4[i] = f3(xi)
    i = i + 1

# matplotlib


import matplotlib.pyplot as plt

plt.figure(1)
plt.plot(x, y, 'bx', label='Irreversible cap Li3N')
plt.title('Capacity as function of x in SiNx for Li3N matrix')
plt.xlabel('Fraction x in SiNx')
plt.ylabel('Capacity [mAh/g]')

plt.figure(2)
plt.plot(x, y2, 'rx', label='irreversible Li2SiN2')
plt.title('Capacity as function of x in SiNx for Li2SiN2  matrix')
plt.xlabel('Fraction x in SiNx')
plt.ylabel('Capacity [mAh/g]')
plt.legend(loc='best')

plt.figure(1)
plt.plot(x, y3, 'bo', label='Reversible cap Li3N')
plt.title('Capacity as function of x in SiNx for Li3N matrix')
plt.xlabel('Fraction x in SiNx')
plt.ylabel('Capacity [mAh/g]')
plt.legend(loc='best')

plt.figure(2)
plt.plot(x, y4, 'bo', label='reversible Li2SiN2')
plt.title('Capacity as function of x in SiNx for Li2SiN2  matrix')
plt.xlabel('Fraction x in SiNx')
plt.ylabel('Capacity [mAh/g]')
plt.legend(loc='best')
plt.show()
# for ......Si3N4?
#QSi3N4 = (1000 * F * n) / (3600 * (Mwsi * a + MwN * b))

# for reversible   Si
QSiaNbrev = (1000 * F * 3.75) / (3600 * 28.08)  # convert from A to mA and s to h so the units will be [mAh/g]

#print(QSiaNbir)
#print(QSiaNbrev)
