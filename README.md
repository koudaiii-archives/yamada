Yamada
==================


Overview
------

yamada is install to apache and PHP and MySQL.

Description
------

これはYamada用のリポジトリで、
インフラのバージョンアップを行っていくためにどうコードに残していくかを考えるキッカケにする
Chefを使うかはちょっと悩み中。

- Start
  - CentOS:5.4-i386
  - Apach:2.2.19
  - PHP:5.3.6
  - MySQL:5.1.58

- End
  - CentOS:6.5-x86
  - Apach:2.4
  - PHP:?
  - MySQL:5.6

Install
------

```
 $ git clone https://github.com/koudaiii/yamada.git
 $ bundle install
```

* Local Host IP Address 192.168.33.11
* Server(Before SSH login on the local server and can sudo)

Tips
------

## Use sahara

```
 $ vagrant sandbox on
 $ vagrant sandbox rollback
 $ vagrant sandbox off
```

## Use Chef-solo

```
 # Install Chef
 $ knife solo prepare vagrant@192.168.33.11
 # provisionning cookbook
 $ bundle exec knife solo cook 192.168.33.11
 # Start provisioning, after install Chef
 $ knife solo bootstrap [IP or hostname]
 # Not Start provisioning
 $ knife solo prepare [IP or hostname]
```

Contribution
------

```
 $ git clone https://github.com/koudaiii/yamada.git
 $ bundle install
 $ bundle exec berks
 $ bundle exec berks vendor cookbooks
 $ vagrant plugin install dotenv
 $ vagrant plugin install sahara
 $ vagrant plugin install vagrant-omnibus
 $ vagrant plugin install vagrant-berkshelf
 $ vagrant ssh-config --host webapp >> ~/.ssh/config
 $ bundle exec kitchen create
 $ bundle exec kitchen setup
 $ bundle exec kitchen converge
 $ bundle exec kitchen test
```

FAQ
------

### ERROR: Your private key could not be loaded from /etc/chef/client.pem

* add -z option

```
 $ bundle exec knife cookbook site show apache -z
```
