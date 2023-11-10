### Bloque 1

##### Consultas

1. Listar los nombres de los usuarios

   ```sql
   mysql> SELECT nombre FROM tblUsuarios;
   +-----------+
   | nombre    |
   +-----------+
   | BRENDA    |
   | OSCAR     |
   | JOSE      |
   | LUIS      |
   | LUIS      |
   | DANIEL    |
   | JAQUELINE |
   | ROMAN     |
   | BLAS      |
   | JESSICA   |
   | DIANA     |
   | RICARDO   |
   | VALENTINA |
   | BRENDA    |
   | LUCIA     |
   | JUAN      |
   | ELPIDIO   |
   | JESSICA   |
   | LETICIA   |
   | LUIS      |
   | HUGO      |
   +-----------+
   
   ```

2. Calcular el saldo máximo de los usuarios de sexo “Mujer”

     ```sql
     mysql> SELECT sexo,max(saldo)  FROM tblUsuarios where sexo='M';
     +------+------------+
     | sexo | max(saldo) |
     +------+------------+
     | M    |        500 |
     +------+------------+
     
     ```

3. Listar nombre y teléfono de los usuarios con teléfono NOKIA, BLACKBERRY o SONY

     ```sql
     mysql> select nombre,telefono,marca from tblUsuarios where marca='NOKIA' or marca='BLACKBERRY' or marca='SONY';
     +-----------+--------------+------------+
     | nombre    | telefono     | marca      |
     +-----------+--------------+------------+
     | JOSE      | 655-143-3922 | NOKIA      |
     | LUIS      | 655-100-8260 | NOKIA      |
     | DANIEL    | 655-145-2586 | SONY       |
     | JAQUELINE | 655-330-5514 | BLACKBERRY |
     | DIANA     | 655-143-3952 | SONY       |
     | VALENTINA | 655-137-4253 | BLACKBERRY |
     | LUCIA     | 655-145-4992 | BLACKBERRY |
     | JESSICA   | 655-330-5143 | SONY       |
     | LETICIA   | 655-143-4019 | BLACKBERRY |
     | LUIS      | 655-100-5085 | SONY       |
     +-----------+--------------+------------+
     ```

4. Contar los usuarios sin saldo o inactivos

     ```sql
     mysql> select saldo,activo,count(*) as inactivos_sinSaldo  from tblUsuarios where saldo=0 or activo=0 group by saldo, activo;
     +-------+--------+--------------------+
     | saldo | activo | inactivos_sinSaldo |
     +-------+--------+--------------------+
     |     0 |      1 |                  3 |
     |    50 |      0 |                  2 |
     |   100 |      0 |                  1 |
     |     0 |      0 |                  1 |
     +-------+--------+--------------------+
     
     ```

5. Listar el login de los usuarios con nivel 1, 2 o 3

     ```sql
     mysql> select nombre,email,nivel from tblUsuarios where nivel<>0;
     +---------+---------------------+-------+
     | nombre  | email               | nivel |
     +---------+---------------------+-------+
     | BRENDA  | brenda@live.com     |     2 |
     | OSCAR   | oscar@gmail.com     |     3 |
     | JOSE    | francisco@gmail.com |     3 |
     | LUIS    | luis@hotmail.com    |     1 |
     | ROMAN   | roman@gmail.com     |     2 |
     | JESSICA | jessica@hotmail.com |     1 |
     | DIANA   | diana@live.com      |     1 |
     | RICARDO | ricardo@hotmail.com |     2 |
     | BRENDA  | brenda2@gmail.com   |     3 |
     | LUCIA   | lucia@gmail.com     |     3 |
     | ELPIDIO | elpidio@outlook.com |     1 |
     | JESSICA | jessica2@live.com   |     3 |
     | LETICIA | leticia@yahoo.com   |     2 |
     | LUIS    | luis2@live.com      |     3 |
     | HUGO    | hugo@live.com       |     2 |
     +---------+---------------------+-------+
     
     ```

