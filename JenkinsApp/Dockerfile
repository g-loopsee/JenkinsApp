FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /JenkinsApp

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet build --configuration Release

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /JenkinsApp
COPY --from=build-env /JenkinsApp/out .