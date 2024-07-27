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
1) Pennylane
2) Numpy
3) Openfermion

For O2 : ![Screenshot from 2024-07-27 21-28-09](https://github.com/user-attachments/assets/b19dc122-4a21-490a-b84c-2a3a80501469)
For H2 : ![Screenshot from 2024-07-27 21-32-31](https://github.com/user-attachments/assets/37f7192b-668e-40bf-9c2b-7c3ead13f166)
For H2O : ![Screenshot from 2024-07-27 21-33-24](https://github.com/user-attachments/assets/5d7672db-ebb5-4bec-b444-f12c3fa5d305)
