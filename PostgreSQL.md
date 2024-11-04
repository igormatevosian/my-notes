#db_design #db 
![[Pasted image 20241016003018.png|400]]
- Множество типов данных
- Одновременная модификация базы (MVCC)
- Работа с большими объемами
- Поддержка сложных запросов
- Возможность расширения
- Написание функций на нескольких языках
- Высокая мощность и широкая функциональность
- Open source
- Кроссплатформенность

## Типы данных
- Числовые
- Символьные
- Бинарные
- Дата время
- Логический
- Геометрические
- Прочие (json, jsonb, uuid, xml, array, т.д.)

## Использование
### Копия бд
Создадим файл с копией
```bash
pg_dump -U <username> -h <source_host> -p <source_port> -d <source_database> -F c -b -v -f <backup_file>.dump
```
>[!example]
>```bash
> pg_dump -U postgres -h localhost -p 5432 -d mydatabase -F c -b -v 
> -f mydatabase_backup.dump
>```

Передадим копию на другую машину:
```bash
scp mydatabase_backup.dump user@target_host:/path/to/destination
```
Создадим новую пустую бд:
```bash
psql -U <username> -h <target_host> -p <target_port> -c "CREATE DATABASE <target_database>;"
```
> [!example]
> ```bash
psql -U postgres -h localhost -p 5432 -c "CREATE DATABASE mydatabase_copy;"
>```

Восстановим бд из файла с копией
```bash
pg_restore -U <username> -h <target_host> -p <target_port> -d <target_database> -v <backup_file>.dump
```
>[!example]
>```bash
pg_restore -U postgres -h localhost -p 5432 -d mydatabase_copy 
-v mydatabase_backup.dump
>```

