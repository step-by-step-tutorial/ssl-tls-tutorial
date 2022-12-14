# <p align="center">General Concepts</p>

## Entity

Entity means a client in server/client relation that needs to interact over a secure channel, such as websites,
companies, individual persons.

## PKI

Public Key Infrastructure (PKI) is an organization to provide assurance for an entity to secure communicate with a true
service provider, by binding public key and identities.

## Certificate authority (CA)

CA is an organization that is responsible to validate the identities of entities and, it must generate private key in
order to sign a public key of an entity.

There are two CA.

* private CA: It is responsible for issuing certificate for members of its own organization.
* public CA: It is responsible for issuing certificate for any entity in the word.

```shell
# generate private
openssl genrsa -out ca-key 2048
```

```shell
# generate certificate for CA (self-sign)
openssl req -new -key ca-key -x509 -out ca.crt -days 3650
```

## Public/Private Key

The pair key is generated by an entity. Private key must be in a safe place and, it does not share with the other
entities and public key is a part should be shared with other entities. Data are encrypted by public key and decrypt
with private key. Usually private key store in a file without postfix and public key in `.pub` file.

```shell
# generate private key
openssl genrsa -out key 2048
```

```shell
# generate public key
openssl rsa -in key -outform PEM -pubout -out key.pub
```

## Certificate signing Request

```shell
# generate CSR
openssl req -new -key key -out codesigning.csr
```

## Certificate

Certificate is a digital document to bind the identity of an entity to public key. It means, certificate is a signed
public key by CA. Normally the signed public key store in `.crt` file. SSL certificates are a type of X.509 Certificate
(X.509 is a standard format for public key certificates).

* Wildcard
* SAN
* Code signing
* Self-signed
* Root

```shell
openssl x509 -req -in codesigning.csr -days 365 -CA ca.crt -CAkey ca-key -CAcreateserial -out entity.crt
```

## Chain of Trust

## Trust Anchor

## Intermediate Certificate


