**# Django_REST_API_Tutorial**

**Step 1: Set Up Django Project and App**
Open a terminal in the directory where you want to create your project.

Run the following commands:


_django-admin startproject myproject
cd myproject
python manage.py startapp myapp_

**Step 2: Define Model**
In myapp/models.py, define your model. For example:


_# myapp/models.py
from django.db import models

class Item(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()

    def __str__(self):
        return self.name_
Run migrations:

_python manage.py makemigrations
python manage.py migrate_

**Step 3: Create Serializers**
In myapp/serializers.py, create serializers for your models:


# myapp/serializers.py
__from rest_framework import serializers
from .models import Item

class ItemSerializer(serializers.ModelSerializer):
    class Meta:
        model = Item
        fields = '__all__'__
        
**Step 4: Create Views**

In myapp/views.py, create views using Django REST framework:


_# myapp/views.py
from rest_framework import generics
from .models import Item
from .serializers import ItemSerializer

class ItemListCreateView(generics.ListCreateAPIView):
    queryset = Item.objects.all()
    serializer_class = ItemSerializer_
**Step 5: URL Configuration**
In myapp/urls.py, define URL patterns for your API:


# myapp/urls.py
_from django.urls import path
from .views import ItemListCreateView

urlpatterns = [
    path('items/', ItemListCreateView.as_view(), name='item-list-create'),
]_
Include this URL configuration in the main project's urls.py:


# myproject/urls.py
_from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('myapp.urls')),
]_
**Step 6: Serve the API**
Run the development server:

_
python manage.py runserver_
Visit http://127.0.0.1:8000/api/items/ in your browser to see the API endpoint.
All earlier stored DATA
![image](https://github.com/mdshamsfiroz/Django_REST_API_Tutorial/assets/76830065/331f40ef-dbb2-4bb1-b6fe-9f6d2c8248de)
![image](https://github.com/mdshamsfiroz/Django_REST_API_Tutorial/assets/76830065/6cddd89a-32a3-4393-abef-03337dbb87bb)

Adding New Data
![image](https://github.com/mdshamsfiroz/Django_REST_API_Tutorial/assets/76830065/74c883db-4eed-41c4-a245-624ace4324a1)
Updated json file
![image](https://github.com/mdshamsfiroz/Django_REST_API_Tutorial/assets/76830065/3be3c44f-e81b-4353-b443-4dc258edf76f)



