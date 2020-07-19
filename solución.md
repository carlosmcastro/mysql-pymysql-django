# Solución problema **MySQL-pymysql-Django2**

Instalamos el modulo de **pymysql**:
```Batchfile
pip install pymysql
```
En **manage.py**, introducimos estas lineas al inicio, antes de cualquier parametro **Django**.
```python
import pymysql
pymysql.install_as_MySQLdb()
```
En la **versión 2** de **Django** posiblemente fallé, a la hora de ejecutar migraciones.
Así que vamos a la ruta:
```Batchfile
cd "env\Lib\site-packages\django\db\backends\mysql"
```
Editamos el archivo **operations.py**
Buscamos la linea:

```python
            query = query.decode(errors='replace')
```
Recordamos que la indentación utilizada es de **4 espacios** en lugar de **TAB**.
y reemplazamos por:
```python
            if not type(query) is str:
                query = query.decode(errors='replace')
```
Con esto ya debería permitirnos las migraciones:
```Batchfile
python -m manage migrate
```


## Más info
 - https://stackoverflow.com/questions/34777755/how-to-config-django-using-pymysql-as-driver
 - https://adamj.eu/tech/2020/02/04/how-to-use-pymysql-with-django/
 - https://medium.com/@a01207543/django-conecta-tu-proyecto-con-la-base-de-datos-mysql-2d329c73192a
 - https://stackoverflow.com/questions/56820895/migrations-error-in-django-2-attributeerror-str-object-has-no-attribute-dec
  
