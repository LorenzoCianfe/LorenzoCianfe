<h1 align="center">Lorenzo Cianfe</h1>

<p align="center">
  <b>Systems Architect &amp; Founder &mdash; Sigilas Suite</b><br>
  Engineering a sovereign European ecosystem for digital identity, zero-knowledge custody, communications, and productivity.<br>
  Strict adherence to client-side cryptography, isolated trust domains, and local-first zero-latency execution.
</p>

<p align="center">
  <img alt="Stack: Go · Rust · TypeScript" src="https://img.shields.io/badge/Stack-Go%20%7C%20Rust%20%7C%20TypeScript-007acc?style=flat-square">
  <img alt="Security: Zero-Knowledge" src="https://img.shields.io/badge/Security-Zero--Knowledge-2e7d32?style=flat-square">
  <img alt="Cryptography: Client-Side AEAD" src="https://img.shields.io/badge/Cryptography-Client--Side%20AEAD-5c6bc0?style=flat-square">
  <img alt="Hosting: Sovereign EU" src="https://img.shields.io/badge/Hosting-Hetzner%20Cloud%20EU-e65100?style=flat-square">
  <img alt="Architecture: Local-First" src="https://img.shields.io/badge/Architecture-Local--First%200ms-37474f?style=flat-square">
</p>

<p align="center">
  <a href="#suite-ecosystem">Suite Ecosystem</a> &middot;
  <a href="#architectural-invariants">System Invariants</a> &middot;
  <a href="#cryptographic-standards">Cryptographic Standards</a> &middot;
  <a href="#engineering-philosophy">Philosophy</a>
</p>

<br>

## Suite Ecosystem

Sigilas is engineered around a <b>Single-Player First</b> paradigm: delivering standalone, high-utility tools to the individual user without reliance on initial network effects, backed by mathematically verifiable zero-knowledge guarantees.

### 1. Identity, Access &amp; Suite Portal

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Identity</h3>
      <b>Authentication Authority &amp; Discovery</b><br><br>
      Central identity and token issuance provider built on OAuth 2.0 with PKCE (S256). Enforces strict domain isolation (Gate F-02 / RFC 8707) with zero cross-product token reuse.
      <br><br>
      <code>Go 1.24 &middot; PostgreSQL &middot; Mailpit &middot; Janitor</code>
      <br><br>
      <i>Repository: <code>sigilas-identity</code> &middot; Core Service</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas One</h3>
      <b>Unified Suite Portal &amp; Subscriptions</b><br><br>
      Central dashboard for user profile management, cross-app quota allocation, and subscription entitlements. Strict architectural isolation between billing data and cryptographic keys.
      <br><br>
      <code>TypeScript &middot; React &middot; OAuth2 SSO Client</code>
      <br><br>
      <i>Status: Portal Orchestrator</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Alias / Hide</h3>
      <b>Email Masking &amp; Privacy Relay</b><br><br>
      On-demand disposable email aliasing with two-way reverse-alias routing. Full SPF/DKIM preservation via SRS and ARC (RFC 8617) with optional client-side PGP encryption before forwarding.
      <br><br>
      <code>Go SMTP &middot; ARC / SRS &middot; PGP Encryption</code>
      <br><br>
      <i>Status: Privacy Infrastructure</i>
    </td>
  </tr>
</table>

### 2. Security, Custody &amp; Encrypted Storage

<table>
  <tr>
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
    <td width="33%" valign="top">
      <h3>Sigilas Drive</h3>
      <b>Hierarchical Encrypted Storage</b><br><br>
      Cloud file system organized as a cryptographic tree with envelope encryption per directory/file. Go backend acts as a blind storage relay with zero visibility into plaintext content or file metadata.
      <br><br>
      <code>Go &middot; Envelope Encryption &middot; Blind S3</code>
      <br><br>
      <i>Status: Storage Foundation</i>
    </td>
  </tr>
</table>

### 3. Local-First Productivity &amp; Documents

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Notes</h3>
      <b>Encrypted Fast-Capture Notes</b><br><br>
      Local-first private note-taking application with instant full-text search directly inside client memory. Markdown-native, zero-latency capture, and background snapshot synchronization.
      <br><br>
      <code>Local-First &middot; IndexedDB &middot; Fast Search</code>
      <br><br>
      <i>Status: Single-Player Utility</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Docs</h3>
      <b>Rich-Text Document Editor</b><br><br>
      Full-featured document processing engine based on TipTap (ProseMirror). Loads in 0 ms from local storage, operates completely offline, and synchronizes encrypted document state to Sigilas Drive.
      <br><br>
      <code>TipTap &middot; ProseMirror &middot; Offline-First</code>
      <br><br>
      <i>Status: Local-First Core</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Sheets</h3>
      <b>Canvas Spreadsheet Engine</b><br><br>
      Client-side calculation and grid engine based on Canvas and WebAssembly (Univer / HyperFormula). Processes XLSX and CSV locally with zero server compute overhead or cloud leakage.
      <br><br>
      <code>Canvas 60fps &middot; WebAssembly &middot; Client-Side Calc</code>
      <br><br>
      <i>Status: Client-Side Engine</i>
    </td>
  </tr>
