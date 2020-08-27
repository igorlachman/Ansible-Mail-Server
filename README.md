# postfix_dovecot
1. Структура директорий:
- файлы конфигурации, в которых нужно сделать изменения:
dovecot_install/files_need_to_change/ 
postfix_install/files_need_to_change/

- файлы конфигурации, которые можно скопировать в том виде, как они есть, но в нужную диретокрию:
dovecot_install/stand_files/
postfix_install/stand_files/

2. Переменные, которые есть в файлах, которые нужно изменять.
Обозначение переменных - "{{some_vars}}"
Заменять нужно с удалением спецсимволов.
Пример:
Имя базы данных - posfix_mail
В файле встречам переменную "{{postfix_dbname}}"
"{{postfix_dbname}}" нужно заменить на posfix_mail

До замены:
dbname = "{{postfix_dbname}}"

После замены:
dbname = posfix_mail

3. Пути, где нужно расположить файлы.
dovecot_install/files_need_to_change/:
  dovecot-sql.conf.ext => /etc/dovecot/dovecot-sql.conf.ext

dovecot_install/stand_files/:
  10-auth.conf => /etc/dovecot/conf.d/10-auth.conf
  10-mail.conf => /etc/dovecot/conf.d/10-mail.conf
  10-master.conf => /etc/dovecot/conf.d/10-master.conf
  10-ssl.conf => /etc/dovecot/conf.d/10-ssl.conf
  15-mailboxes.conf => /etc/dovecot/conf.d/15-mailboxes.conf
  auth-sql.conf.ext => /etc/dovecot/conf.d/auth-sql.conf.ext
  dovecot.conf => /etc/dovecot/dovecot.conf
  
postfix_install/files_need_to_change:
  mysql_virtual_alias_maps.cf => /etc/postfix/sql/mysql_virtual_alias_maps.cf
  mysql_virtual_domains_maps.cf => /etc/postfix/sql/mysql_virtual_domains_maps.cf
  mysql_virtual_mailbox_limit_maps.cf => /etc/postfix/sql/mysql_virtual_mailbox_limit_maps.cf
  mysql_virtual_mailbox_maps.cf => /etc/postfix/sql/mysql_virtual_mailbox_maps.cf
  main.cf => /etc/postfix/main.cf

postfix_install/stand_files/
  master.cf => /etc/postfix/master.cf
