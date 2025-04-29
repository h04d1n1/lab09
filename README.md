$ export GITHUB_TOKEN=<токен> # не указываю, чтобы git не ругался
$ export GITHUB_USERNAME=h04d1n1
$ export PACKAGE_MANAGER=yay
$ export GPG_PACKAGE_NAME=gnupg # на archlinux так пакет называется

$ sudo $PACKAGE_MANAGER -Sy xclip
:: Synchronizing package databases...
 core is up to date
 extra                        7.7 MiB  2.77 MiB/s 00:03 [##############################] 100%
 multilib                   136.0 KiB   303 KiB/s 00:00 [##############################] 100%
warning: xclip-0.13-6 is up to date -- reinstalling
resolving dependencies...
looking for conflicting packages...

Packages (1) xclip-0.13-6

Total Installed Size:  0.03 MiB
Net Upgrade Size:      0.00 MiB

:: Proceed with installation? [Y/n] y
(1/1) checking keys in keyring                          [##############################] 100%
(1/1) checking package integrity                        [##############################] 100%
(1/1) loading package files                             [##############################] 100%
(1/1) checking for file conflicts                       [##############################] 100%
(1/1) checking available disk space                     [##############################] 100%
:: Processing package changes...
(1/1) reinstalling xclip                                [##############################] 100%
:: Running post-transaction hooks...
(1/1) Arming ConditionNeedsUpdate...
$ alias gsed=sed
$ alias pbcopy='xclip -selection clipboard'
$ alias pbpaste='xclip -selection clipboard -o'

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/h04d1n1/workspace ~/h04d1n1/workspace
$ source scripts/activate
$ go install github.com/aktau/github-release@latest
go: downloading github.com/aktau/github-release v0.10.1
go: finding module for package github.com/voxelbrain/goptions
go: finding module for package github.com/dustin/go-humanize
go: finding module for package github.com/github-release/github-release/github
go: downloading github.com/dustin/go-humanize v1.0.1
go: downloading github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: downloading github.com/github-release/github-release v0.10.1
go: found github.com/dustin/go-humanize in github.com/dustin/go-humanize v1.0.1
go: found github.com/github-release/github-release/github in github.com/github-release/github-release v0.10.1
go: found github.com/voxelbrain/goptions in github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: finding module for package github.com/tomnomnom/linkheader
go: finding module for package github.com/kevinburke/rest/restclient
go: downloading github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
go: downloading github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/kevinburke/rest/restclient in github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/tomnomnom/linkheader in github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80

$ git clone https://github.com/${GITHUB_USERNAME}/lab08 projects/lab09
Cloning into 'projects/lab09'...
remote: Enumerating objects: 292, done.
remote: Counting objects: 100% (292/292), done.
remote: Compressing objects: 100% (139/139), done.
remote: Total 292 (delta 118), reused 288 (delta 117), pack-reused 0 (from 0)
Receiving objects: 100% (292/292), 179.38 KiB | 838.00 KiB/s, done.
Resolving deltas: 100% (118/118), done.
$ cd projects/lab09
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab09

$ gsed -i 's/lab08/lab09/g' README.md

$ $PACKAGE_MANAGER -S ${GPG_PACKAGE_NAME}
$ gpg --list-secret-keys --keyid-format LONG
$ gpg --full-generate-key
gpg (GnuPG) 2.4.7; Copyright (C) 2024 g10 Code GmbH
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (9) ECC (sign and encrypt) *default*
  (10) ECC (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 
Requested keysize is 3072 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: h04d1n1
Email address: fedor.z1234@yandex.ru
Comment: 
You selected this USER-ID:
    "h04d1n1 <fedor.z1234@yandex.ru>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: revocation certificate stored as '/home/freeman/.gnupg/openpgp-revocs.d/2E039652A85F61D27ADF880C3472435DAC1CDE1F.rev'
public and secret key created and signed.

pub   rsa3072 2025-04-29 [SC]
      2E039652A85F61D27ADF880C3472435DAC1CDE1F
uid                      h04d1n1 <fedor.z1234@yandex.ru>
sub   rsa3072 2025-04-29 [E]
$ gpg -K ${GITHUB_USERNAME}
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
sec   rsa3072 2025-04-29 [SC]
      2E039652A85F61D27ADF880C3472435DAC1CDE1F
uid           [ultimate] h04d1n1 <fedor.z1234@yandex.ru>
ssb   rsa3072 2025-04-29 [E]
$ GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
$ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
$ gpg --armor --export ${GPG_KEY_ID} | pbcopy
$ pbpaste
-----BEGIN PGP PUBLIC KEY BLOCK-----

mQGNBGgQn7IBDADXAYwd+fs2Kf8vc/5G0Mtn/YNRlZoeSTtLQ6uJzXDkouPPHBn1
5MnPQ9mphfltnupr5U72MnLIYM2K16ss34ErBPzsO2Rc7JdBcHlFqXt/fY7rolFU
QaTQ5RclC2dQgKijeHmuiwkqKN09Li+QsQcY2sgoB4BrLdWza5c3A+u2As0VRrfG
pBnD9p3sjKdSio0MmT8FgziJtSAAmiDatL5USuImTlExeeYjYKBUoplByE7eNSZQ
9XnDN12uQ5FctSW17iaYdbQosT8Yj44vsfapCT5yuUJzBdkdgx+Q4fxrBGY+MqfD
RwqFXzsovms8vdQiOQq8Xevr8QaSYchU82Qhoeq6dbCDAJg+oiE32ryYMv5PJGXb
C55EmP616tGa6dfeF3TykqkEQtGBhye+1SVDRk3/DK+6kb4SN4bAiEdp/B500pks
s+6Fyn0gVYFhhKRNCyPHouTBlqVh03RhGo3BBtJx6643G1wS3O9TYMnjO6GIzsyx
Jy9vPxguCbweb2MAEQEAAbQfaDA0ZDFuMSA8ZmVkb3IuejEyMzRAeWFuZGV4LnJ1
PokB0QQTAQgAOxYhBC4DllKoX2HSet+IDDRyQ12sHN4fBQJoEJ+yAhsDBQsJCAcC
AiICBhUKCQgLAgQWAgMBAh4HAheAAAoJEDRyQ12sHN4fLrQL/jtSWZ1TvugaCE0o
xywpPazi/DbnXoxUBamXM0iTYVkdywX3d8+P2U1UgV8JGGBr/AofWtBTDm/zwJwq
O1SRap+zcT5hogOW8irv7LNCCtsSS+qvL7nMqIEY1Sk8h7241XTHsductntMYztI
alWiT45tjPldFND9IVhlR4sluLwFgM+HpUnnRJK3sWyY8vD+6YwuNMtYc0QKNjJd
WlM5kuy3J8Znss7rdotSkL7Mxt4BcLQ1fpjt894WPD83j3S09jE0yAwOI1u90IUQ
eHaf8J13FDeI3E7Kbh+l/jXTGskUVFwqCjsG9CDh5MkMLqxMJxAh+YErcW5z4Esn
cprf+rr03EcSW/MO0rl0Xa7gHSB6cuxSjscKwa1j4IgLBMgTKXiZYh6Uj9AH6DtA
7G9V0nK2NFs8H2Z2v4ZMAXjanq9duoQF5+A6pPBYNB8gRtf+2rNXy/Hcv3j+jlIM
hYwkyEoHkgq6nq8my9gTbFNxACCvA77SlQHsFn24TuznO1KZqrkBjQRoEJ+yAQwA
vG0dry+2o2f+lpe/oLED/Fj6+ZQ+sjUzZZm02GmikNWw0m2En5PlAqgnQZVcs1Qi
UKVgW2D3aSW6NEAbaYImbCu1wLwZLIGKckKzuJp352HsSNxNJGosRIDLsNpFJCO6
Ui6FxiGmHRWV+TZr5XuyjHdqrgWgc2+Nx4YlGBFUP7ruSJ6tyznbnvt+aI+biVYt
xjZvgquwlrLrrXE8DdpayoTQQg98b3Xs2m+UBAufOTckqIQaXK46J6NcdZvIzJU9
AXIqw1F3sqcea5ZzFatpkdjh2UieXXg3Wva/WBfmJEvHTINhSEBpTn1GY13ztKb7
UTZx70r+jU3fn16xNMCgk8vchGA6kzyRmCOrsq8aLFn+OSn2nM7JdE7jVDI9jOkW
K330jV39lbyVV2xtyQCagl1Kl11Gdz2G1KxxF7oFQCTyv7ieb7uzsT+Ryqk19J1S
VpQdGfRhJhuj0yE1cKoGABT6lB5OyajXvPxGXx6upOgHXPSMqyYK5LTzT5/V1Ynv
ABEBAAGJAbYEGAEIACAWIQQuA5ZSqF9h0nrfiAw0ckNdrBzeHwUCaBCfsgIbDAAK
CRA0ckNdrBzeH+nIC/9jKy6uPT3AuZBFOD3AjX2dT3jEtldc8w24uT7FtB70/Red
eZ/daobjI8jU/CadDtxpaFulzJ0MAxaJUQ+ed4wNFoFI0mI0yxNgS6ZG84CwkErz
HnOxiWYvcD7X/8rFOt2OyOYgL9V047SaGe7r8PzYKAwXN+iYa5btryZgn++TVoCB
BL9kHMXS8lAC44+yagVPhCtyz01rge8cugUNCw0FAOzgR3XVN62+ASfb22QHztQF
9AdF8mpylsDLuLrtIrsPZdFcf4Wuz4f3xc9BmksA7Rc7wndSeTMu9lJ8tMw3NK67
A9ME61hgQc3qxTS5Rlvl0RO1UsSrdkToInE4hrbyWxepm2u8vOoJqt10ReCHLj8h
3eSATSpd+pS31X2BTEVaLz0W162OS+cOMVqB4RYDKxvYqeoG9NsH+x3r9cFJr4ET
7hOdYk0FsFoifY99J4MyPwu0+ZJvi5xw/ilnjHAdA6cI/NcxIT1n8mwb6mU2msTe
gmOSXi6D4R5iCprRMd0=
=kZ1g
-----END PGP PUBLIC KEY BLOCK-----
$ open https://github.com/settings/keys
Using default fileManager (gio command) opening ...
# Создал там новый ключ GPG. Записал туда вывод предпоследней команды
$ git config user.signingkey ${GPG_SEC_KEY_ID}
$ git config gpg.program gpg

$ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile
$ echo 'export GPG_TTY=$(tty)' >> ~/.profile

$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_set_config_location.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:13 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:34 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_private_data.cmake:12 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:35 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_initialize.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/Hunter:36 (include)
  cmake/HunterGate.cmake:540 (include)
  CMakeLists.txt:3 (HunterGate)


-- The C compiler identification is GNU 14.2.1
-- The CXX compiler identification is GNU 14.2.1
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.


-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/freeman/.hunter
-- [hunter] [ Hunter-ID: 26c79d5 | Toolchain-ID: bf48b43 | Config-ID: d14f46d ]
CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_set_config_location.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:13 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_config_sha1.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:9 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_toolchain_sha1.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:10 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_set_config_location.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_apply_gate_settings.cmake:13 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_calculate_self.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_finalize.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_cache_run.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_create_cache_meta_directory.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_create_cache_meta_directory.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_load_from_cache.cmake:6 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:22 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_create_cache_meta_directory.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_save_to_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:26 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_create_cache_meta_directory.cmake:5 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_save_to_cache.cmake:4 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:26 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_save_to_cache.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:26 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_save_to_cache.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:26 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


CMake Deprecation Warning at /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_lock_directory.cmake:4 (cmake_minimum_required):
  Compatibility with CMake < 3.10 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value.  Or, use the <min>...<max> syntax
  to tell CMake that the project requires at least <min> but has been updated
  to work with policies introduced by <max> or earlier.
Call Stack (most recent call first):
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_make_directory.cmake:7 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_save_to_cache.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_download.cmake:26 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/projects/GTest/hunter.cmake:8 (include)
  /home/freeman/.hunter/_Base/Download/Hunter/0.25.8/26c79d5/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
  CMakeLists.txt:26 (hunter_add_package)


-- [hunter] GTEST_ROOT: /home/freeman/.hunter/_Base/26c79d5/bf48b43/d14f46d/Install (ver.: 1.15.2)
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done (1.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/freeman/h04d1n1/workspace/projects/lab09/_build
$ cmake --build _build --target package
[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/freeman/h04d1n1/workspace/projects/lab09/_build/print-0.1.0.0-Linux.tar.gz generated.

$ git tag -s v0.1.0.0
$ git tag -v v0.1.0.0
object 49abec24363108acffcbadaa75ab9bf2e6e70e4a
type commit
tag v0.1.0.0
tagger h04d1n1 <fedor.z1234@yandex.ru> 1745920935 +0300

tag v0.1.0.0
gpg: Signature made Tue 29 Apr 2025 01:02:57 PM MSK
gpg:                using RSA key 2E039652A85F61D27ADF880C3472435DAC1CDE1F
gpg: Good signature from "h04d1n1 <fedor.z1234@yandex.ru>" [ultimate]
$ git show v0.1.0.0
tag v0.1.0.0
Tagger: h04d1n1 <fedor.z1234@yandex.ru>
Date:   Tue Apr 29 13:02:15 2025 +0300

tag v0.1.0.0
-----BEGIN PGP SIGNATURE-----

iQGzBAABCAAdFiEELgOWUqhfYdJ634gMNHJDXawc3h8FAmgQo9EACgkQNHJDXawc
3h9GHwv/XY/6BNfNPGIicbxkTScG5chWgg5QORbn7+BxRUG3VddGPfqD6gufpoX8
ffhUYD706sIuuSI19yP85Rljbu58yxv0rAtdoYO36OTIwnMM1qhYmLI2/uvTPEbP
BP5hmzERjn/F5UKulo6uvBhDLCPsvpDHt4sKlL6okpzIRCUGUE7qvAaZ7NAebHtO
W7cyYdq6LrGYMRHR3f3UbsRAedUQLKi8glQqrgK5tSvGoNFp1Efj7OlRtruzQXCH
GjKT9N88wzrldmqb6nS2nnUBQCNFgetEAJ7vaeEfY53jsoTm7jp76EgbaME+lFmH
xkjbPt/eZQg/zRsQjeOqsOfNqjd0kRG6pPln9ld7BCnos7aCRldkwQY7d62NVlry
IRGW13JVTBhoHtCaeas9SsWIKJ4nF6KKRk/kUAxLbk+7TxKBiTLROSNngIP/EFFd
e+xQNSe7w1BvoRH7tdJKrkGyNBXCsXg2V4mvk+qRKVi4o7B8wTWt0LZn0D5p45vL
2mNejIi/
=7G+/
-----END PGP SIGNATURE-----

commit 49abec24363108acffcbadaa75ab9bf2e6e70e4a (HEAD -> main, tag: v0.1.0.0)
Author: h04d1n1 <93523461+h04d1n1@users.noreply.github.com>
Date:   Mon Apr 28 12:57:16 2025 +0300

    Update README.md

diff --git a/README.md b/README.md
index 6a76314..ba3b15f 100644
--- a/README.md
+++ b/README.md
@@ -1,3311 +1,232 @@
 $ export GITHUB_USERNAME=h04d1n1
-$ alias gsed=sed
 
 $ cd ${GITHUB_USERNAME}/workspace
 $ pushd .
 ~/h04d1n1/workspace ~/h04d1n1/workspace
 $ source scripts/activate
 
-$ git clone https://github.com/${GITHUB_USERNAME}/lab06 projects/lab07
-Cloning into 'projects/lab07'...
-remote: Enumerating objects: 98, done.
-remote: Counting objects: 100% (98/98), done.
-remote: Compressing objects: 100% (66/66), done.

# Дальше можно было листать и скопировать, но там изменения с прошлой лабораторной работы, а их очень много

$ git push origin main --tags
Enumerating objects: 293, done.
Counting objects: 100% (293/293), done.
Delta compression using up to 8 threads
Compressing objects: 100% (139/139), done.
Writing objects: 100% (293/293), 179.96 KiB | 89.98 MiB/s, done.
Total 293 (delta 118), reused 292 (delta 118), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (118/118), done.
To https://github.com/h04d1n1/lab09
 * [new branch]      main -> main
 * [new tag]         v0.1.0.0 -> v0.1.0.0
 
$ github-release --version
github-release v0.10.1
$ github-release info -u ${GITHUB_USERNAME} -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/h04d1n1/lab09/commits/49abec24363108acffcbadaa75ab9bf2e6e70e4a)
releases:
$ github-release release \
    --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"
    
$ export PACKAGE_OS=`uname -s` PACKAGE_ARCH=`uname -m` 
$ export PACKAGE_FILENAME=print-${PACKAGE_OS}-${PACKAGE_ARCH}.tar.gz
$ github-release upload \
    --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "${PACKAGE_FILENAME}" \
    --file _build/*.tar.gz
    
$ github-release info -u ${GITHUB_USERNAME} -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/h04d1n1/lab09/commits/49abec24363108acffcbadaa75ab9bf2e6e70e4a)
releases:
- v0.1.0.0, name: 'libprint', description: 'my first release', id: 215431279, tagged: 29/04/2025 at 10:02, published: 29/04/2025 at 10:21, draft: ✗, prerelease: ✗
  - artifact: print-Linux-x86_64.tar.gz, downloads: 0, state: uploaded, type: application/octet-stream, size: 5.8 kB, id: 250383790
$ wget https://github.com/${GITHUB_USERNAME}/lab09/releases/download/v0.1.0.0/${PACKAGE_FILENAME}
--2025-04-29 13:24:38--  https://github.com/h04d1n1/lab09/releases/download/v0.1.0.0/print-Linux-x86_64.tar.gz
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/974230749/bed9779e-cc0a-4494-9728-1c1ee003b9ff?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250429%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250429T102439Z&X-Amz-Expires=300&X-Amz-Signature=4ff06a6c7662dcf833dd0eda731c21713f26c39b6810ec3e047a5e5bf2624a21&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream [following]
--2025-04-29 13:24:39--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/974230749/bed9779e-cc0a-4494-9728-1c1ee003b9ff?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250429%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250429T102439Z&X-Amz-Expires=300&X-Amz-Signature=4ff06a6c7662dcf833dd0eda731c21713f26c39b6810ec3e047a5e5bf2624a21&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.108.133, 185.199.109.133, 185.199.110.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5787 (5.7K) [application/octet-stream]
Saving to: ‘print-Linux-x86_64.tar.gz’

print-Linux-x86_64.tar. 100%[============================>]   5.65K  --.-KB/s    in 0.01s   

2025-04-29 13:24:40 (474 KB/s) - ‘print-Linux-x86_64.tar.gz’ saved [5787/5787]
$ tar -ztf ${PACKAGE_FILENAME}
print-0.1.0.0-Linux/cmake/
print-0.1.0.0-Linux/cmake/print-config.cmake
print-0.1.0.0-Linux/cmake/print-config-noconfig.cmake
print-0.1.0.0-Linux/bin/
print-0.1.0.0-Linux/bin/demo
print-0.1.0.0-Linux/lib/
print-0.1.0.0-Linux/lib/libprint.a
print-0.1.0.0-Linux/include/
print-0.1.0.0-Linux/include/print.hpp

