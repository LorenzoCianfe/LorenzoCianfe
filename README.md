<h1 align="center">Lorenzo Cianfe</h1>

<p align="center">
  <b>Systems Architect &amp; Founder &mdash; Sigilas Suite</b><br>
  Engineering a sovereign European ecosystem for digital identity, zero-knowledge custody, and local-first productivity.<br>
  Strict adherence to client-side cryptography, isolated trust domains, and zero-latency performance.
</p>

<p align="center">
  <img alt="Stack: Go · Rust · TypeScript" src="https://img.shields.io/badge/Stack-Go%20%7C%20Rust%20%7C%20TypeScript-007acc?style=flat-square">
  <img alt="Security: Zero-Knowledge" src="https://img.shields.io/badge/Security-Zero--Knowledge-2e7d32?style=flat-square">
  <img alt="Cryptography: Client-Side AEAD" src="https://img.shields.io/badge/Cryptography-Client--Side%20AEAD-5c6bc0?style=flat-square">
  <img alt="Hosting: Sovereign EU" src="https://img.shields.io/badge/Hosting-Hetzner%20Cloud%20EU-e65100?style=flat-square">
  <img alt="Architecture: Local-First" src="https://img.shields.io/badge/Architecture-Local--First%200ms-37474f?style=flat-square">
</p>

<p align="center">
  <a href="#sigilas-suite-ecosystem">Suite Ecosystem</a> &middot;
  <a href="#architectural-invariants">System Invariants</a> &middot;
  <a href="#cryptographic-standards">Cryptographic Standards</a> &middot;
  <a href="#engineering-philosophy">Philosophy</a>
</p>

<br>

## Sigilas Suite Ecosystem

