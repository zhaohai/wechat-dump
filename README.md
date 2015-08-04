Wechat Database Dumper
======================

How to use
----------
- Get the wechat UIN by logging in http://web.wechat.com/ and inspect `wxuin`
  cookie record under the domain of `wx2.qq.com`.

- Dump encrypted wechat database from phone/emulator:

    `./dump_message 944818938`

- Decrypt the database:

    `./decrypt_db 867323021476294_944818938.db output.db`

- Play with the decrypted sqlite database, for example:

    `echo "select content from message;" | sqlite3 output.db`


Building `sqlciphier`
--------------------
First of all, you don't really need to build sqlciphier yourself, since
pre-built binaries has been included in the repository.

The linux pre-built binaries are taken from
https://github.com/ppwwyyxx/wechat-dump/tree/master/third-party/sqlcipher/linux/64bit

To build sqlcipher on Mac, follow:

    # Download sqlcipher from https://github.com/sqlcipher/sqlcipher/archive/v2.1.1.zip
    $ ./configure --enable-tempstore=yes --disable-tcl CFLAGS="-DSQLITE_HAS_CODEC" LDFLAGS="PATH_TO_OPENSSL_LIB/libcrypto.a"
    $ make

References
----------
- https://github.com/ppwwyyxx/wechat-dump
- http://maskray.me/blog/2014-10-14-wechat-export
