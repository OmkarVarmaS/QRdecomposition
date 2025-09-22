# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Omkar Varma S
RegisterNumber: 212224240108
'''
import numpy as np

def QR_Decomposition(A):
    A = np.array(A, dtype=float)
    n, m = A.shape
    Q = np.zeros((n, m))
    u = np.zeros((n, m))
    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])
    for i in range(1, m):
        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= np.dot(Q[:, j], A[:, i]) * Q[:, j]
        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i])

    R = np.zeros((m, m))
    for i in range(m):
        for j in range(i, m):
            R[i, j] = np.dot(Q[:, i], A[:, j])

    print("The Q Matrix is")
    print("",Q,end=" ")
    print("\nThe R Matrix is")
    print("",R,end=" ")
a = np.array(eval(input()))
QR_Decomposition(a)

```

## Output

<img width="1403" height="1091" alt="image" src="https://github.com/user-attachments/assets/2e41b258-f374-4a35-a38d-1d1331839ff4" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
