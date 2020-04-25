# django-app-with-debug-off
##### To disable DEBUG on your django app and still serve your static files:  
###### **1. Open `urls.py` and paste in the following code at the end of the file**  
```python
from django.urls import re_path
from django.views.static import serve
from main import settings   # here main is your default folder
if not settings.DEBUG:
    urlpatterns += [
        re_path(r'^static/(?P<path>.*)$', serve, {'document_root': settings.STATIC_ROOT})
    ]
```    

###### **2. Open `settings.py` and paste in the following code at the end of the file**  
```python
if DEBUG:    
    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, "main", "assets")
    ]
else:
    STATIC_ROOT = os.path.join(BASE_DIR, 'main', 'assets')
```
#### And That\'s it You\'re  done!

##### Design by **[BlackrockDigital](https://github.com/BlackrockDigital/startbootstrap-creative "BlackrockDigital")**  
