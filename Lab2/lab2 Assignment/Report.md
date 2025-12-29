Utilisation de l'IA générative pour le débuggage de postgreql


Connection à la base esiee_full puis affichage des tables opérationnelles dans retail
(base) lorenzo@MacBook-Air-de-Lorenzo Data-Engineering % /opt/homebrew/opt/postgresql@17/bin/psql -d esiee_full
psql (17.7 (Homebrew))
Saisissez « help » pour l'aide.

esiee_full=# \dt retail.*
             Liste des relations
 Schéma |     Nom      | Type  | Propriétaire 
--------+--------------+-------+--------------
 retail | brand        | table | lorenzo
 retail | category     | table | lorenzo
 retail | events       | table | lorenzo
 retail | product      | table | lorenzo
 retail | product_name | table | lorenzo

Aperçu rapide de la table
 esiee_full=# select * from retail.events limit 10;
       event_time       | event_type |              session_id              | product_id |  price   
------------------------+------------+--------------------------------------+------------+----------
 2019-10-01 04:17:42+02 | view       | 521147bb-459e-4874-8153-3ab2fa290ad3 |   13700159 |   470.85
 2019-10-01 04:17:42+02 | view       | 34253b2e-b8eb-4e0a-b758-f376a41e96df |    4803710 |    25.71
 2019-10-01 04:17:42+02 | view       | dfc31a56-7292-4f70-b098-d0a2812fbdc6 |   13700226 | 18173.00
 2019-10-01 04:17:42+02 | view       | 4d74b49e-3838-43cc-ac2e-a0490942b464 |   13103842 |   391.26
 2019-10-01 04:17:42+02 | view       | 92d24e81-856a-4157-8689-d38a4a8210bf |    1004669 |    74.39
 2019-10-01 04:17:43+02 | view       | d5de76ec-7ef2-4d78-bf16-220f2ca3fcdb |    1004247 |   809.72
 2019-10-01 04:17:43+02 | view       | fd492d02-c6d6-4575-a967-e7136853eb0a |   18000964 |    19.30
 2019-10-01 04:17:43+02 | view       | d4fbe676-9a7e-48d0-9c38-a8e54a7408f5 |    9101345 |    72.14
 2019-10-01 04:17:44+02 | view       | bc9ffbe5-2245-4668-add5-3238838db13f |   16600063 |   395.89
 2019-10-01 04:17:44+02 | view       | 5271b506-9576-438f-b8c7-a7eefa8c6dba |    3100541 |    36.01
(10 lignes)

Affichage du nombre de lignes contenue dans la table
esiee_full=# select count(*) from retail.events;
  count   
----------
 42418541
(1 ligne)