6. Listar los números de teléfono con saldo menor o igual a 300

     ```sql
     mysql> select telefono,saldo from tblUsuarios where saldo<=300;
     +--------------+-------+
     | telefono     | saldo |
     +--------------+-------+
     | 655-330-5736 |   100 |
     | 655-143-4181 |     0 |
     | 655-143-3922 |   150 |
     | 655-137-1279 |    50 |
     | 655-100-8260 |    50 |
     | 655-145-2586 |   100 |
     | 655-330-5514 |     0 |
     | 655-330-3263 |    50 |
     | 655-330-3871 |   100 |
     | 655-143-3952 |   100 |
     | 655-145-6049 |   150 |
     | 655-137-4253 |    50 |
     | 655-100-1351 |   150 |
     | 655-145-4992 |     0 |
     | 655-100-6517 |     0 |
     | 655-330-5143 |   200 |
     | 655-143-4019 |   100 |
     | 655-100-5085 |   150 |
     +--------------+-------+
     
     ```

7. Calcular la suma de los saldos de los usuarios de la compañia telefónica NEXTEL

     ```sql
     mysql> select sum(saldo),compañia from tblUsuarios where compañia='NEXTEL';
     +------------+-----------+
     | sum(saldo) | compañia  |
     +------------+-----------+
     |        150 | NEXTEL    |
     +------------+-----------+
     
     ```

8. Contar el número de usuarios por compañía telefónica

     ```sql
     mysql> select compañia, count(*) as usuarios_compañia from tblUsuarios group by compañia order by compañia;
     +-----------+--------------------+
     | compañia  | usuarios_compañia  |
     +-----------+--------------------+
     | AT&T      |                  2 |
     | AXEL      |                  2 |
     | IUSACELL  |                  6 |
     | MOVISTAR  |                  2 |
     | NEXTEL    |                  1 |
     | TELCEL    |                  3 |
     | UNEFON    |                  5 |
     +-----------+--------------------+
     
     ```

9. Contar el número de usuarios por nivel

     ```sql
     mysql> select nivel, count(*) as usuarios_compañia from tblUsuarios group by nivel order by nivel;
     +-------+--------------------+
     | nivel | usuarios_compañia  |
     +-------+--------------------+
     |     0 |                  6 |
     |     1 |                  4 |
     |     2 |                  5 |
     |     3 |                  6 |
     +-------+--------------------+
     
     ```

10. Listar el login de los usuarios con nivel 2

       ```sql
        mysql> select nombre,email,nivel from tblUsuarios where nivel=2;
       +---------+---------------------+-------+
       | nombre  | email               | nivel |
       +---------+---------------------+-------+
       | BRENDA  | brenda@live.com     |     2 |
       | ROMAN   | roman@gmail.com     |     2 |
       | RICARDO | ricardo@hotmail.com |     2 |
       | LETICIA | leticia@yahoo.com   |     2 |
       | HUGO    | hugo@live.com       |     2 |
       +---------+---------------------+-------+
       
       ```

11. Mostrar el email de los usuarios que usan gmail

        ```sql
        mysql> select email from tblUsuarios WHERE email LIKE '%gmail%';
        +---------------------+
        | email               |
        +---------------------+
        | oscar@gmail.com     |
        | francisco@gmail.com |
        | roman@gmail.com     |
        | brenda2@gmail.com   |
        | lucia@gmail.com     |
        +---------------------+
        
        ```

12. Listar nombre y teléfono de los usuarios con teléfono LG, SAMSUNG o MOTOROLA

      ```sql
      mysql> select nombre,telefono from tblUsuarios where marca='LG' or marca='SAMSUNG' or marca='MOTOROLA' order by nombre;
      +---------+--------------+
      | nombre  | telefono     |
      +---------+--------------+
      | BLAS    | 655-330-3871 |
      | BRENDA  | 655-330-5736 |
      | BRENDA  | 655-100-1351 |
      | ELPIDIO | 655-145-9938 |
      | HUGO    | 655-137-3935 |
      | JESSICA | 655-143-6861 |
      | JUAN    | 655-100-6517 |
      | LUIS    | 655-137-1279 |
      | OSCAR   | 655-143-4181 |
      | RICARDO | 655-145-6049 |
      | ROMAN   | 655-330-3263 |
      +---------+--------------+
      
      ```

------

### Bloque 2

##### Consultas

1. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca LG o SAMSUNG

     ```sql
     mysql> select nombre,telefono from tblUsuarios where marca<>"LG" and marca<>'SAMSUNG' ORDER BY nombre ;
     +-----------+--------------+
     | nombre    | telefono     |
     +-----------+--------------+
     | BRENDA    | 655-100-1351 |
     | DANIEL    | 655-145-2586 |
     | DIANA     | 655-143-3952 |
     | ELPIDIO   | 655-145-9938 |
     | HUGO      | 655-137-3935 |
     | JAQUELINE | 655-330-5514 |
     | JESSICA   | 655-330-5143 |
     | JOSE      | 655-143-3922 |
     | LETICIA   | 655-143-4019 |
     | LUCIA     | 655-145-4992 |
     | LUIS      | 655-100-8260 |
     | LUIS      | 655-100-5085 |
     | RICARDO   | 655-145-6049 |
     | VALENTINA | 655-137-4253 |
     +-----------+--------------+
     
     ```

2. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL

     ```sql
      mysql> select usuario,email,telefono from tblUsuarios where compañia='IUSACELL';
     +---------+---------------------+--------------+
     | usuario | email               | telefono     |
     +---------+---------------------+--------------+
     | BRE2271 | brenda@live.com     | 655-330-5736 |
     | LUI7072 | luis@hotmail.com    | 655-100-8260 |
     | ROM6520 | roman@gmail.com     | 655-330-3263 |
     | RIC8283 | ricardo@hotmail.com | 655-145-6049 |
     | LUC4982 | lucia@gmail.com     | 655-145-4992 |
     | JES9640 | jessica2@live.com   | 655-330-5143 |
     +---------+---------------------+--------------+
     
     ```

3. Listar el login y teléfono de los usuarios con compañia telefónica que no sea TELCEL

     ```sql
     mysql> select usuario,email,telefono from tblUsuarios where compañia<>'TELCEL';
     +---------+-----------------------+--------------+
     | usuario | email                 | telefono     |
     +---------+-----------------------+--------------+
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | JOS7086 | francisco@gmail.com   | 655-143-3922 |
     | LUI7072 | luis@hotmail.com      | 655-100-8260 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | RIC8283 | ricardo@hotmail.com   | 655-145-6049 |
     | VAL6882 | valentina@live.com    | 655-137-4253 |
     | BRE8106 | brenda2@gmail.com     | 655-100-1351 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | ELP2984 | elpidio@outlook.com   | 655-145-9938 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |
     | HUG5441 | hugo@live.com         | 655-137-3935 |
     +---------+-----------------------+--------------+
     
     ```

4. Calcular el saldo promedio de los usuarios que tienen teléfono marca NOKIA

     ```sql
     mysql>  select round(AVG(saldo)) as promedio from tblUsuarios where marca='NOKIA';
     +----------+
     | promedio |
     +----------+
     |      100 |
     +----------+
     
     ```

5. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL o AXEL

     ```sql
      mysql> select usuario,email,telefono from tblUsuarios where compañia='IUSACELL' or compañia='AXEL';
     +---------+-----------------------+--------------+
     | usuario | email                 | telefono     |
     +---------+-----------------------+--------------+
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | LUI7072 | luis@hotmail.com      | 655-100-8260 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | RIC8283 | ricardo@hotmail.com   | 655-145-6049 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |
     +---------+-----------------------+--------------+
     
     ```

6. Mostrar el email de los usuarios que no usan yahoo

     ```sql
      mysql> select email from tblUsuarios WHERE email not LIKE '%yahoo%';
     +-----------------------+
     | email                 |
     +-----------------------+
     | brenda@live.com       |
     | oscar@gmail.com       |
     | francisco@gmail.com   |
     | enrique@outlook.com   |
     | luis@hotmail.com      |
     | daniel@outlook.com    |
     | jaqueline@outlook.com |
     | roman@gmail.com       |
     | blas@hotmail.com      |
     | jessica@hotmail.com   |
     | diana@live.com        |
     | ricardo@hotmail.com   |
     | valentina@live.com    |
     | brenda2@gmail.com     |
     | lucia@gmail.com       |
     | juan@outlook.com      |
     | elpidio@outlook.com   |
     | jessica2@live.com     |
     | luis2@live.com        |
     | hugo@live.com         |
     +-----------------------+
     
     ```

