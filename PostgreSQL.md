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
Пример:
```bash
pg_dump -U postgres -h localhost -p 5432 -d mydatabase -F c -b -v -f mydatabase_backup.dump
```
Передадим копию:
```bash
scp mydatabase_backup.dump user@target_host:/path/to/destination
```
Восстановим бд:
```bash
psql -U <username> -h <target_host> -p <target_port> -c "CREATE DATABASE <target_database>;"
```
```bash
pg_restore -U <username> -h <target_host> -p <target_port> -d <target_database> -v <backup_file>.dump
```

