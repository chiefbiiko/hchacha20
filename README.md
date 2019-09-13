# hchacha20

[![Travis](http://img.shields.io/travis/chiefbiiko/hchacha20.svg?style=flat)](http://travis-ci.org/chiefbiiko/hchacha20) [![AppVeyor](https://ci.appveyor.com/api/projects/status/github/chiefbiiko/hchacha20?branch=master&svg=true)](https://ci.appveyor.com/project/chiefbiiko/hchacha20)

HChaCha20 PRF.

Special-purpose hashing, such as X25519 key derivation, or XChacha20 initialization. If in doubt, do not use.

4 background see [djb's HSalsa20 paper](https://cr.yp.to/snuffle/xsalsa-20081128.pdf), and [the XChaCha20 IRTF CFRG draft](https://tools.ietf.org/html/draft-irtf-cfrg-xchacha-01#section-2.2).

## Usage

``` ts
import {
  hchacha20,
  OUTPUT_BYTES,
  KEY_BYTES,
  NONCE_BYTES
} from "https://denopkg.com/chiefbiiko/hchacha20/mod.ts";

const out: Uint8Array = new Uint8Array(OUTPUT_BYTES);
const key: Uint8Array = crypto.getRandomValues(new Uint8Array(KEY_BYTES));
const nonce: Uint8Array = new Uint8Array(NONCE_BYTES).fill(0x01, 0, 1);

hchacha20(out, key, nonce);

key.fill(0x00);
```

## API

#### Constants

``` ts
export const OUTPUT_BYTES: number = 32;
export const KEY_BYTES: number = 32;
export const NONCE_BYTES: number = 16;
export const CONSTANT_BYTES: number = 16;
```

#### `hchacha20(out: Uint8Array, key: Uint8Array, nonce: Uint8Array, constant?: Uint8Array): void`

`out` must be a 32-byte buffer.

## License

[MIT](./LICENSE)
