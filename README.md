# mfti-course-sre
## ДЗ 1

Последовательность развертывания:
1. Скачать https://github.com/vitabaks/postgresql_cluster
2. Поменять файлы на аналогично папке [./postgresql_cluster](./postgresql_cluster)
3. Из репозитория https://github.com/vitabaks/postgresql_cluster запустить 
```
cd automation
ansible-galaxy install --force -r requirements.yml
ansible-playbook deploy_pgcluster.yml
ansible all -i /home/fanastasiiaf/sre/postgresql_cluster/automation/inventory -m ping # для проверки запуска
```
4. Зайти на мастер бд-шки и запустить [скрипт миграции](./migration.sql)
5. Запустить `helm install my-release mfti-course-chart/`
(В случае изменения helm-а можно апгрейдить командой `helm upgrade --install my-release mfti-course-chart/`)
6. Проверить, что под запустился
7. Пробрасываем swagger `curl -X 'GET' 'https://domain-mfti-course/WeatherForecast' -H 'accept: text/plain' --insecure`
8. Добавляем хост в конец файла `sudo vim /etc/hosts`:
`176.109.82.213  domain-mfti-course`
9. Заходим по [url](https://domain-mfti-course/swagger/index.html)
10. Для проверки заходим в POST /Cities и execute-им
11. Далее смотрим что он вернул 200 и в бд появился город