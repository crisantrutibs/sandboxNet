# Stage 1
FROM mcr.microsoft.com/dotnet/sdk:5.0.302 AS build-env
WORKDIR /src
COPY  TodoApi.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /app

# Stage 2
FROM mcr.microsoft.com/dotnet/aspnet:5.0.8 
WORKDIR /app
COPY --from=build-env /app .
ENTRYPOINT ["dotnet", "TodoApi.dll"]