7. Listar el login y teléfono de los usuarios con compañia telefónica que no sea TELCEL o IUSACELL

     ```sql
      mysql> select usuario,email,telefono from tblUsuarios where compañia<>'IUSACELL' and compañia<>'TELCEL';
     +---------+-----------------------+--------------+
     | usuario | email                 | telefono     |
     +---------+-----------------------+--------------+
     | JOS7086 | francisco@gmail.com   | 655-143-3922 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | VAL6882 | valentina@live.com    | 655-137-4253 |
     | BRE8106 | brenda2@gmail.com     | 655-100-1351 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | ELP2984 | elpidio@outlook.com   | 655-145-9938 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |
     | HUG5441 | hugo@live.com         | 655-137-3935 |
     +---------+-----------------------+--------------+
     
     ```

8. Listar el login y teléfono de los usuarios con compañia telefónica UNEFON

     ```sql
     mysql> select usuario,email,telefono from tblUsuarios where compañia='UNEFON';
     +---------+--------------------+--------------+
     | usuario | email              | telefono     |
     +---------+--------------------+--------------+
     | DAN2832 | daniel@outlook.com | 655-145-2586 |
     | BLA9739 | blas@hotmail.com   | 655-330-3871 |
     | DIA6570 | diana@live.com     | 655-143-3952 |
     | LET4015 | leticia@yahoo.com  | 655-143-4019 |
     | LUI1076 | luis2@live.com     | 655-100-5085 |
     +---------+--------------------+--------------+
     
     ```

9. Listar las diferentes marcas de celular en orden alfabético descendentemente

     ```sql
     mysql> select distinct marca from tblUsuarios order by marca desc;
     +------------+
     | marca      |
     +------------+
     | SONY       |
     | SAMSUNG    |
     | NOKIA      |
     | MOTOROLA   |
     | LG         |
     | BLACKBERRY |
     +------------+
     
     ```

10. Listar las diferentes compañias en orden alfabético aleatorio

       ```sql
       mysql> select distinct compañia from tblUsuarios order by rand();
       +-----------+
       | compañia  |
       +-----------+
       | AT&T      |
       | MOVISTAR  |
       | UNEFON    |
       | TELCEL    |
       | IUSACELL  |
       | NEXTEL    |
       | AXEL      |
       +-----------+
       
       
       ```

11. Listar el login de los usuarios con nivel 0 o 2

        ```sql
        mysql> select usuario,email from tblUsuarios where nivel=0 or nivel=2;
        +---------+-----------------------+
        | usuario | email                 |
        +---------+-----------------------+
        | BRE2271 | brenda@live.com       |
        | LUI6115 | enrique@outlook.com   |
        | DAN2832 | daniel@outlook.com    |
        | JAQ5351 | jaqueline@outlook.com |
        | ROM6520 | roman@gmail.com       |
        | BLA9739 | blas@hotmail.com      |
        | RIC8283 | ricardo@hotmail.com   |
        | VAL6882 | valentina@live.com    |
        | JUA2337 | juan@outlook.com      |
        | LET4015 | leticia@yahoo.com     |
        | HUG5441 | hugo@live.com         |
        +---------+-----------------------+
        
        ```

12. Calcular el saldo promedio de los usuarios que tienen teléfono marca LG

      ```sql
      mysql>  select round(AVG(saldo)) as promedio from tblUsuarios where marca='LG';
      +----------+
      | promedio |
      +----------+
      |       50 |
      +----------+
      
      ```

------

### Bloque 3

##### Consultas

1. Listar el login de los usuarios con nivel 1 o 3

     ```sql
      mysql> select usuario,email from tblUsuarios where nivel=1 or nivel=3;
     +---------+---------------------+
     | usuario | email               |
     +---------+---------------------+
     | OSC4677 | oscar@gmail.com     |
     | JOS7086 | francisco@gmail.com |
     | LUI7072 | luis@hotmail.com    |
     | JES4752 | jessica@hotmail.com |
     | DIA6570 | diana@live.com      |
     | BRE8106 | brenda2@gmail.com   |
     | LUC4982 | lucia@gmail.com     |
     | ELP2984 | elpidio@outlook.com |
     | JES9640 | jessica2@live.com   |
     | LUI1076 | luis2@live.com      |
     +---------+---------------------+
     ```

2. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca BLACKBERRY

     ```sql
     mysql> select nombre,telefono from tblUsuarios where marca<>'BLACKBERRY';
     +---------+--------------+
     | nombre  | telefono     |
     +---------+--------------+
     | BRENDA  | 655-330-5736 |
     | OSCAR   | 655-143-4181 |
     | JOSE    | 655-143-3922 |
     | LUIS    | 655-137-1279 |
     | LUIS    | 655-100-8260 |
     | DANIEL  | 655-145-2586 |
     | ROMAN   | 655-330-3263 |
     | BLAS    | 655-330-3871 |
     | JESSICA | 655-143-6861 |
     | DIANA   | 655-143-3952 |
     | RICARDO | 655-145-6049 |
     | BRENDA  | 655-100-1351 |
     | JUAN    | 655-100-6517 |
     | ELPIDIO | 655-145-9938 |
     | JESSICA | 655-330-5143 |
     | LUIS    | 655-100-5085 |
     | HUGO    | 655-137-3935 |
     +---------+--------------+
     
     ```

3. Listar el login de los usuarios con nivel 3

     ```sql
      mysql> select usuario,email from tblUsuarios where nivel=3;
     +---------+---------------------+
     | usuario | email               |
     +---------+---------------------+
     | OSC4677 | oscar@gmail.com     |
     | JOS7086 | francisco@gmail.com |
     | BRE8106 | brenda2@gmail.com   |
     | LUC4982 | lucia@gmail.com     |
     | JES9640 | jessica2@live.com   |
     | LUI1076 | luis2@live.com      |
     +---------+---------------------+
     
     ```

4. Listar el login de los usuarios con nivel 0

     ```sql
     mysql> select usuario,email from tblUsuarios where nivel=0;
     +---------+-----------------------+
     | usuario | email                 |
     +---------+-----------------------+
     | LUI6115 | enrique@outlook.com   |
     | DAN2832 | daniel@outlook.com    |
     | JAQ5351 | jaqueline@outlook.com |
     | BLA9739 | blas@hotmail.com      |
     | VAL6882 | valentina@live.com    |
     | JUA2337 | juan@outlook.com      |
     +---------+-----------------------+
     
     ```

5. Listar el login de los usuarios con nivel 1

     ```sql
     mysql> select usuario,email from tblUsuarios where nivel=1;
     +---------+---------------------+
     | usuario | email               |
     +---------+---------------------+
     | LUI7072 | luis@hotmail.com    |
     | JES4752 | jessica@hotmail.com |
     | DIA6570 | diana@live.com      |
     | ELP2984 | elpidio@outlook.com |
     +---------+---------------------+
      
     ```

6. Contar el número de usuarios por sexo

     ```sql
      mysql> select sexo,count(usuario) as num_usuarios from tblUsuarios group by sexo;
     +------+--------------+
     | sexo | num_usuarios |
     +------+--------------+
     | M    |            9 |
     | H    |           12 |
     +------+--------------+
     
     ```

7. Listar el login y teléfono de los usuarios con compañia telefónica AT&T

     ```sql
      mysql> select usuario,email from tblUsuarios where compañia='AT&T';
     +---------+--------------------+
     | usuario | email              |
     +---------+--------------------+
     | VAL6882 | valentina@live.com |
     | HUG5441 | hugo@live.com      |
     +---------+--------------------+
     
     ```

8. Listar las diferentes compañias en orden alfabético descendentemente

     ```sql
      mysql> select distinct compañia from tblUsuarios order by compañia desc;
     +-----------+
     | compañia  |
     +-----------+
     | UNEFON    |
     | TELCEL    |
     | NEXTEL    |
     | MOVISTAR  |
     | IUSACELL  |
     | AXEL      |
     | AT&T      |
     +-----------+
     
     ```

9. Listar el logn de los usuarios inactivos

     ```sql
      mysql> select usuario,email from tblUsuarios where activo=0;
     +---------+--------------------+
     | usuario | email              |
     +---------+--------------------+
     | LUI7072 | luis@hotmail.com   |
     | DIA6570 | diana@live.com     |
     | VAL6882 | valentina@live.com |
     | JUA2337 | juan@outlook.com   |
     +---------+--------------------+
     
     ```

10. Listar los números de teléfono sin saldo

       ```sql
        mysql> select telefono from tblUsuarios where saldo=0;
       +--------------+
       | telefono     |
       +--------------+
       | 655-143-4181 |
       | 655-330-5514 |
       | 655-145-4992 |
       | 655-100-6517 |
       +--------------+
       
       ```

