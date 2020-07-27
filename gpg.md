# GnuPG

## 生成密钥

```sh
gpg --full-gen-key
```

## 加密

```sh
gpg -r recipient -R hidden-recipient -e file
```

## 解密

```sh
gpg -d file.gpg
```

## 生成 revocation certificate

```sh
gpg --output revoke.asc --gen-revoke foo@bar.baz
```
