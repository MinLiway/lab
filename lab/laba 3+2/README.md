# Лабораторная 5

![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%BC%D1%83%D0%B6%D0%B8%D0%BA-%D1%81-%D0%BF%D0%B5%D1%81%D0%BA%D0%BE%D0%BC-%D1%88%D0%B0%D0%B1%D0%BB%D0%BE%D0%BD.jpg)

## Вот это мы должны сделать

 + На серверах web1, web2 необходимо установить Nginx.
 + На серверах haproxy1, haproxy2 установить и настроить отказоустойчивую связку HAProxy+Keepalived. 
 Настроить VIP с помощью Keepalived в соответствии со схемой
 + На серверах web1, web2 Nginx должен работать по порту 8080 и отдавать кастомную страницу, зайдя на которую можно понять на каком сервере вы находитесь.
 + На серверах с HAProxy ПО должно обеспечить балансировку нагрузки серверов web1 и web2 в режиме round-robin. Сделать таймауты ожидания ответа web1 и web2 как можно меньше. Тип 1-2 секунды
 + Все это нужно запихнуть в ansible сценарий

## Как запустить playbook

Поднимаем бродячую машину:
````
vagrant up
````
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-38-03.png)

Запускаем playbook:

````
ansible-playbook nginx.yml 
````

![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-39-51.png)

## Проверяем все ли машины запустились
````
vagrant status
````
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-14%2009-19-14.png)


## Проверяем балансировщик
### Если при каждом обновлении web1 и web2 меняются местами все итс гуд
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-51.png)
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-47.png)

## Если выключен haproxy1
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-51.png)
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-47.png)

## Если выключен haproxy2
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-51.png)
![](https://github.com/MinLiway/laba-2-2/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-04-13%2018-45-47.png)

## Если ничего не получилось попробуйте отправить в огонь все что было до этого (первый семестр)
## (Сжигаем мосты короч)

````
vagrant destroy --force
````

