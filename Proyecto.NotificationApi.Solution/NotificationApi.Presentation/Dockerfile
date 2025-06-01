# Etapa de build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copiar los archivos del proyecto
COPY Proyecto.NotificationApi.Solution/NotificationApi.Presentation/NotificationApi.Presentation.csproj NotificationApi.Presentation/
COPY Proyecto.NotificationApi.Solution/NotificationApi.Application/NotificationApi.Application.csproj NotificationApi.Application/
COPY Proyecto.NotificationApi.Solution/NotificationApi.Domain/NotificationApi.Domain.csproj NotificationApi.Domain/
COPY Proyecto.NotificationApi.Solution/NotificationApi.Infrastructure/NotificationApi.Infrastructure.csproj NotificationApi.Infrastructure/
COPY Proyecto.SharedLibrarySolution/Proyecto.SharedLibrary/Proyecto.SharedLibrary.csproj Proyecto.SharedLibrary/

# Restaurar dependencias
RUN dotnet restore NotificationApi.Presentation/NotificationApi.Presentation.csproj

# Copiar el código fuente completo
COPY Proyecto.NotificationApi.Solution/ NotificationApi.Solution/
COPY Proyecto.SharedLibrarySolution/ Proyecto.SharedLibrarySolution/

# Cambiar al directorio del proyecto principal
WORKDIR /src/NotificationApi.Solution/NotificationApi.Presentation

# Publicar la aplicación
RUN dotnet publish NotificationApi.Presentation.csproj -c Release -o /app/publish

# Etapa de runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .

# Entrypoint para la API
ENTRYPOINT ["dotnet", "NotificationApi.Presentation.dll"]
