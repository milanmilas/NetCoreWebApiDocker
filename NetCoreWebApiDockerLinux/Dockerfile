#FROM microsoft/aspnetcore:2.0 AS base
#WORKDIR /app
#EXPOSE 80
#
#FROM microsoft/aspnetcore-build:2.0 AS build
#WORKDIR /src
#COPY NetCoreWebApiDocker.sln ./
#COPY NetCoreWebApiDockerLinux/NetCoreWebApiDockerLinux.csproj NetCoreWebApiDockerLinux/
#RUN dotnet restore -nowarn:msb3202,nu1503
#COPY . .
#WORKDIR /src/NetCoreWebApiDockerLinux
#RUN dotnet build -c Release -o /app
#
#FROM build AS publish
#RUN dotnet publish -c Release -o /app
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app .
#ENTRYPOINT ["dotnet", "NetCoreWebApiDockerLinux.dll"]


FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY NetCoreWebApiDocker.sln ./
COPY NetCoreWebApiDockerLinux/NetCoreWebApiDockerLinux.csproj NetCoreWebApiDockerLinux/
RUN dotnet restore -nowarn:msb3202,nu1503
COPY . .
WORKDIR /src/NetCoreWebApiDockerLinux
RUN dotnet build -c Release -o /app

FROM build AS publish
RUN dotnet publish -c Release -o /app

FROM microsoft/dotnet:2.0.0-runtime-stretch-arm32v7
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "NetCoreWebApiDockerLinux.dll"]