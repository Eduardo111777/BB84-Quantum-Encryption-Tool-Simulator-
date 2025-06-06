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

```text
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
- Qiskit
- `pqcrypto` (optional, for post-quantum signing)
- Other: `tkinter`, `cryptography`, `pyperclip`, etc.

---

## 🛠️ Installation

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

1. Run the GUI:

```bash
python gui/bb84_gui.py
```

2. Follow the interface to:

- Select a file to encrypt.
- Perform BB84 key generation.
- Encrypt the file using AES-256 and store the encrypted Key A with validation via Key B and HMAC.
- Optionally sign the encrypted package with Dilithium2.

---

## 🧑‍💻 Author

- **Héctor Mozo**  
  Department of Computer Science, University of the People

---

## 📄 License

This project is licensed under the MIT License.

---

## 📢 Citation

If you use this project in academic work, please cite it as:

> Mozo, H. (2025). *BB84 Hybrid Quantum-Classical Encryption System (Version 1.0.0)* [Software]. GitHub. [https://github.com/Eduardo111777/BB84-Quantum-Encryption-Tool-Simulator-](https://github.com/Eduardo111777/BB84-Quantum-Encryption-Tool-Simulator-)

---