</table>

### 4. Sovereign Communications &amp; Time

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Calendar</h3>
      <b>Zero-Knowledge Schedule &amp; Events</b><br><br>
      Private calendar compliant with RFC 5545 (iCalendar). Event titles, locations, and descriptions are encrypted client-side. Push reminders utilize blind timing tokens without exposing event data.
      <br><br>
      <code>RFC 5545 &middot; Blind Push Timers &middot; E2EE Events</code>
      <br><br>
      <i>Status: Privacy Scheduling</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Meet</h3>
      <b>End-to-End Encrypted Video Conferencing</b><br><br>
      Sovereign real-time audio/video calls powered by a Go WebRTC SFU (Pion). True E2EE achieved via browser Insertable Streams and SFrame (RFC 9605), ensuring the relay never decrypts media frames.
      <br><br>
      <code>Go Pion SFU &middot; Insertable Streams &middot; SFrame RFC 9605</code>
      <br><br>
      <i>Status: Communications Core</i>
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

### 5. Ledger, Media &amp; Machine Intelligence

<table>
  <tr>
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
      <h3>Sigilas Social</h3>
      <b>Sovereign Mobile Video &amp; Interactions</b><br><br>
      Mobile video reels, stories, and real-time interaction prototype built for iOS Safari. Maintained as an isolated research sandbox for high-performance mobile multimedia UX.
      <br><br>
      <code>Next.js 15 &middot; React 19 &middot; SQLite &middot; WebSockets</code>
      <br><br>
      <i>Status: Isolated R&amp;D Sandbox</i>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas AI</h3>
      <b>Privacy-Preserving Intelligence</b><br><br>
      Three-tier AI assistant: Tier 1 executes on-device via WebGPU (WebLLM / Transformers.js, zero server cost); Tier 2 utilizes European Confidential Computing TEEs (AMD SEV-SNP); Tier 3 offers stateless BYOK proxies.
      <br><br>
      <code>WebGPU On-Device &middot; Hardware TEE &middot; Private RAG</code>
      <br><br>
      <i>Status: Privacy AI Layer</i>
    </td>
  </tr>
</table>

<br>

## Architectural Invariants

Every service within the Sigilas ecosystem strictly adheres to three non-negotiable architectural invariants:

1. **One Identity, Isolated Trust Domains (Gate F-02):**  
   `sigilas-identity` serves as the sole authentication authority. Downstream services consume opaque global account identifiers (`accountId`) and never share databases. Bearer tokens implement OAuth 2.0 Resource Indicators (RFC 8707) with strict audience binding (`aud`), rendering tokens completely non-reusable across products.
2. **Zero-Knowledge &amp; Client-Side Cryptography:**  
   The cryptographic boundary remains strictly on the client device (Web Crypto API). Backend servers operate exclusively as blind relays or opaque blob storage. Master keys, decryption secrets, and plaintext payloads never transit or reside on server memory.
3. **Local-First &amp; Zero Latency:**  
   Personal productivity and credential tools execute locally against client-side storage (IndexedDB / SQLite), guaranteeing immediate 0 ms UI responsiveness and complete offline autonomy, backed by background synchronization of encrypted snapshots.

<br>

## Cryptographic Standards

| Primitive / Protocol | Standard Specification | Implementation Role |
| :--- | :--- | :--- |
| **Symmetric Cipher** | AES-256-GCM (NIST SP 800-38D) | Chunk streaming wire format (Send) &amp; item-level encryption (Vault, Drive, Calendar) |
| **Key Derivation (KDF)** | Argon2id (RFC 9106) | Master key derivation from credentials (memory: 64 MiB, iterations: 3, parallelism: 4) |
| **Domain Separation** | HKDF-SHA256 (RFC 5869) | Deterministic subkey generation (`AuthHash`, `VaultKey`, `HistoryKey`) |
| **Asymmetric Cryptography** | X25519 (RFC 7748) &amp; Ed25519 (RFC 8032) | Envelope key exchange and digital signature verification |
| **Authentication Flow** | OAuth 2.0 PKCE (RFC 7636) &amp; RFC 8707 | Authorization code profile with S256 challenge and audience binding |
| **Time-Based One-Time Pass** | RFC 6238 | Client-side 30-second token generation without server exposure |
| **Email Alias Authentication** | SRS &amp; ARC (RFC 8617) | Preserving SPF/DKIM/DMARC authentication chains through forwarding relays |
| **Media Stream Encryption** | SFrame (RFC 9605) &amp; Insertable Streams | End-to-end media frame encryption through WebRTC Selective Forwarding Units |

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
