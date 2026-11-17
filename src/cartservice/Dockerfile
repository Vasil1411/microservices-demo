# Етап 1: Компилиране и пускане на .NET приложението
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /app
COPY . .
RUN dotnet restore cartservice.sln
RUN dotnet publish cartservice.sln -c Release -o /app/publish

# Етап 2: Финален лек образ за стартиране
FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 7070
ENTRYPOINT ["dotnet", "cartservice.dll"]