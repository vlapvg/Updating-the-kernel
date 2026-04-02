### ДЗ: Обновление ядра системы. Тема 1: С чего начинается Linux.  
#### Описание домашнего задания
1. Запустить ВМ c Ubuntu.
2. Обновить ядро ОС на новейшую стабильную версию из mainline-репозитория.  
#### Обновление ядра (основные команды)  
##### Проверим текущую версию ядра
    vlap@april:~$ uname -r
    6.8.0-107-generic
##### Смотрим архитектуру процессора
    vlap@april:~$ uname -p
    x86_64  
##### Идём в репозиторий: <https://kernel.ubuntu.com/mainline>, ищем свежую версию ядра 

Самое свежее ядро на тот момент: **6.19.10-061910-generic**  

##### Качаем пакеты на виртуальную машину
    vlap@april:~$ mkdir kernel && cd kernel

    vlap@april:~/kernel$ wget https://kernel.ubuntu.com/mainline/v6.19.10/amd64/linux-headers-6.19.10-061910-generic_6.19.10-061910.202603251147_amd64.deb

    vlap@april:~/kernel$ wget https://kernel.ubuntu.com/mainline/v6.19.10/amd64/linux-headers-6.19.10-061910_6.19.10-061910.202603251147_all.deb

    vlap@april:~/kernel$ wget https://kernel.ubuntu.com/mainline/v6.19.10/amd64/linux-image-unsigned-6.19.10-061910-generic_6.19.10-061910.202603251147_amd64.deb

    vlap@april:~/kernel$ wget https://kernel.ubuntu.com/mainline/v6.19.10/amd64/linux-modules-6.19.10-061910-generic_6.19.10-061910.202603251147_amd64.deb  
##### Устанавливаем все пакеты сразу:

    vlap@april:~/kernel$ sudo dpkg -i *.deb  
##### Проверяем, что ядро появилось в /boot

    vlap@april:~/kernel$ ls -al /boot  
    ...
    lrwxrwxrwx  1 root root       30 Apr  1 13:42 vmlinuz -> vmlinuz-6.19.10-061910-generic
    -rw-------  1 root root 16978432 Mar 25 11:47 vmlinuz-6.19.10-061910-generic
    -rw-------  1 root root 15042952 Mar 13 17:46 vmlinuz-6.8.0-107-generic
    lrwxrwxrwx  1 root root       25 Apr  1 08:51 vmlinuz.old -> vmlinuz-6.8.0-107-generic
    ...  
##### Перезагружаем виртуальную машину
    vlap@april:~$ sudo reboot 
##### Проверяем версию ядра  

    vlap@april:~$ uname -r
    6.19.10-061910-generic  
##### Обновление ядра закончено
До обновления версия ядра была: **6.8.0-107-generic**  
После обновления стала: **6.19.10-061910-generic**


