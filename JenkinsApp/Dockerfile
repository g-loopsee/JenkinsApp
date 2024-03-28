FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /JenkinsApp

# Копировать все файлы проекта
COPY . ./
# Восстановить зависимости
RUN dotnet restore
# Собрать и опубликовать релизную версию
RUN dotnet build --configuration Release

# Собрать образ среды выполнения
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /JenkinsApp
# Копировать собранные артефакты из папки сборки проекта
COPY --from=build-env /JenkinsApp/bin/Release ./app