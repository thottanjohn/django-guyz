from django.shortcuts import render,redirect
from django.http import HttpResponse
from django.contrib.auth import authenticate,login
from django.contrib.auth.models import User

# Create your views here.
def hello_world(request):
	names=['joy','ray','ram']
	data={"names":names}
	return render(request,"a.html",data)
def log(request):
	data = {}
	if request.method=="POST":
		username=request.POST.get("usr")
		password=request.POST.get("pass")
		user = authenticate(username=username, password=password)
		if user is not None:
			login(request,user)
			return render(request,"c.html",data)
		else:
			return render(request,"login.html",{"message:Such a user does ot exist"})
	else:
		return render(request,"login.html",data)
def signup(request):
	if request.method=="POST":
		username=request.POST.get("usr")
		password=request.POST.get("pass")
		cpassword=request.POST.get("cpass")
		if password!=cpassword:
			return render(request,"signup1.html",{"message":"Passwords do no match"})
		else:	
			user = User.objects.create_user(username=username,password=password)
			return redirect("/lg")
	else:
		data={}
		return render(request,"signup1.html",data)
	
