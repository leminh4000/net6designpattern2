FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["c03SingleResp01/c03SingleResp01.csproj", "c03SingleResp01/"]
RUN dotnet restore "c03SingleResp01/c03SingleResp01.csproj"
COPY . .
WORKDIR "/src/c03SingleResp01"
RUN dotnet build "c03SingleResp01.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "c03SingleResp01.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "c03SingleResp01.dll"]
