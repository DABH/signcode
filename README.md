# signcode

Sign Windows executables from a Mac.

## Installing

```sh
npm install signcode
```

## Using

```js
var signcode = require('signcode')

var options = {
  cert: '/Users/kevin/certs/cert.pem',
  hash: ['sha1', 'sha256'],
  key: '/Users/kevin/certs/key.pem',
  overwrite: true
  path: '/Users/kevin/apps/myapp.exe'
}

signcode.sign(options, function (error) {
  if (error) {
    console.error('Signing failed', error.message)
  } else {
    console.log(options.path + ' is now signed')
  }
}
```

## Cert helpers commands

These commands are helpful to when working with certificates.

### Create cert and key with no password

```sh
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -nodes
```

### Create cert and key with a password

```sh
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem
```

### Show fingerprint of a cert

```sh
openssl x509 -noout -in ./test/fixtures/cert.pem -fingerprint -sha1
```

```sh
openssl x509 -noout -in ./test/fixtures/cert.pem -fingerprint -sha256
```
