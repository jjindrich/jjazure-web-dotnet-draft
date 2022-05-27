FROM mcr.microsoft.com/dotnet/aspnet:6.0-focal AS base
WORKDIR /app
EXPOSE 80

ENV ASPNETCORE_URLS=http://+:80

FROM mcr.microsoft.com/dotnet/sdk:6.0-focal AS build
WORKDIR /src
COPY ["jjweb.csproj", "./"]
RUN dotnet restore "jjweb.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "jjweb.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "jjweb.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "jjweb.dll"]