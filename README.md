# Quantum Computing Tutorials

Tutorials on Quantum Computing with [Qiskit](https://qiskit.org/documentation/tutorials.html)

Tutorials on Quantum Machine Learning with [PennyLane](https://pennylane.ai/qml/)

## Installation

Create a minimal environment with only Python installed in it.

````
conda create -y -n qc-tutorials python=3.8
````
Activate your new environment.
````
conda activate qc-tutorials
````
Next, install the dependencies.
````
pip install -r requirements.txt
````
<!-- 
````
pip install qiskit-ibmq-provider
````
If you want to install GPU supported simulators, you have to install this other package:
````
pip install qiskit-aer-gpu
```` -->

----
## Use

### Local
Activate your environment
````
conda activate qc-tutorials
````
launch Jupyter by running
````
jupyter notebook 
````
or if jupyter is not recognized use
````
python -m jupyter notebook 
````

### Remote
In the host machine, activate your environment.
````
conda activate qc-tutorials
````
launch Jupyter by running (e.g. port=8888)
````
jupyter notebook --no-browser --port=XXXX
````
or if jupyter is not recognized use
````
python -m jupyter notebook -no-browser --port=XXXX
````
If the notebook is not visualizing, redirect the port on your local machine by opening a terminal and run this command,
````
ssh -N -f -L YYYY:localhost:XXXX account@host
````

### Quantum Embedding (Encoding) Techniques

A quantum embedding represents classical data as quantum states in a Hilbert space via a quantum feature map.

To embed this data into 𝑛 quantum subsystems (qubits or qumodes), we use various embedding techniques:

* **BASIS** *Embedding*
* **AMPLITUDE** *Embedding* 
* **ANGLE** *Embedding*

They are explained in *embedding_techniques.ipynb*

### Image Processing

In the *image_processing.ipynb* notebook, we evaluate 2 quantum image processing techniques:

* **FRQI**: Circuit depth:  5238273, Circuit size:  7342090
* **NEQR**: Circuit depth:  6071, Circuit size:  22324

The results give us an overview in terms of complexity of the circuits. 
We encode a reduced version (32x32) of the `lena.jpg` image for both the image techniques 
and we compare the depth and size of the corresponding quantum circuits.

----

## Test with Real Quantum Hardware

#### Configure your IBM Quantum Experience credentials

1. Create an IBM Quantum Experience account or log in to your existing account 
by visiting the [IBM Quantum Experience login page](https://quantum-computing.ibm.com/login).

2. Copy (and/or optionally regenerate) your API token from your 
[IBM Quantum Experience account page](https://quantum-computing.ibm.com/account).

3. Take your token from step 2, here called MY_API_TOKEN, and run:
````
from qiskit import IBMQ
IBMQ.save_account('MY_API_TOKEN')
````
The command above stores your credentials locally in a configuration file called `qiskitrc`.
By default, this file is located in `$HOME/.qiskit`, where `$HOME` is your home directory. 


#### Find available IBM quantum computers

In python
````
provider = IBMQ.load_account()
available_cloud_backends = provider.backends()
print('\nHere is the list of cloud backends that are available to you:')
for i in available_cloud_backends: print(i)
````
Output:
````
Here is the list of cloud backends that are available to you:
ibmq_qasm_simulator
ibmqx2
ibmq_armonk
ibmq_santiago
ibmq_bogota
ibmq_lima
ibmq_belem
ibmq_quito
simulator_statevector
simulator_mps
simulator_extended_stabilizer
simulator_stabilizer
ibmq_manila
````


