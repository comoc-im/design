# Comoc ID

A plaintext `.id` file containing an [ECC] key pair

---
## 1. Sign up

1. User click create button, Client generate [ECC] key pair `A`.
2. Put `A` in `.id` file, trigger download.
3. Ask for the `.id` just downloaded, make sure it's downloaded,
   hence transfer the responsibility to user.
4. Ask for PIN password `P`, then:
   1. Generate symmetric crypto key `B`, save it to local session storage;
   2. Encrypt private key of A, getting `C`, save `public key of A` and `C` to 
      local permanent storage;
   3. Send `public key of A`, `Hash of P`, `B` to [Beacon] server.

---
## 2. Sign in

### With `.id` file

### With previous session


[ECC]: https://en.wikipedia.org/wiki/Elliptic-curve_cryptography "Elliptic-curve cryptography"
[Beacon]: https://github.com/comoc-im/beacon "Signaling server of comoc IM"
