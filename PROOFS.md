# Proofs you can verify independently

Each is a **challenge**, not a claim. None require access to any FRAYMUS system.

## 1. Identity — Ed25519 (RFC 8032)

See [`identity.json`](identity.json). It contains a public key, a plain-English statement, and an Ed25519
signature over that statement. Verify with any standard library:

```python
from nacl.signing import VerifyKey          # pip install pynacl
import json
p = json.load(open("identity.json"))
VerifyKey(bytes.fromhex(p["ed25519_public_key_hex"])).verify(
    p["statement"].encode(), bytes.fromhex(p["signature_hex"]))
# raises if invalid; returns the message if valid
```

Also confirm the identity derivation:
```python
import hashlib
sha = hashlib.sha256(bytes.fromhex(p["ed25519_public_key_hex"])).hexdigest()[:16]
assert "fx-" + "-".join(sha[i:i+4] for i in range(0,16,4)) == p["fx"]
```
Change one character of `statement` → verification fails. The signature proves the holder of the private key
authored exactly that statement, and nothing else can be forged in their name.

## 2. The φ-seal — pure math

FRAYMUS seals artifacts with **φ^75**, where φ = (1+√5)/2.

- Exact: φ^75 converges to the **75th Lucas number** (OEIS A000032) = **4,721,424,167,835,364**.
- As stored in a 64-bit float: **4,721,424,167,835,376** — a 12-count drift at the 16th significant digit, the
  documented precision limit of IEEE-754 doubles at this magnitude.

```python
phi = (1+5**0.5)/2
print(phi**75)                 # 4.721424167835376e+15  (float)
# Lucas L_75 (exact):
a,b=2,1
for _ in range(75): a,b=b,a+b
print(a)                       # 4721424167835364
```

## 3. The QHRC patent — public record

US patent application **#19/071,497** (Quantum Harmonic Resonance). Look it up on Google Patents or the
USPTO Patent Center. An external, government-held anchor that exists independent of any FRAYMUS server.
