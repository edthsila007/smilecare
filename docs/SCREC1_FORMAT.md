# SCREC1 Patient Migration Format

SCREC1 was used during testing to move individual patient records between early SmileCare prototypes.

Each `.enc` file is a JSON wrapper containing:

- `record_id`
- `iterations`
- Base64-encoded `salt`
- Base64-encoded `nonce`
- Base64-encoded `ciphertext`

Record encryption:

- Cipher: AES-256-GCM
- KDF: PBKDF2-HMAC-SHA256
- Key length: 32 bytes
- Password source: `SMILECARE_EXPORT_KEY`
- Additional authenticated data: UTF-8 encoded `record_id`

The decrypted content is a UTF-8 JSON patient record.

These migration samples contain synthetic test data only.
