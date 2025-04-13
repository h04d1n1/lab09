# lab04
$ export GITHUB_USERNAME=h04d1n1
$ export GITHUB_TOKEN=<token> // Вставил свой токен

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/h04d1n1/workspace ~/h04d1n1/workspace
$ source scripts/activate

$ curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
Turning on ignore dotfiles mode.
Downloading https://github.com/rvm/rvm/archive/master.tar.gz
Installing RVM to /home/freeman/.rvm/
Installation of RVM in /home/freeman/.rvm/ is almost complete:

  * To start using RVM you need to run `source /home/freeman/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate

$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
$ . scripts/activate
$ rvm autolibs disable
$ rvm install ruby # Версия 2.4.2 не устанавливалась, make выдавал ошибку
Searching for binary rubies, this might take some time.
No binary rubies available for: arch/libc-2.41/x86_64/ruby-3.4.1.
Continuing with compilation. Please read 'rvm help mount' to get more information on binary rubies.
Installing Ruby from source to: /home/freeman/.rvm/rubies/ruby-3.4.1, this may take a while depending on your cpu(s)...
ruby-3.4.1 - #downloading ruby-3.4.1, this may take a while depending on your connection...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22.0M  100 22.0M    0     0  10.2M      0  0:00:02  0:00:02 --:--:-- 10.2M
ruby-3.4.1 - #extracting ruby-3.4.1 to /home/freeman/.rvm/src/ruby-3.4.1.....
ruby-3.4.1 - #autogen.sh.
ruby-3.4.1 - #configuring...................................................................
ruby-3.4.1 - #post-configuration..
ruby-3.4.1 - #compiling........................................................................................................
ruby-3.4.1 - #installing......................
ruby-3.4.1 - #making binaries executable...
Installed rubygems 3.6.2 is newer than 3.0.9 provided with installed ruby, skipping installation, use --force to force installation.
ruby-3.4.1 - #gemset created /home/freeman/.rvm/gems/ruby-3.4.1@global
ruby-3.4.1 - #importing gemset /home/freeman/.rvm/gemsets/global.gems...........................................................
ruby-3.4.1 - #generating global wrappers........
ruby-3.4.1 - #gemset created /home/freeman/.rvm/gems/ruby-3.4.1
ruby-3.4.1 - #importing gemsetfile /home/freeman/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-3.4.1 - #generating default wrappers........
ruby-3.4.1 - #adjusting #shebangs for (gem irb erb ri rdoc testrb rake).
Install of ruby-3.4.1 - #complete 
Ruby was built without documentation, to build it run: rvm docs generate-ri
$ rvm use 3.4.1 --default
Using /home/freeman/.rvm/gems/ruby-3.4.1
$ gem install travis
Fetching net-http-pipeline-1.0.1.gem
Fetching connection_pool-2.5.0.gem
Fetching net-http-persistent-4.0.5.gem
Fetching multi_json-1.15.0.gem
Fetching ffi-1.17.1-x86_64-linux-gnu.gem
Fetching ethon-0.16.0.gem
Fetching typhoeus-1.4.1.gem
Fetching faraday-net_http-3.0.2.gem
Fetching faraday-2.7.12.gem
Fetching faraday-typhoeus-1.1.0.gem
Fetching faraday-retry-2.3.1.gem
Fetching public_suffix-6.0.1.gem
Fetching addressable-2.8.7.gem
Fetching concurrent-ruby-1.3.5.gem
Fetching tzinfo-2.0.6.gem
Fetching i18n-1.14.7.gem
Fetching activesupport-7.0.8.7.gem
Fetching travis-gh-0.21.0.gem
Fetching rack-3.1.13.gem
Fetching rack-test-2.1.0.gem
Fetching websocket-1.2.11.gem
Fetching pusher-client-0.6.2.gem
Fetching launchy-2.5.2.gem
Fetching json_pure-2.6.3.gem
Fetching travis-1.14.0.gem
Fetching highline-2.1.0.gem
Fetching faraday-rack-2.1.2.gem
Successfully installed net-http-pipeline-1.0.1
Successfully installed connection_pool-2.5.0
Successfully installed net-http-persistent-4.0.5
Successfully installed multi_json-1.15.0
Successfully installed ffi-1.17.1-x86_64-linux-gnu
Successfully installed ethon-0.16.0
Successfully installed typhoeus-1.4.1
Successfully installed faraday-net_http-3.0.2
Successfully installed faraday-2.7.12
Successfully installed faraday-typhoeus-1.1.0
Successfully installed faraday-retry-2.3.1
Successfully installed public_suffix-6.0.1
Successfully installed addressable-2.8.7
Successfully installed concurrent-ruby-1.3.5
Successfully installed tzinfo-2.0.6
Successfully installed i18n-1.14.7
Successfully installed activesupport-7.0.8.7
Successfully installed travis-gh-0.21.0
Successfully installed rack-3.1.13
Successfully installed rack-test-2.1.0
Successfully installed websocket-1.2.11
Successfully installed pusher-client-0.6.2
Successfully installed launchy-2.5.2
Successfully installed json_pure-2.6.3
Successfully installed highline-2.1.0
Successfully installed faraday-rack-2.1.2
Successfully installed travis-1.14.0
27 gems installed

$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab04
Cloning into 'projects/lab04'...
remote: Enumerating objects: 27, done.
remote: Counting objects: 100% (27/27), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 27 (delta 4), reused 23 (delta 3), pack-reused 0 (from 0)
Receiving objects: 100% (27/27), 10.21 KiB | 232.00 KiB/s, done.
Resolving deltas: 100% (4/4), done.
$ cd projects/lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04

$ cat > .travis.yml <<EOF
language: cpp
EOF
$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF

$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
[master bc36064] added CI
 2 files changed, 14 insertions(+), 256 deletions(-)
 create mode 100644 .travis.yml
 delete mode 100644 README.md
$ git push origin master
Enumerating objects: 30, done.
Counting objects: 100% (30/30), done.
