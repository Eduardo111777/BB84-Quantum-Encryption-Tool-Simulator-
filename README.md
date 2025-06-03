
# 🔐 BB84 Hybrid Quantum-Classical Encryption System

This project implements a complete quantum-classical encryption framework based on the BB84 protocol for secure key distribution, combined with AES-256 symmetric encryption, HMAC validation, and optional post-quantum authentication using Dilithium2.

---

## ✨ Features

- 🧬 **Quantum Key Generation via BB84** (simulated with Qiskit AerSimulator)
- 🔐 **AES-256 encryption** with salted key derivation
- 🔑 **Key A / Key B split model** for zero-trust decryption
- ✅ **Integrity validation** via HMAC and key verification
- 🔏 **Optional post-quantum signature** using Dilithium2 (if supported)
- 📦 **Modular architecture** with clean separation between crypto engine, quantum logic, and GUI
- 🖥️ **Tkinter GUI** for file selection, key generation, and process visualization

---

## 📚 Architecture

```bash
bb84_backend/
├── core/
│   ├── bb84_quantum.py        # Simulates BB84 protocol
│   ├── aes_engine.py          # AES-256 CBC encryption/decryption
│   ├── encryption.py          # Core logic for high-level encryption/decryption operations
│   ├── key_utils.py           # Key derivation, integrity checks
│   └── __init__.py
├── gui/
│   ├── bb84_gui.py            # Tkinter interface
│   └── __init__.py
├── logic/
│   ├── controller.py          # Central orchestrator for all modules
│   └── __init__.py
├── secure_io/
│   ├── secure_packager.py     # File encryption packaging, signature, and HMAC
│   └── __init__.py
└── requirements.txt
```

---

## ⚙️ Requirements

- Python 3.9+
- [Qiskit](https://qiskit.org/)
- [pqcrypto](https://pypi.org/project/pqcrypto/) *(optional for post-quantum signing)*
- Other: `tkinter`, `cryptography`, `pyperclip`, etc.

Install all requirements:
```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

### 🧪 Generate Quantum Key

```python
from core.bb84_quantum import bb84_protocol

key_a, key_b, match_indices = bb84_protocol(length=256, authenticate=True)
```

### 🔒 Encrypt a File

```python
from secure_io.file_io import save_encrypted_file

with open("secret.txt", "rb") as f:
    data = f.read()

package_bytes = save_encrypted_file(data, key_a, key_b, original_filename="secret.txt")

with open("encrypted_output.bb84", "wb") as out:
    out.write(package_bytes)
```

### 🔓 Decrypt

```python
from secure_io.file_io import load_and_decrypt_bytes

with open("encrypted_output.bb84", "rb") as f:
    package = f.read()

plaintext, metadata, ok = load_and_decrypt_bytes(package, key_b)

if ok:
    with open("decrypted_" + metadata["original_filename"], "wb") as f:
        f.write(plaintext)
```

---

## 🔐 Security Model

- Zero-trust decryption model (requires only Key B to derive and validate Key A)
- AES-256 + salted derivation ensures strong symmetric encryption
- BB84 simulated quantum randomness ensures key unpredictability
- Optional Dilithium2 post-quantum signatures prevent tampering

---

## 🧠 Academic Value

This system simulates and integrates real-world quantum principles into a hybrid encryption protocol. It can serve as:

- A secure file encryption tool
- A proof-of-concept for post-quantum cryptography
- A foundation for further research and academic publication

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙌 Credits

Developed by [Hector Mozo], 05/29/2025-05/31/2025.  
Includes contributions and tools from Qiskit and the pqcrypto library.
