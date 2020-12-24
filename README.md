# linux-lab-3
## Часть 1
### Добавление пользователей
Вводим следующие команды для создания пользователей:
sudo useradd -d /home/us1 -s /bin/bash us1
sudo useradd -d /home/us2 -s /bin/bash us2
sudo useradd -d /home/us3 -s /bin/bash us3
Получим:
![](images/image.png)
### Добавление паролей
Добавляем пользователям пароли. Результат выполнения команд:
![](images/image_2020-12-24_15-16-24.png)
### Добавление группы admin.
Добавления позьлователей us1, us2 и root в группу admin следующими командами:
sudo groupadd admin
sudo usermod -aG admin us1
sudo usermod -aG admin us2
sudo usermod -aG admin root
Результаты:
![](images/image_2020-12-24_15-22-27.png)
#### Удостовериться в этом введением команд.
![](images/image_2020-12-24_15-27-38.png)
Реализация запрета всем пользователям, кроме группы admin, логин в систему по SSH в выходные дни
Устанавливаем pam_script командой sudo apt install libpam-script.
Создаем файл /usr/share/libpam-script/pam_script_acct, и пишем в нем код:
![](images/image_2020-12-24_15-40-25.png)
Далее выполняем команду sudo chmod +x /usr/share/libpam-script/pam_script_acct:
![](images/image_2020-12-24_15-38-56.png)
## Часть 2
Для установки докера были выполнены команды:

``sudo apt update && sudo apt upgrade\n
sudo apt install apt-transport-https ca-certificates curl software-properties-common\n
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -\n
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"\n
sudo apt update && apt-cache policy docker-ce\n
sudo apt install -y docker-ce``
Выдача прав пользователю pavel производилась командой:

sudo usermod -aG docker pavel 
Чтобы пользовать мог пользоваться основными командами docker'a необходимо установить пакет docker compose, для этого необходимо выполнить следующие команды:
