# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<html>
<head>
    <title>Power of the lamp calculator</title>
    <style>
        body {
            font-size: 20px;
            background-color: #f9dede;
            color: rgb(23, 20, 20);
            font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
            text-align: center;
            padding-top: 40px;
        }

        h1 {
            color: #1c0aa5;font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
            margin-bottom: 20px;
        }

        .formelt {
            margin: 10px 0;
        }

        input[type="text"] {
            padding: 5px;
            font-size: 16px;
            width: 200px;
        }

        input[type="submit"] {
            padding: 8px 16px;
            font-size: 16px;
            background-color: #5df56f;
            color: #111;
            border: none;
            cursor: pointer;
        }

        input[type="submit"]:hover {
            background-color: #5cd1f4;
        }
    </style>
</head>
<body>
    <h1>POWER CALCULATOR</h1><br><br>
    <form method="POST">
        {% csrf_token %}
        <div class="formelt">
            Intensity (I): <input type="text" name="intensity" value="{{i}}"> (in amperes)<br/>
        </div>
        <div class="formelt">
            Resistance (R): <input type="text" name="resistance" value="{{r}}"> (in ohms)<br/>
        </div>
        <div class="formelt">
            <input type="submit" value="Calculate Power"><br/>
        </div>
        <div class="formelt">
            Power (P): <input type="text" name="power" value="{{p}}"> watts<br/>
        </div>
    </form>
</body>
</html>

views.html
##view.py:
from django.shortcuts import render

def lamp_power(request):
    context = {}
    context['p'] = "0"
    context['i'] = "0"
    context['r'] = "0"

    if request.method == 'POST':
        print("POST method is used")
        i = request.POST.get('intensity', '0')
        r = request.POST.get('resistance', '0')
        print("Intensity =", i)
        print("Resistance =", r)
        
        try:
            power = float(i) ** 2 * float(r)
        except ValueError:
            power = "Invalid input"

        context['p'] = power
        context['i'] = i
        context['r'] = r
        print("Power =", power)

    return render(request, 'mathapp/math.html', context)


urls.py
##urls.py:
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('lamp-power/', views.lamp_power, name="lamp_power"),
    path('', views.lamp_power, name="lamp_power_root")
]
```

## SERVER SIDE PROCESSING:

![Screenshot 2025-05-22 215432](https://github.com/user-attachments/assets/13935beb-246a-4122-8b33-c5d427c0ec3e)


## HOMEPAGE:

![Screenshot 2025-05-22 215502](https://github.com/user-attachments/assets/129de1e9-849c-4581-a31a-4d05c7ab8455)



## RESULT:
The program for performing server side processing is completed successfully.
