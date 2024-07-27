Domain: Quantum Computing

Problem Statement:
Qkrishi : VQE for formation of Water
The Qkrishi project aims to apply quantum computing techniques, specifically
the Variational Quantum Eigensolver (VQE) algorithm, to simulate and
understand the formation of water (H₂O) from hydrogen and oxygen . This
project will explore the potential of quantum computing in solving complex
quantum chemistry problems, focusing on accurately determining the ground
state energy of the water molecule, which is essential for understanding its
formation process.

Our solution, as outlined in the proposal, follows the main steps of:
1) Generating Hamiltonian
2) Design an ansatz
3) Optimise the energy

To design the ansatz, we use the PennyLane library function qml.UCCSD
This runs through all the possible excitations assigning them weights (here, theta) and runs the unitary operator to control the excitations of them all.
Next we use the PennyLane in-built gradient-descent optimiser to optimise the energy.

Note: The descent optimiser is used due to the existence of the Variational Quantum Principle. This states that the ground-state energy of a state can never be less than the expectation value of the Hamiltonian.
However, the Hamilotnian must be of a suitable initial state, hence, the ansatz must be taken precisely.

PYTHON language has been used for the simulation of quantum circuit and optimization of parameters.
The libraries used are :
1) Pennylane (Python library for quantum computing, quantum machine learning, and quantum chemistry)
2) Numpy (Library adding support for large, multi-dimensional arrays and matrices, along with a large collection of functions to operate on these arrays)
3) Openfermion (Open source library for compiling and analyzing quantum algorithms which simulate fermionic systems)

CODE OVERVIEW :
1.First we have imported neccessary libraries like pennylane, numpy, openfermion.
2.Defined molecular structure of molecules : symbols and coordinates(3D).
3.Added some additional properties : charge, spin multiplicity, basis set.
4.Created a 'Molecule' object using the previously defined parameters. This object will store all necessary information about that respective molecule.
5.Defined the number of active electrons and orbitals for the simulation.
   -active electrons specifies the number of electrons considered in the active space. 
   -active orbitals specifies the number of orbitals considered.
6.Compute the Hamiltonian of the molecule and determine the number of qubits required for the simulation.
   -Hamiltonian operator representing the energy of the system.
   -Qubits mentioned in code are the number of qubits needed to represent the molecular system on a quantum computer.
7.Generated the Hartree-Fock state, which is the initial approximation of the ground state wavefunction.
8.After that we have generated single and double excitations from the Hartree-Fock state.
9.Define the quantum device (simulator) to be used for the simulation.
   -Default qubit simulator is used when number of qubits required for simulation are less.
   -Lightning qubit simulator is used when number of qubits required for simulation are more.
10.Defined the quantum node (qnode) for the UCCSD circuit.
   -The 'circuit' function applies the UCCSD ansatz to the Hartree-Fock state. 
   -The function returns the expectation value of the Hamiltonian (H).
11.Initialized the circuit parameters used in UCCSD ansatz to zero.The number of parameters is equal to the total number of single and double excitations.
12.Defined the optimizer to be used for parameter optimization. Here, the gradient descent optimizer with a stepsize of 0.5 is chosen.
13.Optimize the circuit parameters over 21 iterations:
   -In each iteration, the optimizer updates the parameters and computes the energy.
   -Every second step, the current step number and energy are printed.

Here are the energy outputs recieved after simulations : 
For O2 : ![Screenshot from 2024-07-27 21-28-09](https://github.com/user-attachments/assets/b19dc122-4a21-490a-b84c-2a3a80501469)
For H2 : ![Screenshot from 2024-07-27 21-32-31](https://github.com/user-attachments/assets/37f7192b-668e-40bf-9c2b-7c3ead13f166)
For H2O : ![Screenshot from 2024-07-27 21-33-24](https://github.com/user-attachments/assets/5d7672db-ebb5-4bec-b444-f12c3fa5d305)