Sigilas is engineered around a <b>Single-Player First</b> paradigm: delivering standalone, high-utility tools to the individual user without reliance on initial network effects, backed by mathematically verifiable zero-knowledge guarantees.

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Identity</h3>
      <b>Authentication Authority &amp; Discovery</b><br><br>
      Central identity and token issuance provider built on OAuth 2.0 with PKCE (S256). Enforces strict domain isolation (Gate F-02 / RFC 8707) with zero cross-product token reuse.
      <br><br>
      <code>Go 1.24 &middot; PostgreSQL &middot; Mailpit &middot; Janitor</code>
      <br><br>
      <i>Repository: <code>sigilas-identity</code> &middot; Private Core</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Send</h3>
      <b>Ephemeral Zero-Knowledge Transfer</b><br><br>
      Sovereign European alternative to Wormhole and WeTransfer for secure file delivery up to 15 GB. Client-side 4 MiB streaming AEAD chunking, URL anchor key (#key), client PoW anti-DoS, and automated physical deletion.
      <br><br>
      <code>Go &middot; Vite/TS &middot; Sharded Storage &middot; S3</code>
      <br><br>
      <i>Repository: <code>sigilas-send</code> &middot; In Hardening (M5)</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Vault &amp; Pass</h3>
      <b>Digital Custody &amp; 3D Physical Wallet</b><br><br>
      Zero-knowledge credential manager and international identity wallet. Argon2id key derivation, RFC 6238 TOTP engine, and interactive CSS 3D viewer with vector barcode generators (IT, FR, DE, ES, US, CN).
      <br><br>
      <code>Go &middot; IndexedDB &middot; CSS 3D &middot; SVG &middot; .pkpass</code>
      <br><br>
      <i>Repository: <code>sigilas-vault</code> &middot; Feature Complete (M2)</i>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Drive &amp; Docs</h3>
      <b>Local-First Sovereign Workspace</b><br><br>
      Zero-latency rich-text editor and spreadsheet engine operating directly on local IndexedDB (0 ms open time). Encrypted hierarchical tree with periodic asynchronous snapshot sync to blind cloud storage.
      <br><br>
      <code>Local-First &middot; TipTap &middot; IndexedDB &middot; Canvas</code>
      <br><br>
      <i>Status: Architectural Design</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Bank</h3>
      <b>Double-Entry Accounting Ledger</b><br><br>
      High-integrity core banking ledger with complete formal separation between identity credentials and the accounting party model (ADR-0037).
      <br><br>
      <code>TypeScript &middot; NestJS &middot; PostgreSQL &middot; 482 Tests</code>
      <br><br>
      <i>Repository: <code>sigilas-bank</code> &middot; Frozen Core</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Chat</h3>
      <b>End-to-End Encrypted Messaging</b><br><br>
      Sovereign real-time communication platform powered by a hardened native Rust cryptographic core implementing modern MLS and Double Ratchet protocols.
      <br><br>
      <code>Rust Core &middot; MLS / Double Ratchet &middot; Baseline</code>
      <br><br>
      <i>Repository: <code>sigilas-chat</code> &middot; Verified Baseline</i>
    </td>
  </tr>
</table>

<br>

## Architectural Invariants

Every service within the Sigilas ecosystem strictly adheres to three non-negotiable architectural invariants:

1. **One Identity, Isolated Trust Domains (Gate F-02):**  
   `sigilas-identity` serves as the sole authentication authority. Downstream services consume opaque global account identifiers (`accountId`) and never share databases. Bearer tokens implement OAuth 2.0 Resource Indicators (RFC 8707) with strict audience binding (`aud`), rendering tokens completely non-reusable across products.
2. **Zero-Knowledge & Client-Side Cryptography:**  
   The cryptographic boundary remains strictly on the client device (Web Crypto API). Backend servers operate exclusively as blind relays or opaque blob storage. Master keys, decryption secrets, and plaintext payloads never transit or reside on server memory.
3. **Local-First & Zero Latency:**  
   Personal productivity and credential tools execute locally against client-side storage (IndexedDB / SQLite), guaranteeing immediate 0 ms UI responsiveness and complete offline autonomy, backed by background synchronization of encrypted snapshots.

<br>

## Cryptographic Standards

| Primitive / Protocol | Standard Specification | Implementation Role |
| :--- | :--- | :--- |
| **Symmetric Cipher** | AES-256-GCM (NIST SP 800-38D) | Chunk streaming wire format (Send) & item-level encryption (Vault) |
| **Key Derivation (KDF)** | Argon2id (RFC 9106) | Master key derivation from credentials (memory: 64 MiB, iterations: 3, parallelism: 4) |
| **Domain Separation** | HKDF-SHA256 (RFC 5869) | Deterministic subkey generation (`AuthHash`, `VaultKey`, `HistoryKey`) |
| **Asymmetric Cryptography** | X25519 (RFC 7748) & Ed25519 (RFC 8032) | Envelope key exchange and digital signature verification |
| **Authentication Flow** | OAuth 2.0 PKCE (RFC 7636) & RFC 8707 | Authorization code profile with S256 challenge and audience binding |
| **Time-Based One-Time Pass** | RFC 6238 | Client-side 30-second token generation without server exposure |

<br>

## Engineering Philosophy

* **Lean Single-Node Density:** Engineered in compiled Go and Rust to operate efficiently on low-cost European cloud instances (Hetzner Cloud EU), keeping memory footprints under 30–50 MB per service while handling high-throughput encrypted I/O.
* **Deterministic Integrity:** Ephemeral transfers verify chunk position and stream termination via Authenticated Additional Data (`AAD = drop_id || chunk_index || is_last`), eliminating truncation and reordering attacks at the cryptographic layer.
* **Sovereignty by Design:** Developed in the European Union, free from telemetry, ad-tech tracking, or proprietary vendor lock-in.

<br>

---

<p align="center">
  <sub>Sigilas Suite &mdash; European Sovereign Infrastructure for Identity, Privacy, and Secure Computing.</sub><br>
  <sub>Official Domains: <a href="https://sigilas.eu">sigilas.eu</a> &middot; <a href="https://sigilas.com">sigilas.com</a></sub>
</p>
