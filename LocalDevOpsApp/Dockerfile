FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Bulunduğum yerdeki csproj dosyasını kopyala
COPY *.csproj ./
RUN dotnet restore

# Bulunduğum yerdeki her şeyi kopyala
COPY . ./
RUN dotnet publish -c Release -o out

# Runtime aşaması
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out .
EXPOSE 8080
ENTRYPOINT ["dotnet", "LocalDevOpsApp.dll"]
