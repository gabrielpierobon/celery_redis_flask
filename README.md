# celery_redis_flask

Esta es una webapp para demostrar las capacidades de desarrollar tareas asíncronas con **Celery** como gestor de tareas, **Redis** como *message broker* y **flower** como interfase para monitorear las tareas.

*La app permite programar el envío de emails a diferentes cuentas*

El código se desarrlla en lenguaje **Python**, utilizando el framework **Flask**

No se encuentra *dockerizado*


La idea viene de aca:  
https://stackabuse.com/asynchronous-tasks-using-flask-redis-and-celery/  
https://github.com/ro6ley/flask-celery-demo

#### crear environment con `conda create --name my_env`
#### requirements con `pip install -r requirements.txt`

**Warning_1:**
Habilitar la cuenta de gmail para que puedan acceder aplicaciones terceras

**Warning_2:**
En el original:
Hay un error en la linea 14 de app.py que se tiene que arreglar, comentandola.
*Make shure to remove celery.conf.update(app.config) in the function make_celery(app). 
The error won't be displayed anymore.*
</aside>

**Warning_3:**
index.html original tambien tenia un error. Cambiado por:
      <option value="minutes">Minutes</option>
      <option value="hours">Hours</option>
      <option value="days">Days</option>



### Para ejecutar la app:

1. **Flask** service: en el env, ejecutar la app `python app.py`
2. **Celery** service: en el env, ejecutary celery `celery -A app.client worker --pool=solo -l info`
En el ejemplo usa `celery worker -A app.client --loglevel=info` pero en Windows no está funcionando bien eso
3. **Flower** service: en el env, ejecutar flower para monitorear las tareas `flower -A app.client --port=5555`
