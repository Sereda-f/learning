 A/B-testing Payment
 A/B тесты процесса оплат на сайте
 Проект состоит из трех частей.     
1 часть - А/В тест и его интерпретация      
В ходе тестирования одной гипотезы целевой группе была предложена новая механика оплаты услуг на сайте, у контрольной группы оставалась базовая механика.      
Необходимо проанализировать итоги эксперимента и сделать вывод, стоит ли запускать новую механику оплаты на всех пользователей.      
Выбор анализируемых метрик и тестов производился самостоятельно.
В результате ознакомления с предоставленными данными были предложены несколько метрик для исследования и проведения А/В-теста: абсолютная конверсия, относительная конверсия из активного пользователя в покупку и ARPAU. Метрики были рассчитаны с учетом всех нюансов, выявленных на этапе исследования данных, затем с помощью тестов была определена статистическая значимость изменений в группах для каждой метрики. 

2 часть - взаимодействие с базой SQL и получение метрик из данной базы.
Были составлены SQL запросы, позволяющие рассчитать основные метрики для тех или иных групп пользователей по заданным предметам: были рассчитаны различные типы конверсий, ARPU и ARPAU.
С помощью библиотеки Pandahouse было установлено подключение к существующей базе данных, размещенной в ClickHouse, полученные результаты расчетов метрик были выведены в рабочий ноутбук.

3 часть - написание функции для автоматического подсчета метрик на основании добавленных данных, построение графиков.      
Для автоматизации подсчета метрик в различных группах при обновлении данных пользователей за последующие периоды были написаны две функции: 1 функция автоматически рассчитывает основные метрики по заданным параметрам с учетом обновленных данных; 2 функция позволяет автоматически визуализировать полученные результаты по группам для возможности предварительного анализа изменения метрик. 

В работе были использованы следующие библиотеки:     
- Requests, Urllib.parse - для получения доступа к файлам на Я.диске;    
- Pandas, Numpy - для работы c данными дата фреймов;    
- Seaborn - для построения графиков;    
- Pingouin - для проведения статистического теста хи-квадрат;    
- Pandahouse - для работы с данными в ClickHouse
- для проведения статистического теста бутстрап была использована кастомизированная функция.     

В результате работы с данными было выявлено что ARPAU статистически значимо увеличилось в тестовой группе, а относительная конверсия активных пользователей статистически значимо уменьшилась, что вносит дисбаланс и не позволяет принять однозначное решение. Был составлен ряд вопросов для уточнения к проведенному А/В тесту. 
Также были разработаны 2 функции для автоматизированного перерасчета метрик и визуализации с учетом обновляющихся данных.