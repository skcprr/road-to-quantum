# **Quantum Gates**

Before studying what quantum gates are, let's learn  about classical logic gates.

## Classical logic gates

Classical logic gates are used to manipulate bits. They can take one or more bits as their input and their  output can  also be one or more bits, depending on the type of a gate.  

### Single-bit logic gates

Single-bit logic gates are the simplest type of logic gates. They take one bit as input and return one bit as output. The best known single-bit logic gates are the **identity gate** and the **NOT gate**:

- The **identity gate** does nothing to the input bit $A$. So 0 remains 0, and  1 remains 1. Using a truth table, the identity gate can be written as: 
    
    | $A$ | $A$ |
    |:-:|:-:|
    | 0 | 0|
    | 1 | 1 |
    
    The identity gate  is sometimes called the *buffer gate*. 
- The **NOT gate** flips the input bit $A$: 0 becomes 1 and 1 becomes 0. This is why it's often called the **inverter gate**. Its truth table is:
    | $A$ | $\bar{A}$ |     
    |:-:|:-:|              
    | 0 | 1|                
    | 1 | 0 |

### Two-bit gates

Two-bit logic gates take two bits as input ($A$ and  $B$) and return one bit as output. Out of the 16 possible gates, five are the most important:

- The **AND gate** - the  output bit $A\wedge B$ is 1 only if both input bits are equal to 1:
    | $A$  |$B$| $A\wedge B$|
    |:-:|:-:|:-:|
    | 0  | 0| 0|
    | 0  |1|0|
    |1 |0|0|
    |1 |1|1|

- The **OR gate** outputs 1 if either one or two bits are equal to 1:
    | $A$  |$B$| $A\vee B$|
    |:-:|:-:|:-:|
    | 0  | 0| 0|
    | 0  |1|1|
    |1 |0|1|
    |1 |1|1|
    
- The **XOR (Exclusive OR) gate** the output is 1 if exactly one of the input bits is 1, but not both:
    | $A$  |$B$| $A\oplus B$|
    |:-:|:-:|:-:|
    | 0  | 0| 0|
    | 0  |1|1|
    |1 |0|1|
    |1 |1|0|
  
- The **NAND gate** - the negation of AND:
    | $A$  |$B$| $\overline{A\wedge B}$|
    |:-:|:-:|:-:|
    | 0  | 0| 1|
    | 0  |1|1|
    |1 |0|1|
    |1 |1|0|

- The **NOR gate** - the negation of OR:
    | $A$  |$B$| $\overline{A\vee B}$|
    |:-:|:-:|:-:|
    | 0  | 0| 1|
    | 0  |1|0|
    |1 |0|0|
    |1 |1|0|

### Reversible and irreversible logic gates 

A *reversible* logic gate is a gate, which the input bits always can be determined based on the output bits. For example the **NOT gate** is reversible, because it is possible to determine  the input bits from the output bit. 


An *irreversible* logic gate is the opposite of a reversible gate. Even if the output bits are known,   the input bits cannot be determined. For example, the **NAND gate**: if the output bit is equal 0 it could have come from three possible input combinations.

In general, a logic gate is reversible if:
1. The number of input bits equals the number of output bits.
2. The mapping between input and output is one-to-one (injective).

For instance, consider the following gate:

| $A$  |$B$| $C$ $D$|
|:-:|:-:|:-:|
| 0  | 0| 1 1|
| 0  |1|0 1|
|1 |0| 0 1|
|1 |1|0 0|

Even though the number of inputs equals the number of outputs, this gate is still irreversible, because inputs (0 1 and 1 0) produce the same output
***
## Quantum  gates

A **quantum gate** acts on qubits in the same way that a  classical logic gate acts on bits - it transforms one quantum state into another. 

Let's consider a quantum gate $U$, that acts on a qubit in the state 

$$
|\psi\rangle = \alpha |0\rangle + \beta|1\rangle ,
$$  

and transforms it into 

$$
|\psi'\rangle = \alpha' |0\rangle + \beta'|1\rangle .
$$

This transformation can be written as:

$$
U|\psi\rangle = |\psi'\rangle .
$$

#### Linearity
Quantum gates must be **linear**, which it is a general property of quantum mechanics. If quantum gates were nonlinear it could lead to apparent paradoxes, such as time travel. 

#### Matrix Representation
Any quantum gate acting on a single qubit can be represented as a $2\times 2$ matrix. For example, the gate $U$ above can be expressed as:

$$
U = \begin{pmatrix}
    \alpha' & 0 \\
    0 & \beta'
\end{pmatrix}.
$$

In general, a valid single qubit gate must preserve the **total probability** of the quantum state: 

