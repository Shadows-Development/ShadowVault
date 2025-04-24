> ⚠️ ShadowVault is in early development. Hardware is en route — development will kick off as soon as it lands.


# 🔐 ShadowVault — Hardware-Backed Post-Quantum Key Management for Embedded Systems

**ShadowVault** is a lightweight, secure Key Management System (KMS) designed for embedded devices. Built on the **ESP32**, it combines cutting-edge **post-quantum cryptography** (Kyber512), **secure hardware encryption** (via ATECC608A), and **microSD persistence** to create a truly modern cryptographic vault.

> ShadowVault is the foundation for future secure systems in the Shadow Development ecosystem — including password managers, identity systems, and secure provisioning frameworks.

---

## 🚀 Features

- 🔐 **Post-Quantum Security**: Implements Kyber512 for quantum-resistant key encapsulation
- 🔏 **Encrypted Key Storage**: All keys are AES-128 encrypted using keys stored securely in the ATECC608A chip
- 💾 **Persistent Storage**: Encrypted keys are saved to a microSD card for reuse between boots or sessions
- 📡 **ESP32-Based**: Portable and affordable with WiFi + BLE capabilities for optional host communication
- 🧠 **Modular**: Designed for easy integration into password managers, secure boot chains, and more

---

## 🛠 Hardware Requirements

- ✅ ESP32 development board (WROOM or WROVER preferred)
- ✅ ATECC608A secure element (via I2C)
- ✅ microSD card module (via SPI)
- ✅ 3.3V power source (USB or battery)

---

## 📂 Project Structure

```
shadowvault/
├── firmware/                # ESP32 source code (C++ / ESP-IDF)
│   ├── main.cpp
│   ├── kyber/               # Kyber512 implementation
│   ├── crypto/              # ATECC608A and AES logic
│   ├── storage/             # microSD key I/O
│   └── util/                # Logging, serial helpers
├── docs/                    # Architecture diagrams, threat model
│   ├── threat_model.md
│   └── key_flow.png
├── README.md
└── LICENSE
```

---

## ⚙️ How It Works

1. On boot, the ESP32 checks the SD card for an encrypted Kyber keypair.
2. If missing, it generates a new Kyber keypair and uses the ATECC608A to AES-128 encrypt it.
3. The encrypted keypair is saved to the microSD card.
4. The device can then encapsulate/decrypt shared secrets with a host securely.
5. The shared secret can be used for further encryption, authentication, or provisioning.

---

## 🧪 Use Cases

- 🧠 Secure embedded key storage for IoT devices
- 🛡️ Hardware root-of-trust for password managers and identity systems
- 🔐 Foundation for a secure boot chain or firmware verification
- 🔑 Key exchange between constrained devices and post-quantum-aware services

---

## 🔒 Security Highlights

- AES-128 encryption with non-exportable keys (ATECC608A)
- Proper IV handling for CBC mode (with optional HMAC)
- Hardware RNG + Kyber entropy for strong randomness
- Optional tamper-detection and zeroization features in future revisions
- Designed with future **secure firmware update** and **OTA** in mind

---

## 📦 Future Plans

- [ ] Host SDK (`@shadow-dev/vault-sdk`) for integrating ShadowVault into software clients
- [ ] Password manager integration (`ShadowPass`)
- [ ] Secure OTA update support
- [ ] BLE-based key exchange protocol
- [ ] Industrial-grade PCB design and manufacturing pipeline

---

## 🧑‍💻 Development Notes

This project uses:
- **ESP-IDF**
- **Kyber512 reference implementation (pq-crystals)**
- **Microchip ATECC608A library**
- **FATFS for microSD**

For setup instructions, see [docs/setup.md](docs/setup.md) *(coming soon)*.

---

## 📄 License

Apache License 2.0 — open for use, modification, and distribution with attribution and patent protection.

---

## 👨‍💻 Author

**Harlan Risdal**  
Creator of Shadow Development · Studying Computer Science or Cybersecurity Engineering @ Iowa State University
Website: [https://shadowdevelopment.net](https://shadowdevelopment.net) *Coming Soon*

---

## 🧠 Want to Contribute?

Whether you're a hardware hacker, cryptography geek, or embedded dev — PRs, ideas, and contributions are welcome.  
See [CONTRIBUTING.md](CONTRIBUTING.md) *(coming soon)* or open an issue to get started.

---

## 🔗 Part of the Shadow Ecosystem

- 🧱 [ShadowCore](https://github.com/shadowdevelopment/shadowcore) — Core tools for building secure bots
- 🌐 ShadowPass *(coming soon)* — Hardware-enforced password manager built on ShadowVault
- 🔐 ShadowSecure *(future)* — End-to-end encryption infrastructure for modern systems
