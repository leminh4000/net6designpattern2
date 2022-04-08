FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["net6designpattern1/net6designpattern1.csproj", "net6designpattern1/"]
RUN dotnet restore "net6designpattern1/net6designpattern1.csproj"
COPY . .
WORKDIR "/src/net6designpattern1"
RUN dotnet build "net6designpattern1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "net6designpattern1.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "net6designpattern1.dll"]
