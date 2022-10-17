# How to use GPU acceleration

## `CUDA` installation

TODO: Add instructions for CUDA installation

## `pytorch` installation with GPU acceleration

[*Prerequisite: `CUDA` set-up (`cudatoolkit==11.6`)*](#cuda-installation)

```bash
conda install pytorch torchvision torchaudio cudatoolkit=11.6 -c pytorch -c conda-forge
```

Docs: <https://pytorch.org/docs/stable/index.html>

## Using GPU acceleration with `qiskit` and `pennylane`

[*Prerequisite: `CUDA` set-up (`cudatoolkit==11.6`)*](#cuda-installation)

### `qiskit`

You need to remove `qiskit-aer` and reinstall `qiskit-aer-gpu`:

```bash
pip uninstall qiskit-aer
pip install qiskit-aer-gpu
```

or

```bash
pip uninstall qiskit-aer
pip install --upgrade --force-reinstall qiskit-aer-gpu
```

Check:

```python
from qiskit.providers.aer import AerSimulator
print(AerSimulator().available_devices()) # ('CPU', 'GPU')
```

### `pennylane`

```bash
pip install cuquantum
pip install pennylane-lightning-gpu
```

Usage:

```python
import pennylane as qml
device = qml.device('lightning.gpu', wires=3)

@qml.qnode(device=device)
def circuit()
  ...
```
