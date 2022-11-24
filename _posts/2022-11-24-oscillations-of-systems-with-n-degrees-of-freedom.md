---
layout: post
title: Laboratory 9 and 10 week - oscillations of systems with n degrees of freedom
categories: [Miscellaneous, Jekyll]
---

# oscillations of systems with n degrees of freedom

Point mass m1=m2=m3 is attached to the flexible beam of negligible weight, which is woven into the frame at one end, at the distance L1,L2,L3.
Based on the measured free oscillations of the system, identify the size of the point masses.

you will see the oscillations of the tax system in your homeland.
neglect the effect of tesis forces. do not tie them to the material of the beam.

Beam Parameters:
```
#Parameters
L1=0.25
L2=0.225
L3=0.19
E = 0.72e11
b=0.025
h=0.003
```

Input frequency parameters:

```
# Input parameters:
f1=2.119
f2=13.88
f3=39.61
```

Matrix of causal factors
```
# matrix of causal factors
J = 1/12 * b *h **3
L = L1+L2+L3
a11 = L**3/(3*E*J)
a12 = 1/(6*E*J)*(L1**3-3*L**2*L1 +2*L**3)
a13 = 1/(6*E*J)*((L1+L2)**3-3*L**2*(L1+L2)+2*L**3)
a22 = (L2+L3)**3/(3*E*J)
a23 = 1/(6*E*J)*(L2**3-3*(L2+L3)**2*L2+2*(L2+L3)**3)
a33 = L3**3/(3*E*J)

P = [[a11, a12, a13],[ a12, a22, a23],[ a13, a23, a33]]
```

Caulculation for differennt mass size
```
import numpy as np
VYSL = []
for x in range(0,200):
    m = x/1000.0
    m1=m
    m2=m+0.012
    m3=m
    M=np.diag([m1,m2,m3])
    u,v  = np.linalg.eig(P*M)
    frequencys = np.diag((v**0.5)/2/np.pi)
    VYSL.append([m, frequencys])
```

