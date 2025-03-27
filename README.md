# Deterministic RSA JS

**⚠️ WARNING: This project has not yet been verified to be cryptographically secure. USE AT YOUR OWN RISK! ⚠️**

## Project Overview

`deterministic-rsa-js` is a high-performance JavaScript library for generating deterministic RSA keys using native BigInt operations. Unlike traditional RSA key generation libraries, this implementation offers:

- **Deterministic Key Generation**: Generate RSA keys reproducibly from seed values
- **Superior Performance**: Approximately 3x faster than comparable implementations
- **Native JavaScript**: Leverages native `BigInt` for precise, efficient large number handling
- **Multithreaded Prime Generation**: Uses worker pools for parallel computation
- **Optimized Memory Behavior**: Minimizes garbage collection overhead

### Key Features
- Generates RSA key pairs from deterministic seeds
- Supports configurable key sizes (minimum 192 bits)
- Produces keys in standard JSON Web Key (JWK) format
- Uses advanced prime generation techniques (Miller-Rabin primality testing)
- Parallel prime number generation

## Installation

Install the library using npm:

```bash
npm install deterministic-rsa-js
```

### Prerequisites
- Node.js version that supports BigInt (v10.4.0 or later)
- Modern JavaScript runtime environment

## API Reference

### `rsaGenKeys(bits, seed, [e])`

Generates a deterministic RSA key pair.

**Parameters:**
- `bits` (number): Total bit length of the RSA key (must be multiple of 32, minimum 192)
- `seed` (Uint8Array): 32-byte seed for deterministic key generation
- `e` (optional BigInt, default: 65537n): Public exponent

**Returns:**
An object with two JWK keys:
```javascript
{
  privateKey: {
    kty: "RSA",
    n: string,   // Base64URL encoded modulus
    e: string,   // Base64URL encoded public exponent
    d: string,   // Base64URL encoded private exponent
    p: string,   // Base64URL encoded prime factor p
    q: string,   // Base64URL encoded prime factor q
    dp: string,  // CRT exponent 1
    dq: string,  // CRT exponent 2
    qi: string   // CRT coefficient
  },
  publicKey: {
    kty: "RSA",
    n: string,   // Base64URL encoded modulus
    e: string    // Base64URL encoded public exponent
  }
}
```

**Example Usage:**
```javascript
const { rsaGenKeys } = require('deterministic-rsa-js');

// Generate a 2048-bit key with a specific seed
const seed = crypto.getRandomValues(new Uint8Array(32));
const keyPair = await rsaGenKeys(2048, seed);
```

## Repository Structure

- `index.js`: Main library implementation
- `test.js`: Test suite for library functionality
- `package.json`: Project metadata and dependencies
- `LICENSE`: MIT license file

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### Running Tests
```bash
node test
```

## Roadmap / TODO

- [ ] Add optimized prime checking implementation
- [ ] Integrate native Node.js crypto module
- [ ] Explore alternative Pseudo-Random Number Generation (PRNG) methods

## Performance Notes

This library uses several optimization techniques:
- Native BigInt operations
- Multithreaded prime generation
- Efficient random number generation
- Preallocated buffers

## License

[MIT License](LICENSE)

## Disclaimer

This library is experimental. Do not use in production environments without thorough security review and testing.