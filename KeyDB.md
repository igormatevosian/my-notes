#db_design 
- получение полноценной многопоточности;
- полная и абсолютная совместимость с [[Redis]] (для нас это было особенно важно, т.к. выполнять какие-либо доработки со стороны приложения не представлялось возможным), что также сулило беспроблемную миграцию;
- встроенный механизм бэкапа в S3-хранилище;
- простая во внедрении active-репликация;
- простая кластеризация и шардирование.
![[Pasted image 20241013010702.png]]