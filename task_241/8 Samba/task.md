## установка samba
## ![img.png](img.png)
## Общая папка — это каталог, доступ к которому могут получать пользователи локальной сети.
## Обмена файлами между устройствами.
## Хранения общедоступной информации, доступной всем в сети.
## Организации работы в командах.
## Создайте общую папку без пароля с правами только на чтение файлов
## ![img_1.png](img_1.png)
## настройка
## bash
## [Read]
## path = /srv/samba/read
## browseable = yes
## read only = yes
## guest ok = yes
##  Создайте общую папку с паролем с правами на чтение и запись
## sudo mkdir -p /srv/samba/private
## sudo chmod 770 /srv/samba/private
## настройка
## [private]
## path = /srv/samba/private
## browseable = yes
## read only = no
## valid users = fgh
## Создайте общую папку с доступом для какой-то группы с полными правами
## sudo mkdir -p /srv/samba/group_share
## sudo chown -R :sambagroup /srv/samba/group_share
## sudo chmod 777 /srv/samba/group_share
## Создайте общую папку в которой у одной группы будет полный доступ, а у другой только доступ на чтение. Третья группа не должна иметь к ней доступа
## sudo setfacl -m g:readgroup:r-x /srv/samba/mixed_share
## sudo setfacl -m g:writegroup:rwx /srv/samba/mixed_share
## path = /srv/samba/mixed_share
## browseable = yes
## valid users = @read
## read only = no
##
##
##
##
##