11. Calcular el saldo mínimo de los usuarios de sexo “Hombre”

        ```sql
        mysql> select min(saldo) as saldo_minimo from tblUsuarios where sexo='H';
        +--------------+
        | saldo_minimo |
        +--------------+
        |            0 |
        +--------------+
        
        ```

12. Listar los números de teléfono con saldo mayor a 300

      ```sql
      mysql> select telefono from tblUsuarios where saldo>300;
      +--------------+
      | telefono     |
      +--------------+
      | 655-143-6861 |
      | 655-145-9938 |
      | 655-137-3935 |
      +--------------+
      
      ```

------

### Bloque 4

##### Consultas

1. Contar el número de usuarios por marca de teléfono

     ```sql
     mysql> select marca,count(usuario) as cant_usuarios from tblUsuarios group by marca order by marca;
     +------------+---------------+
     | marca      | cant_usuarios |
     +------------+---------------+
     | BLACKBERRY |             4 |
     | LG         |             3 |
     | MOTOROLA   |             4 |
     | NOKIA      |             2 |
     | SAMSUNG    |             4 |
     | SONY       |             4 |
     +------------+---------------+
     
     ```

2. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca LG

     ```sql
     mysql> select nombre,telefono from tblUsuarios where marca<>'LG';
     +-----------+--------------+
     | nombre    | telefono     |
     +-----------+--------------+
     | BRENDA    | 655-330-5736 |
     | JOSE      | 655-143-3922 |
     | LUIS      | 655-137-1279 |
     | LUIS      | 655-100-8260 |
     | DANIEL    | 655-145-2586 |
     | JAQUELINE | 655-330-5514 |
     | JESSICA   | 655-143-6861 |
     | DIANA     | 655-143-3952 |
     | RICARDO   | 655-145-6049 |
     | VALENTINA | 655-137-4253 |
     | BRENDA    | 655-100-1351 |
     | LUCIA     | 655-145-4992 |
     | JUAN      | 655-100-6517 |
     | ELPIDIO   | 655-145-9938 |
     | JESSICA   | 655-330-5143 |
     | LETICIA   | 655-143-4019 |
     | LUIS      | 655-100-5085 |
     | HUGO      | 655-137-3935 |
     +-----------+--------------+
     
     ```

3. Listar las diferentes compañias en orden alfabético ascendentemente

     ```sql
     mysql> select distinct compañia from tblUsuarios order by compañia;
     +-----------+
     | compañia  |
     +-----------+
     | AT&T      |
     | AXEL      |
     | IUSACELL  |
     | MOVISTAR  |
     | NEXTEL    |
     | TELCEL    |
     | UNEFON    |
     +-----------+
     
     ```

4. Calcular la suma de los saldos de los usuarios de la compañia telefónica UNEFON

     ```sql
      mysql> select sum(saldo) as Total from tblUsuarios where compañia='UNEFON';
     +-------+
     | Total |
     +-------+
     |   550 |
     +-------+
     
     ```

5. Mostrar el email de los usuarios que usan hotmail

     ```sql
     mysql> select email from tblUsuarios WHERE email LIKE '%hotmail%';
     +---------------------+
     | email               |
     +---------------------+
     | luis@hotmail.com    |
     | blas@hotmail.com    |
     | jessica@hotmail.com |
     | ricardo@hotmail.com |
     +---------------------+
     
     ```

6. Listar los nombres de los usuarios sin saldo o inactivos

     ```sql
      # Solucion en 'sql'
     ```

7. Listar el login y teléfono de los usuarios con compañia telefónicaIUSACELL o TELCEL

     ```sql
      # Solucion en 'sql'
     ```

8. Listar las diferentes marcas de celular en orden alfabético ascendentemente

     ```sql
      # Solucion en 'sql'
     ```

9. Listar las diferentes marcas de celular en orden alfabético aleatorio

     ```sql
      # Solucion en 'sql'
     ```

10. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL o UNEFON

      ```sql
       # Solucion en 'sql'
      ```

11. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca MOTOROLA o NOKIA

      ```sql
       # Solucion en 'sql'
      ```

12. Calcular la suma de los saldos de los usuarios de la compañia telefónica TELCEL

      ```sql
       # Solucion en 'sql'
      ```
