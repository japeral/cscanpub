# ECDSA priv and pub key generator

This is a PoC to generate ECDSA private and public keys with C++ and measure performance

It output 2 lines:
* 1: private key in hex
* 2: public key in hex

## Curve and Hashes

* curve used: secp256r1
* hashes: sha256 for the private key and sha512 to derive the public key

## Dependencies

* [crypto++ library](https://www.cryptopp.com)
* [g++ compiler](https://gcc.gnu.org)

## How to compile

```console
g++ -g3 -O2 -Wall -Wextra -o gen_priv_pub gen_priv_pub.cpp -L/usr/local/lib -lcryptopp
```

### Build within Docker (Alpine base image, and docker multistage build ready)
```
docker build . -t cscanpub
```

## How to run

Make sure you add library in your path with

```console
LD_LIBRARY_PATH=/usr/local/lib
export LD_LIBRARY_PATH

./gen_priv_pub
```

### Run within Docker
```
docker run cscanpub
```
## openssl observ format

To generate a sec256p1 with openssl, the equivalent curve within openssl is prime256v1
```
openssl ecparam -name prime256v1 -genkey -noout -out thesuperprime.pem 
```

