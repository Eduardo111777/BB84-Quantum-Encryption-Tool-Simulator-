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
- 🧩 The system is modular, portable, and scalable, enabling smooth adaptation across platforms, integration with other security modules, and future research extensions.

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
- `pqcrypto` (optional for post-quantum signing)
- Other: `tkinter`, `cryptography`, `pyperclip`, etc.

---

## Install all requirements

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

This project is licensed under the Apache License 2.0 — see the [LICENSE](LICENSE) file for details.

---

## 📚 Citation

If you use this software in academic work or publications, please cite it as:

> Mozo, H. (2025). *BB84 Hybrid Quantum-Classical Encryption Tool.* Journal of Open Source Software. DOI: *[pending upon acceptance]*.

---

## ⚠️ Commercial Use Notice

If used in commercial products or services, proper attribution to Hector Mozo as the original author is required.  
Commercial users are kindly requested to contact the author at [hectormozo308@gmail.com](mailto:hectormozo308@gmail.com) to discuss potential licensing, partnership opportunities, or attribution preferences.

---

## 🙌 Credits

**Primary developer:** **Héctor Mozo**  
**Development period:** January 2025 – May 29, 2025 (local environment)  
The project leverages components from **Qiskit** and the **pqcrypto** library.

---
## Contributing

Contributions to this project are welcome!

If you would like to contribute, please:

- Fork the repository.
- Create a new branch for your feature or bugfix.
- Submit a pull request with a clear description of your changes.

Please ensure that your code follows good coding practices and includes appropriate documentation where necessary.

You can also open issues to report bugs or suggest enhancements.

We encourage contributions that align with the project's goal of advancing research in quantum-classical hybrid cryptography.

---

© 2025 Héctor Mozo — Licensed under the Apache License, Version 2.0

