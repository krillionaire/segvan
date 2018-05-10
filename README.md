Bitcoin SegWit vanity address generator
=======================================

This is a simple Bitcoin SegWit [vanity address](https://github.com/bitcoinbook/bitcoinbook/blob/develop/ch04.asciidoc#vanity-addresses) generator.

Inspired by the vanity address miner for the P2PKH non-SegWit addresses from the book ["Mastering Bitcoin" by Andreas Antonopoulos](https://github.com/bitcoinbook/bitcoinbook/). I put this code under public domain, you can do whatever you want with it.

For building you will need C++11 compatible compiler, `CMake`, `libbitcoin` and `libsodium`.
```
$ cmake .
$ make VERBOSE=1
```

Usage:
```
Usage: segvan [options] pattern
Options:
        -d      Enable debug output
        -i      Case insensitive matching
        -t num  Number of CPU threads to use (default 1)
```

Example:
```
$ time ./segvan 3Kids
Found vanity address! 3KidsZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
Private key: KPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKP

real    47m28.866s
user    44m58.046s
sys     2m30.354s
```

Then use Bitcoin Core 0.15.x console:
```
> importprivkey KPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKPKP "Vanity test" false
(null)
> getaddressesbyaccount "Vanity test"
[
  "1ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ"
]
> addwitnessaddress 1ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
3KidsZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ
```


Coin Prefixes:


| Name | Symbol | P2SH Prefix | P2SH Prefix (v2) | P2PKH Prefix | WIF Prefix |
|-------------------|--------|------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Bitcoin | BTC | [0x05](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L141) |  | [0x00](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L140) | [0x80](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L142) |
| Bitcoin (testnet) | BTC | [0xc4](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L246) |  | [0x6f](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L245) | [0xef](https://github.com/bitcoin/bitcoin/blob/f82e1c94821212cc8962775a7a29599ebd92eee0/src/chainparams.cpp#L247) |
| BLAST | BLAST | [0x12](https://github.com/blastdev/blast-core/blob/0d9a5bd6d55f026785aa98b0419fea13f7a0317c/src/chainparams.cpp#L124) |  | [0x19](https://github.com/blastdev/blast-core/blob/0d9a5bd6d55f026785aa98b0419fea13f7a0317c/src/chainparams.cpp#L123) | [0xef](https://github.com/blastdev/blast-core/blob/0d9a5bd6d55f026785aa98b0419fea13f7a0317c/src/chainparams.cpp#L125) |
| Digibyte | DGB | [0x3f](https://github.com/digibyte/digibyte/blob/5045c58d9ca2518c7f48dd1c5e51b39fece7019f/src/chainparams.cpp#L220) |  | [0x1e](https://github.com/digibyte/digibyte/blob/5045c58d9ca2518c7f48dd1c5e51b39fece7019f/src/chainparams.cpp#L218) | [0x80]( https://github.com/digibyte/digibyte/blob/5045c58d9ca2518c7f48dd1c5e51b39fece7019f/src/chainparams.cpp#L221 ) |
| Groestlcoin | GRS | [0x05](https://github.com/Groestlcoin/groestlcoin/blob/a910b33aa43fd063a143c5c05e4d852461722efa/src/groestlcoin.cpp#L407) |  | [0x24](https://github.com/Groestlcoin/groestlcoin/blob/a910b33aa43fd063a143c5c05e4d852461722efa/src/groestlcoin.cpp#L406) | [0x80](https://github.com/Groestlcoin/groestlcoin/blob/a910b33aa43fd063a143c5c05e4d852461722efa/src/groestlcoin.cpp#L408) |
| Jincoin | JIN | [0x15](https://github.com/jincoin/jincoin-core/blob/97c773bae2aaf7d34f3e553944ab7a604cdd6f4d/src/chainparams.cpp#L127) |  | [0x2b](https://github.com/jincoin/jincoin-core/blob/97c773bae2aaf7d34f3e553944ab7a604cdd6f4d/src/chainparams.cpp#L126) | [0xab](https://github.com/jincoin/jincoin-core/blob/97c773bae2aaf7d34f3e553944ab7a604cdd6f4d/src/chainparams.cpp#L128) |
| Litecoin | LTC | [0x05](https://github.com/litecoin-project/litecoin/blob/3567effe2049771a2201ae62f6edb06bf27634d2/src/chainparams.cpp#L135) | [0x32](https://github.com/litecoin-project/litecoin/blob/3567effe2049771a2201ae62f6edb06bf27634d2/src/chainparams.cpp#L136) | [0x30](https://github.com/litecoin-project/litecoin/blob/3567effe2049771a2201ae62f6edb06bf27634d2/src/chainparams.cpp#L134) | [0xb0](https://github.com/litecoin-project/litecoin/blob/3567effe2049771a2201ae62f6edb06bf27634d2/src/chainparams.cpp#L137) |
| Monacoin | MONA | [0x05](https://github.com/monacoinproject/monacoin/blob/6539eed1b32efd038d373b8e57915cf68bc2b127/src/chainparams.cpp#L137) | [0x37](https://github.com/monacoinproject/monacoin/blob/6539eed1b32efd038d373b8e57915cf68bc2b127/src/chainparams.cpp#L138) | [0x32](https://github.com/monacoinproject/monacoin/blob/6539eed1b32efd038d373b8e57915cf68bc2b127/src/chainparams.cpp#L136) | [0xb0](https://github.com/monacoinproject/monacoin/blob/6539eed1b32efd038d373b8e57915cf68bc2b127/src/chainparams.cpp#L139) |
| Myriadcoin | MYR | [0x09]( https://github.com/myriadcoin/myriadcoin/blob/561f7f7523c5c695bdb754b792e2ac1bd633fac3/src/chainparams.cpp#L182 ) |  | [0x32]( https://github.com/myriadcoin/myriadcoin/blob/561f7f7523c5c695bdb754b792e2ac1bd633fac3/src/chainparams.cpp#L181 ) | [0xb2](https://github.com/myriadcoin/myriadcoin/blob/561f7f7523c5c695bdb754b792e2ac1bd633fac3/src/chainparams.cpp#L183) |
| NAVCoin | NAV | [0x55]( https://github.com/NAVCoin/navcoin-core/blob/eeeee0e9adb2994022c81bfb7529cf392a64f5d1/src/chainparams.cpp#L161 ) |  | [0x35]( https://github.com/NAVCoin/navcoin-core/blob/eeeee0e9adb2994022c81bfb7529cf392a64f5d1/src/chainparams.cpp#L160 ) | [0x96](https://github.com/NAVCoin/navcoin-core/blob/eeeee0e9adb2994022c81bfb7529cf392a64f5d1/src/chainparams.cpp#L162) |
| Vertcoin | VTC | [ 0x05]( https://github.com/vertcoin-project/vertcoin-core/blob/1a4381eb29157c05b938a2db6d8e31cb56819ea4/src/chainparams.cpp#L137) |  | [0x47](https://github.com/vertcoin-project/vertcoin-core/blob/1a4381eb29157c05b938a2db6d8e31cb56819ea4/src/chainparams.cpp#L136) | [ 0x80]( https://github.com/vertcoin-project/vertcoin-core/blob/1a4381eb29157c05b938a2db6d8e31cb56819ea4/src/chainparams.cpp#L138) |
| Viacoin | VIA | [0x21](https://github.com/viacoin/viacoin/blob/6cf362667b227ef38796232405fb151144ed67a4/src/chainparams.cpp#L138) |  | [0x47](https://github.com/viacoin/viacoin/blob/6cf362667b227ef38796232405fb151144ed67a4/src/chainparams.cpp#L137) | [0xc7]( https://github.com/viacoin/viacoin/blob/6cf362667b227ef38796232405fb151144ed67a4/src/chainparams.cpp#L139 ) |
