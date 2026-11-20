<div align="center">
  <img src="assets/crest-logo.png" alt="Crest Programming Language Logo" width="220" />
  <h1>Crest Community Package Registry</h1>
  <p><strong>The Open Staging & Contribution Hub for the Crest Programming Language</strong></p>
  <p><em>Developed and maintained by <strong>CDUS-TECH Company</strong>. All rights reserved.</em></p>
</div>

---

## 🌐 Welcome Community Developers!

The **Crest Community Registry** is an open repository where community developers, open-source contributors, and teams can create, test, and showcase new packages and integrations for the **Crest Programming Language**.

### 💡 Multi-Language Freedom
Community developers have full freedom to build packages in **any language of their choice**:
* **C / C++** (Native libraries, game engines, SIMD mathematics)
* **Rust** (High-performance, memory-safe engines, WebAssembly tools)
* **TypeScript / JavaScript** (Web, React, React Native components & utilities)
* **Python / Go / Zig / Assembly / WASM**

As long as the package exposes a clean **Crest language entrypoint (`index.crt` or `index.crest`)**, Crest developers can import and use your package directly using idiomatic Crest syntax!

---

## 📦 How to Contribute a New Package

To have your package recognized and reviewed by CDUS-TECH Company for promotion into the official Crest modules registry, follow these exact requirements:

### 1. Create your package folder
Create a folder named `<your-package-name>/` directly in the root of this repository.

### 2. Add a `crest.json` manifest
Every package must contain a `crest.json` manifest at its root:

```json
{
  "name": "your-package",
  "version": "1.0.0",
  "main": "index.crt",
  "description": "Your package description",
  "author": "CDUS-TECH Company"
}
```

### 3. Add your Crest source file (`index.crt` or `index.crest`)
Provide a clean Crest syntax wrapper file so Crest developers can import and interact with your package:

```crest
// index.crt - Your Package Entry Point for Crest
export fn helloCommunity() {
  Say "Hello from the Crest Community Package!";
  return true;
}
```

---

## 🔍 Package Evaluation & Official Promotion Pipeline

1. **Submission**: Submit a Pull Request with your package folder containing `crest.json`, `index.crt`, and your package implementation code or native binaries.
2. **Review & Verification**: The CDUS-TECH Company engineering team will test your package against the Crest language interpreter, parser, and type checker to verify that:
   - The `crest.json` manifest adheres to Crest specifications.
   - The `index.crt` wrapper executes cleanly without syntax or runtime errors.
   - Memory management, FFI bindings, and performance criteria are met.
3. **Official Promotion**: Once evaluated, verified, and approved, your package will be officially promoted and merged into the primary **Crest Modules Registry** (`crest_modules`), making it directly installable by every Crest developer worldwide via:
   ```bash
   crest install your-package
   ```

---

<div align="center">
  <sub>© 2026 <strong>CDUS-TECH Company</strong>. All rights reserved. | Official Crest Programming Language Ecosystem</sub>
</div>