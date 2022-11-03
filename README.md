# Sync_Bitrix_to_SD - проект для синхронизации баз компаний Bitrix > Service Desk
 
 Проект анализирует базы компаний Bitrix и Service Desk, создает компании и переносит их данные из Bitrix в Service Desk, если их там не было. Также переименовывает компании в Service Desk, если обнаружено различие в названии с базой Bitrix.
 
 Алгоритм работы:
 1. Задаются все необходимые переменные (URL для запросов, токены);
 2. Отправляются запросы в SD и Bitrix, получаются данные о компаниях (данные о компаниях в Bitrix получаются циклически - по 50 штук за один раз, в связи с ограничениями платформы);
 3. Для каждой компании из Bitrix производится поиск компании в SD по совпадению Bitrix ID:
  - Если совпадения нет, создается компания в SD с переносом данных из Bitrix (причем для множественных параметров выбирается первый);
  - Если в SD есть компания с совпадающим Bitrix ID, производится проверка совпадения названий, в случае несовпадения компания в SD переименовывается;
 4. Отправляются соответствующие запросы в SD;
 5. Производится поиск компаний в SD, у которых нет Bitrix ID (информация об этих компаниях заносится в лог файл в директории проекта).
