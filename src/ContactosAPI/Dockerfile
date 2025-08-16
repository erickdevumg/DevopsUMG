FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build 
WORKDIR /src
COPY ContactosAPI.csproj .
RUN dotnet restore
COPY . .

RUN dotnet build "ContactosAPI.csproj" -c Release -o /app/build

RUN dotnet publish -c release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "ContactosAPI.dll"]