$$
|\alpha'|^2 + |\beta'|^2 = 1 .
$$ 

The class of matrices that satisfy this constraint are called **unitary matrices**.

A unitary matrix $U$ satisfies:

$$
    U^\dagger U = UU^\dagger = I ,
$$
where $U^\dagger$ is the **conjugate transpose** of $U$.


> Quantum gates acting on a single qubit are $2\times 2$ **unitary** matrices. Every unitary matrix is a valid quantum gate.

#### Reversibility 
Since every unitary matrix is invertible, quantum gates are always **reversible**.

The inverse of a quantum gate $U$ is simply its conjugate transpose:

$$
    U^{-1} = U^\dagger .
$$

> **Key fact:** Quantum gates acting on a single qubit are always $2\times 2$ unitary matrices. Unitary matrix corresponds to a valid quantum gate.

## Common single qubit quantum gates
In contrast to  classical single-bit gates, where there exist only two gates: the **identity gate** and the **NOT gate** - there are infinitely many valid single qubit quantum gates. In fact, every $2\times 2$ unitary matrix is a quantum gate. Some of the most common single qubit quantum gates are:

### Identity gate
The identity gate $I$ leaves the qubit's state unchanged. Its matrix form is:

$$
I = \begin{pmatrix}
    1 & 0 \\ 
    0 & 1
\end{pmatrix},
$$ 

***
### Pauli gates $(X, Y, Z)$
The Pauli gates are the matrices which correspond to a rotation around $x, y$ and $z$ axes of the Bloch sphere by $\pi$ radians.


The Pauli-$X$ gate is the quantum equivalent of the classical **NOT gate**. It flips $|0\rangle$ to $|1\rangle$ and $|1\rangle$ to $|0\rangle$:

$$
X = \begin{pmatrix}
    0 &1 \\ 
    1& 0
\end{pmatrix}.
$$

The Pauli-$Y$ gate turns $|0\rangle$ into $i|1\rangle$, and $|1\rangle$ into $-i|0\rangle$. This corresponds to a rotation about the $y$-axis on the Bloch sphere:

$$
Y = \begin{pmatrix}
    0 &-i \\ 
    i& 0
\end{pmatrix}.
$$

The Pauli-$Z$ gate turns $|1\rangle$ into $-|1\rangle$ and does nothing to $|0\rangle$. This corresponds to a rotation about the $z$-axis on the Bloch sphere:

$$
Z = \begin{pmatrix}
    1 &0 \\ 
    0& -1
\end{pmatrix}.
$$

***
### Hadamard gate
The Hadamard gate is one of the most useful quantum gates. It turns $|0\rangle$ into $\frac{|0\rangle + |1\rangle}{\sqrt{2}}$ and $|1\rangle$ into $\frac{|0\rangle - |1\rangle}{\sqrt{2}}$. So it creates an equal superposition when applied to a computational basis state:

$$
H = \frac{1}{\sqrt{2}}\begin{pmatrix}
    1 &1 \\ 
    1& -1
\end{pmatrix}.
$$

***

### Phase shift gates

Phase shift gates are family of single qubit quantum gates which map the basis states $|0\rangle$ into $|0\rangle$ and $|1\rangle$ into $e^{i\phi}|1\rangle$. The probability of measuring a $|0\rangle$ or $|1\rangle$ does not change after applying this gates, but they modifiy the relative phase of the quantum state. This is equivalent to a rotation about $z$-axis on the Bloch sphere  by $\phi$ radians:

$$
P(\phi) = \begin{pmatrix}
    1 &0 \\ 
    0& e^{i\phi}
\end{pmatrix},
$$

where $\phi$ is the **phase shift**. 

Common phase shift gates are:

$T$ gate, defined with $\psi = \frac{\pi}{4}$:
    
$$
    T = \begin{pmatrix}
    1 &0 \\ 
    0& e^{i\frac{\pi}{4}}
    \end{pmatrix}.
$$

  $S$ gate (also called the phase gate), defined with $$\phi = \frac{\pi}{2}:
    
$$
    S = \begin{pmatrix}
    1 &0 \\
    0& e^{i\frac{\pi}{2}}
    \end{pmatrix}.
$$

The Pauli-$Z$ gate is also a special case of a phase shift gate: $Z = P\left(\pi\right)$.
***

## Summary

- A quantum gate acts on qubit by transforming its state. 
- Any single qubit quantum gate can be represented by $2\times 2$ unitary matrix. 
- Quantum gates are always reversible, because unitary matrices are invertibles.
- Common single qubit quantum gates Include the Pauli matrices $X, Y, Z$ matrices, the Hadamard matrix $H$ and the family of phase shift gates $P(\phi)$.