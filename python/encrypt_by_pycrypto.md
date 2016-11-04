```bash
pip install pycrypto
```

```python
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

pub_key_file = open(PUBLIC_KEY_PATH, 'r')
key = RSA.importKey(pub_key_file.read())

cipher = PKCS1_OAEP.new(public_key)

try:
	cipher_text_byte = cipher.encrypt('hoge')
	return base64.b64encode(cipher_text_byte)
except ValueError as error:
	print error
```
