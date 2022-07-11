# Репозиторий с выполнением домашнего задания к занятию "08.03 Использование Yandex Cloud"

## Ansible playbook отвечает за установку и запуск Clickhouse, Vector и Lighthouse на указанные сервер  

Необходимо уточнить адрес/имя серверов `ansible_host:` в файле `inventory/prod.yml`.

Также возможно заменить запуск на localhost - вместо удаленных серверов. 
Для этого необходимо заменить в Playbook `site.yml` имена префиксов у хостов:
 - "yc-" - для удаленных серверов (ВМ в YC)
 - "localhost-" - для запуска на localhost
---
# !!!Внимание!!!
На этапе установки clickhouse есть шаг, на котором в 
`/etc/clickhouse-server/config.xml` разрешается подключение к серверу 
на любых интерфейсах/с любых адресов. Использовать только для тестовых 
нужд и без публикации чувствительной информации.
---

Работоспобоность проверена на ansible версии:
```bash
ansible --version
ansible [core 2.13.1]
  config file = None
  configured module search path = ['/home/bvm/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.8/dist-packages/ansible
  ansible collection location = /home/bvm/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.8.10 (default, Mar 15 2022, 12:22:08) [GCC 9.4.0]
  jinja version = 3.1.2
  libyaml = True
```

Запуск осуществляется на окружении prod:
```bash
ansible-playbook site.yml -i ./inventory/prod.yml
```
### Автор: Vladimir Baksheev

---
