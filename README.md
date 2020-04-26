# celery_redis_flask

La idea viene de aca: 
https://stackabuse.com/asynchronous-tasks-using-flask-redis-and-celery/  
https://github.com/ro6ley/flask-celery-demo

#### crear environment con `conda create --name my_env`
#### requirements con `pip install -r requirements.txt`

<aside class="notice">
Habilitar la cuenta de gmail para que puedan acceder aplicaciones terceras
</aside>

<aside class="warning">
En el original:
Hay un error en la linea 14 de app.py que se tiene que arreglar, comentandola.
*Make shure to remove celery.conf.update(app.config) in the function make_celery(app). 
The error won't be displayed anymore.*
</aside>


<aside class="warning">
index.html original tambien tenia un error. Cambiado por:
      <option value="minutes">Minutes</option>
      <option value="hours">Hours</option>
      <option value="days">Days</option>
</aside>


### Para ejecutar la app:

1. en el env, ejecutar la app `python app.py`
2. en el env, ejecutary celery `celery -A app.client worker --pool=solo -l info`
En el ejemplo usa `celery worker -A app.client --loglevel=info` pero en Windows no está funcionando bien eso
3. en el env, ejecutar flower para monitorear las tareas `flower -A app.client --port=5555`
