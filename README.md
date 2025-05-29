# Домашнее задание "Средство визуализации Grafana"   

---

### Обязательные задания

### Задание 1 

1) Используя директорию help внутри этого домашнего задания, запустите связку prometheus-grafana.  
2) Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.  
3) Подключите поднятый вами prometheus, как источник данных.  
4) Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

![image.jpg](https://github.com/temagraf/Grafana/blob/main/2.png)

### Задание 2 

Изучите самостоятельно ресурсы:
- PromQL tutorial for beginners and humans.
- Understanding Machine CPU usage.
- Introduction to PromQL, the Prometheus query language.

  Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
- CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.
Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

![image.jpg](https://github.com/temagraf/Grafana/blob/main/3.png) 

**- утилизация CPU для nodeexporter (в процентах, 100-idle)**

```bash
100 - avg(irate(node_cpu_seconds_total{job="node-exporter", mode="idle"}[1m])) * 100
```

**- CPULA 1/5/15:**

```bash
avg(node_load1{job="node-exporter"})
avg(node_load5{job="node-exporter"})
avg(node_load15{job="node-exporter"})
```

**- количество свободной оперативной памяти**

```bash
node_memory_MemFree_bytes{job='nodeexporter'}
```

**- количество места на файловой системе**

```bash
node_filesystem_avail_bytes{job=~"nodeexporter",mountpoint="/",fstype!="rootfs"}
```


### Задание 3

1) Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
2) В качестве решения задания приведите скриншот вашей итоговой Dashboard.

Настроил алертинг.  
Алерты настроил чтобы отправлялись в телеграм.   
Грузанул специально комп, чтобы спровоцировать отправку алерта.  

![image.jpg](https://github.com/temagraf/Grafana/blob/main/4.png)

![image.jpg](https://github.com/temagraf/Grafana/blob/main/6.png) 


### Задание 4

Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
В качестве решения задания приведите листинг этого файла.  

Ссылка на Dashboard в json файл [New dashboar1111 - Grafana.json](https://github.com/temagraf/Grafana/blob/main/New%20dashboar1111%20-%20Grafana.json)
