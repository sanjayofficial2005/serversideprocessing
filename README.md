# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
clone the repository from the github.


### Step 2:
add math.html and result.html in templates.



### Step 3:

modify settings.py.

### Step 4:
define path in views.py and urls.py.



### Step 5:
run the url in the webserver


### Step 6:

Publish the website in the given URL.

## PROGRAM :
### math.html:
```html
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of prism</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body 
{
background-color:cyan;
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed lime;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color: purple;
}
.formelt{
color: Red;
text-align: center;
margin-top: 5px;
margin-bottom: 5px;
}
h1
{
color: yellow;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
    <div class="edge">
    <div class="box">
    <h1>Area of a Prism</h1>
    <form method="POST">
    {% csrf_token %}
    <div class="formelt">
    Side : <input type="text" name="side" value="{{s}}"></input>(in m)<br/>
    <div class="formelt">
    Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br/>
    </div>
    <div class="formelt">
    <input type="submit" value="Calculate"></input><br/>
    </div>
    <div class="formelt">
    Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
    </div>
    </form>
    </div>
    </div>
    </body>
    </html>
```

 ### views.py:
 ```python
 from django.shortcuts import render
from django.template  import loader
from django.shortcuts import render


# Create your views here.
def prismarea(request):
    context={}
    context['area'] = "0"
    context['s'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        s = request.POST.get('side','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('side=',s)
        print('height=',h)
        area = 2*int(s) * int(h)+4*int(s)*int(h)
        context['area'] = area
        context['s'] = s
        context['h'] = h
        print('Area=',area)
    return render(request,'myapp/math.html',context)
```

### urls.py:
```python
"""myproj URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from myapp import views


urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofprism/', views.prismarea, name="areaofprism"),
]

"""path('',views.prismarea,name="areaofprism)"""
```

## OUTPUT:
![server side processing](https://github.com/sanjayofficial2005/serversideprocessing/assets/148048602/4c4cc147-4a2c-4e65-81a7-3e40d03e6858)


### Home Page:


## Result:
This program executed succesfully.

