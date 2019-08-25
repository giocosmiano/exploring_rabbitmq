- [RabbitMQ - Open Source Message Broker](https://www.rabbitmq.com/)
  - [Documentation](https://www.rabbitmq.com/documentation.html)
  - [Server Documentation](https://www.rabbitmq.com/admin-guide.html)
  - [Client Documentation](https://www.rabbitmq.com/clients.html)
  - [Developer Tools](https://www.rabbitmq.com/devtools.html)
  - [Management Plugin](https://www.rabbitmq.com/management.html)
  - [Management Command Line Tool](https://www.rabbitmq.com/management-cli.html)
  - [How to Install RabbitMQ on Ubuntu 18.04](https://tecadmin.net/install-rabbitmq-server-on-ubuntu/)

- Installing `rabbitmq` in `Ubuntu 18.04 x64`
  - [Download RabbitMQ](https://www.rabbitmq.com/download.html)
    - [Download Debian, Ubuntu - rabbitmq-server_3.7.17-1_all.deb](https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.7.17/rabbitmq-server_3.7.17-1_all.deb)
    - [Download from JFrog Bintray](https://bintray.com/rabbitmq/debian)
    - [RabbitMQ Server tags](https://github.com/rabbitmq/rabbitmq-server/tags)
      - [RabbitMQ Server v3.7.17](https://github.com/rabbitmq/rabbitmq-server/releases/tag/v3.7.17)

- Installing `erlang/otp` in `Ubuntu 18.04 x64`
  - [Download Erlang for RabbitMQ](https://www.rabbitmq.com/install-debian.html#apt-bintray-erlang)
    - [Download from JFrog Bintray](https://bintray.com/rabbitmq-erlang/debian/erlang/)

- [RabbitMQ Management Dashboard UI](http://localhost:15672)

```bash
   $ sudo dpkg -i rabbitmq-server_3.7.17-1_all.deb

   $ sudo dpkg -i erlang_21.3.8.6-1_all.deb
```

- Add these settings to `.bashrc` for personal preference

```bash
   alias rabbitmq-restart='sudo systemctl restart rabbitmq-server'
   alias rabbitmq-start='sudo systemctl start rabbitmq-server'
   alias rabbitmq-stop='sudo systemctl stop rabbitmq-server'
   alias rabbitmq-status='sudo systemctl status rabbitmq-server'
   alias rabbitmq-enable='sudo systemctl enable rabbitmq-server'
   alias rabbitmq-disable='sudo systemctl disable rabbitmq-server'
```

- Configure to start `rabbitmq` automatically with the server

```bash
   $ sudo cp rabbitmq.service /etc/systemd/system
```

- Update the `systemd` service after copying `rabbitmq` services 

```bash
   $ sudo systemctl daemon-reload
```

- Enable to auto-start `rabbitmq` service

```bash
   $ rabbitmq-enable
```

- Start/Re-Start `rabbitmq` service

```bash
   $ rabbitmq-start
   $ rabbitmq-restart
```

- Check `RabbitMQ` version

```bash
   $ sudo rabbitmqctl status
```

- Check `Erlang` version

```bash
   $ erl

   $ erl -eval 'erlang:display(erlang:system_info(otp_release)), halt().'
```

- Enable `RabbitMQ Management Dashboard UI`

```bash
   $ sudo rabbitmq-plugins enable rabbitmq_management
```

- Creating Admin User in `RabbitMQ`, `admin/secret`

```bash
   $ sudo rabbitmqctl add_user admin secret 
   $ sudo rabbitmqctl set_user_tags admin administrator
   $ sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"
```

- Install `rabbitmqadmin`
  - [Download `rabbitmqadmin` from github](https://raw.githubusercontent.com/rabbitmq/rabbitmq-management/v3.7.17/bin/rabbitmqadmin)
  - [Download from local RabbitMQ instance](http://localhost:15672/cli/rabbitmqadmin)
