# Building .net service and running it inside a container

We are going to use .NetCore which is supported on Linux. There are 2 ways to create a core project easily 

## Using Yeoman

You don`t need yo use Visual Studio instead you can use Yeoman genetaror and Visual Studio code, please check netcore documentation [Yeoman + Core Tutorial](https://docs.asp.net/en/latest/client-side/yeoman.html)

A small resume from the last link is:
* Install node
* Execute -> npm install -g generator-aspnet
* Execute -> yo aspnet
* Select the type o project and the name, the project folder is going to be located in your actual folder
* Go to the project folder and execute "dotnet restore" "dotnet build" "dotnet run"
* Now your project is running locally on a server called kestrel.

## Using Visual Studio 

Core is being changed frecuently, so you need to update your Visual Studio to the last version, this time we`re going to use Visual Studio 2015 update 3 last update.


## Package project inside a docker image

If you used Yeoman to create the project, you can find inside the project`s folder a Dockerfile ready to be used like this one 

´´´sh
FROM microsoft/dotnet:latest

COPY . /app

WORKDIR /app

RUN ["dotnet", "restore"]

RUN ["dotnet", "build"]

EXPOSE 5000/tcp

ENTRYPOINT ["dotnet", "run", "--server.urls", "http://0.0.0.0:5000"]

´´´
As you can see, we´re going to use and official image for netcore and we`re going to expose kestrel on port 5000. Now what we have to do is to build the image an Run the container.

docker build -t mynetcoreapp .
docker run -d -p 8181:5000 mynetcoreapp

Now we can test on http://localhost:8181 or http://<docker-machine-ip>:8181

 





