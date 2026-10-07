<h1 align="center">Lorenzo Cianfe</h1>

<p align="center">
  <b>Systems Architect &amp; Founder &mdash; Sigilas Suite</b><br>
  Engineering a sovereign European ecosystem for digital identity, zero-knowledge custody, communications, and productivity.<br>
  Built on client-side cryptography, isolated trust domains, and local-first zero-latency execution.
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

<table>
  <tr>
    <td width="25%" valign="top">
      <h3>Zero-Knowledge</h3>
      Client-side Web Crypto API. Encryption keys and plaintext never leave the browser.
    </td>
    <td width="25%" valign="top">
      <h3>Single-Player First</h3>
      Immediate standalone utility for the individual user, avoiding network effect traps.
    </td>
    <td width="25%" valign="top">
      <h3>Local-First (0 ms)</h3>
      Instant startup from IndexedDB/SQLite with asynchronous encrypted cloud sync.
    </td>
    <td width="25%" valign="top">
      <h3>Sovereign EU Cloud</h3>
      Hosted on low-cost European VPS (Hetzner), free from ad-tech, tracking, or US cloud acts.
    </td>
  </tr>
</table>

<br>

## Suite Ecosystem

### 1. Identity, Access &amp; Suite Portal

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Identity</h3>
      <b>Authentication Authority &amp; Discovery</b>
      <p>Central OAuth 2.0 PKCE identity provider enforcing isolated trust domains (Gate F-02) and strict audience binding.</p>
      <b>Status:</b> Active &middot; <code>Go</code> <code>PostgreSQL</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas One</h3>
      <b>Unified Suite Portal &amp; Subscriptions</b>
      <p>Central dashboard for account discovery, storage quota aggregation, and billing with zero key visibility.</p>
      <b>Status:</b> Design &middot; <code>TypeScript</code> <code>React</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Alias / Hide</h3>
      <b>Email Masking &amp; Privacy Relay</b>
      <p>On-demand disposable email aliasing with two-way reverse routing, preserving SPF/DMARC via SRS and ARC (RFC 8617).</p>
      <b>Status:</b> Design &middot; <code>Go SMTP</code> <code>ARC/SRS</code>
    </td>
  </tr>
</table>

### 2. Security, Custody &amp; Encrypted Storage

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Send</h3>
      <b>Ephemeral Zero-Knowledge Transfer</b>
      <p>European alternative to Wormhole/WeTransfer up to 15 GB. 4 MiB streaming AEAD chunking, URL anchor key, and client PoW anti-DoS.</p>
      <b>Status:</b> Active &middot; <code>Go</code> <code>TypeScript</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Vault &amp; Pass</h3>
      <b>Digital Custody &amp; 3D Physical Wallet</b>
      <p>Argon2id credential manager, RFC 6238 TOTP engine, and interactive CSS 3D wallet for international IDs (IT, FR, DE, ES, US, CN).</p>
      <b>Status:</b> Active &middot; <code>Go</code> <code>IndexedDB</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Drive</h3>
      <b>Hierarchical Encrypted Storage</b>
      <p>Cryptographic folder/file envelope tree where Go relays act as blind storage with zero visibility into filenames or content.</p>
      <b>Status:</b> Design &middot; <code>Go</code> <code>S3-Compatible</code>
    </td>
  </tr>
</table>

### 3. Local-First Productivity &amp; Documents

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Notes</h3>
      <b>Encrypted Fast-Capture Notes</b>
      <p>Personal note-taking with instant full-text search in client memory, Markdown support, and encrypted snapshot sync.</p>
      <b>Status:</b> Design &middot; <code>Local-First</code> <code>IndexedDB</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Docs</h3>
      <b>Rich-Text Document Editor</b>
      <p>Document editor powered by TipTap (ProseMirror). Loads in 0 ms from local storage and operates completely offline.</p>
      <b>Status:</b> Design &middot; <code>TipTap</code> <code>ProseMirror</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Sheets</h3>
      <b>Canvas Spreadsheet Engine</b>
      <p>Client-side formula calculation and grid engine based on Canvas and WebAssembly (Univer/HyperFormula) at zero server CPU cost.</p>
      <b>Status:</b> Design &middot; <code>Canvas 60fps</code> <code>Wasm</code>
    </td>
  </tr>
</table>

### 4. Sovereign Communications &amp; Time

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Calendar</h3>
      <b>Zero-Knowledge Schedule &amp; Events</b>
      <p>RFC 5545 iCalendar with client-side encrypted events and blind timed notification tokens for zero-knowledge push reminders.</p>
      <b>Status:</b> Design &middot; <code>RFC 5545</code> <code>Blind Push</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Meet</h3>
      <b>End-to-End Encrypted Video Calls</b>
      <p>Go WebRTC SFU (Pion) with true E2EE achieved via browser Insertable Streams and SFrame (RFC 9605), keeping media frames unreadable to the relay.</p>
      <b>Status:</b> Design &middot; <code>Pion SFU</code> <code>SFrame RFC 9605</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Chat</h3>
      <b>End-to-End Encrypted Messaging</b>
      <p>Real-time messaging platform powered by a hardened native Rust cryptographic core implementing MLS and Double Ratchet.</p>
      <b>Status:</b> Frozen &middot; <code>Rust Core</code> <code>MLS</code>
    </td>
  </tr>
</table>

### 5. Ledger, Media &amp; Machine Intelligence

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>Sigilas Bank</h3>
      <b>Double-Entry Accounting Ledger</b>
      <p>High-integrity core banking ledger with strict accounting isolation between credentials and the party model (ADR-0037).</p>
      <b>Status:</b> Frozen &middot; <code>NestJS</code> <code>PostgreSQL</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas Social</h3>
      <b>Sovereign Mobile Video &amp; Interactions</b>
      <p>Mobile video reels, stories, and real-time interaction prototype built for iOS Safari. Maintained as an isolated mobile UX sandbox.</p>
      <b>Status:</b> R&amp;D &middot; <code>Next.js 15</code> <code>SQLite</code>
    </td>
    <td width="33%" valign="top">
      <h3>Sigilas AI</h3>
      <b>Privacy-Preserving Intelligence</b>
      <p>Three-tier AI assistant: On-device WebGPU (WebLLM/Transformers.js, zero server cost), European Confidential TEEs, and BYOK proxy.</p>
      <b>Status:</b> Design &middot; <code>WebGPU</code> <code>Confidential TEE</code>
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
