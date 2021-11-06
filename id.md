# Comoc ID

A plaintext `.id` file containing an [ECC] key pair

---
## Sign up

1. User click create button, Client generate [ECC] key pair `A`
2. Client put `A` in `.id` file, trigger download
3. Client ask for the `.id` just downloaded, make sure it's downloaded, hence
   transfer the responsibility to user
4. Client ask for PIN password `P`, then:
   1. Generate symmetric crypto key `B`, save it to local session storage
   2. Encrypt `private key of A` with `B`, getting `C`, save `public key of A`
      and `C` to local permanent storage;
   3. Send `public key of A`, `Hash of P`, `B` to [Beacon server]
5. [Beacon server] save `public key of A`, `Hash of P`, `B` as a new user.

---
## Sign in

### With `.id` file

1. User provided `.id` file `F`, click sign in button
2. Client get key pair `A` from `F`, then:
   1. Let `R` be the sign in request
   2. sign `R` with `private key of A`, getting `S`
   3. send `public key of A`, `R`, `S` to [Beacon server]
3. [Beacon server] verify the signature, find a record with the `public key of A`,
   then return the symmetric crypto key `B` to client
4. Client save symmetric crypto key `B` to local session storage
5. Client encrypt `private key of A` with `B`, getting `C`, save `public key of A`,
   and `C` to local permanent storage

### With previous session

1. User select a previous session to sign in, enter PIN code `P`
2. Client get `public key of A` from local permanent storage, then send
   `public key of A`, `P` to [Beacon server]
3. [Beacon server] find a record with `public key of A`, then:
   1. verify `P` again the hash within the record
   2. then return the symmetric crypto key `B` to client
4. Client save symmetric crypto key `B` to local session storage


[ECC]: https://en.wikipedia.org/wiki/Elliptic-curve_cryptography "Elliptic-curve cryptography"
[Beacon server]: https://github.com/comoc-im/beacon "Signaling server of comoc IM"
