# Задача 1. Выбор инструментов



# Задача 2. Установка терраформ

```
$ terraform -v
Terraform v1.2.9
on linux_amd64

Your version of Terraform is out of date! The latest version
is 1.4.6. You can update by downloading from https://www.terraform.io/downloads.html
```

# Задача 3. Поддержка legacy-кода
## Нужно сделать так, чтобы вы могли одновременно использовать последнюю версию Terraform, установленную при помощи штатного менеджера пакетов, и устаревшую версию

Скачал последнюю версию terraform, распаковал и переименовал исполняемый файл terraform_new.
Далее скопировал в каталог /usr/local/bin/. По аналогии можно добавлять различные версии. 
```
$ sudo cp terraform_1.4.6_linux_amd64/terraform_new /usr/local/bin/
$ terraform_new -v
Terraform v1.4.6
on linux_amd64
```
