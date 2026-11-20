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
Developers have complete freedom to write package logic in **any programming language**:
* **C / C++** (Game engines, graphics, low-level system bindings, SIMD)
* **Rust** (High-performance, memory-safe algorithms, WebAssembly)
* **TypeScript / JavaScript** (Web APIs, React / React Native utilities)
* **Go / Zig / Python / WASM**
* **Pure Crest** (`.crt` / `.crest`)

As long as the package exposes a clean **Crest language entrypoint (`index.crt` or `index.crest`)**, any Crest developer will be able to import and use your package directly using native Crest syntax!

---

## 📦 How to Structure & Contribute a Package

To have your package recognized, validated, and evaluated for promotion into the official Crest modules registry, follow these exact requirements:

### 1. Create your package folder
Create a folder named `<your-package-name>/` directly in the root of this repository.

### 2. Add a `crest.json` manifest
Every package must contain a `crest.json` manifest file at its root with the following structure:

```json
{
  "name": "your-package",
  "version": "1.0.0",
  "main": "index.crt",
  "description": "Your package description",
  "author": "CDUS-TECH Company"
}
```

#### Manifest Fields Explained:
* `"name"`: The exact package identifier developers use to import (e.g. `import { ... } from "your-package"`).
* `"version"`: Semantic versioning (`major.minor.patch`).
* `"main"`: The entry point wrapper file (always `"index.crt"` or `"index.crest"`).
* `"description"`: Brief, descriptive summary of what the package accomplishes.
* `"author"`: Set to `"CDUS-TECH Company"`.

---

### 3. Add your Crest source file (`index.crt` or `index.crest`)

Provide a clean Crest syntax wrapper file so Crest developers can import and interact with your package. 

Below are concrete examples showing how to write `index.crt` depending on your package's underlying language:

---

#### 🌟 Pattern A: Pure Crest Package
If your package is written completely in Crest syntax:

```crest
// index.crt - Pure Crest utility module
export shape UserProfile {
  username: string,
  level: number
}

export fn createProfile(username: string, level: number): UserProfile {
  return {
    username: username,
    level: level
  };
}

export fn greet(profile: UserProfile): string {
  const badge = profile.level > 10 ? "Veteran" : "Novice";
  return `Welcome, ${profile.username}! Status: ${badge}`;
}
```

---

#### ⚡ Pattern B: C / C++ / Rust / Native FFI Package
If your package wraps a native compiled binary or C-compatible library (e.g. `.dll`, `.so`, `.dylib`), use Crest's native FFI:

```crest
// index.crt - Native C / Rust FFI wrapper
const nativeLib = loadNativeLibrary("my_math_core", {
  computeFastDistance: { returnType: "number", paramTypes: ["number", "number", "number", "number"] },
  initializeEngine: { returnType: "void", paramTypes: [] }
});

export fn initEngine() {
  return callNativeSymbol(nativeLib, "initializeEngine", []);
}

export fn fastDistance(x1: number, y1: number, x2: number, y2: number): number {
  return callNativeSymbol(nativeLib, "computeFastDistance", [x1, y1, x2, y2]);
}
```

---

#### 🌐 Pattern C: Web / Network / JavaScript / React Native Package
If your package connects to REST APIs or web services (similar to `axios`):

```crest
// index.crt - Network / Web service module
export fn fetchUser(userId: string): any {
  const url = `https://api.example.com/users/${userId}`;
  const response = fetchHttp(url, {
    method: "GET",
    headers: {
      "Accept": "application/json",
      "User-Agent": "Crest-Community/1.0"
    }
  });
  return response;
}

export fn postData(url: string, payload: any): any {
  const bodyText = typeof payload == "string" ? payload : JSON.stringify(payload);
  return fetchHttp(url, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: bodyText
  });
}
```

---

### 4. Provide a Detailed `README.md` Inside Your Package Folder
Include a `README.md` inside `<your-package-name>/` explaining:
1. **Overview & Features**: What your package provides.
2. **Crest Usage Example**: Code snippet showing `import { ... } from "your-package"`.
3. **API Reference**: List of exported functions, parameters, and return types.
4. **Branding**: Conclude with ownership line: `Developed by CDUS-TECH Company. All rights reserved.`

---

## 🔍 Package Evaluation & Official Promotion Pipeline

```
[ Community Pull Request ]
          │
          ▼
[ Automated Crest Syntax & AST Check ]
  - Validates crest.json structure
  - Tokenizes & parses index.crt with zero syntax errors
          │
          ▼
[ Evaluation & Runtime Verification by CDUS-TECH Team ]
  - Tests functions, memory stability, and performance
          │
          ▼
[ Promotion to Official 'crest_modules' Registry ]
  - Merged into official repository
  - Available to all developers via: crest install <your-package>
```

1. **Submission**: Open a Pull Request adding your package folder to this repository.
2. **Review & Verification**: The CDUS-TECH Company engineering team tests your package against the Crest language interpreter, parser, and type checker to ensure compatibility.
3. **Official Promotion**: Once approved, your package is officially promoted into the primary **Crest Modules Registry** (`crest_modules`), making it installable by any Crest user worldwide with:
   ```bash
   crest install <your-package>
   ```

---

## 🔄 Package Updates & Continuous Re-Verification Lifecycle

Even after your package is officially verified and published to the `crest_modules` registry, your development lifecycle continues seamlessly:

### 1. Releasing an Update
Whenever you add new features, fix bugs, or optimize performance:
* Make your code updates in your package folder.
* **Bump the version number** in your `crest.json` manifest according to Semantic Versioning (e.g. from `"1.0.0"` to `"1.0.1"` or `"1.1.0"`).

### 2. Automated & Continuous Re-Verification
* Every time a new version is submitted, the CDUS-TECH verification pipeline automatically **re-verifies the package over and over again**:
  * **Syntax & AST Re-check**: Validates that all new syntax constructs parse cleanly.
  * **Regression Testing**: Confirms that existing functions and APIs did not break.
  * **Memory & FFI Audit**: Checks that native bindings and allocations remain zero-leak and safe.
* Once the new version passes re-verification, it is immediately updated and published in the official registry.

### 3. Developer Peace of Mind
This continuous re-verification guarantees that any package bearing the **CDUS-TECH Company** verification badge is 100% reliable, safe, and backwards-compatible for all Crest developers worldwide with every version release.

---

<div align="center">
  <sub>© 2026 <strong>CDUS-TECH Company</strong>. All rights reserved. | Official Crest Programming Language Ecosystem</sub>
</div>