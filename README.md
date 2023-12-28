# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:

Fork the repository and clone it into vs code



### Step 2:

Now activate django and create a new django project called 'myproj'

### Step 3:

After that create a app called myapp using the command "python manage.py startapp myapp"

### Step 4:

Now create a folder called template in myproj, Now within this folder create an another folder called myapp

### Step 5:

Now within this folder create two html files called math.html and result.html

### Step 6:

Now make the necesssary changes in settings.py and views.py and urls.py
### Step 7:
Now run the server

## PROGRAM :

### Code for math.html

```<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Square Prism</title>
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
<h1>Area of a Square Prism</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Side A : <input type="text" name="side" value="{{s}}"></input>(in m)<br/>
</div>
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
### Code fo result.html

```
<!DOCTYPE html>
<html>
    <head>
        <title>SEC demo on server processing result</title>
    </head>
    <body>
        The result is {{result}}
    </body>
</html>

```
### Code for views.py

```from django.shortcuts import render
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
        area = 2*int(s)*int(s) + 4*int(s)*int(h)
        context['area'] = area
        context['s'] = s
        context['h'] = h
        print('Area=',area)
    return render(request,'myapp/math.html',context)
```
### Code for urls.py

```"""myproj URL Configuration

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
    path('areaofprism/',views.prismarea,name="areaofprism"),

]
```


## OUTPUT:
## CLIENT OUTPUT
<img width="610" alt="image" src="https://github.com/MOHAMEDRIDWAN/serversideprocessing/assets/146993368/fe9a2ad9-5fe3-4170-9d30-ca7b7e11b862">

## SERVER OUTPUT
<img width="611" alt="image" src="https://github.com/MOHAMEDRIDWAN/serversideprocessing/assets/146993368/e328b5df-4990-4057-b905-e0d795d0c16a">

### Home Page:
<img width="680" alt="image" src="https://github.com/MOHAMEDRIDWAN/serversideprocessing/assets/146993368/76286e0e-ea7d-418c-aba3-6b94e7193e7c">



## Result:
The website with server side response has been created succesfully
