FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["c03SingleResp02/c03SingleResp02.csproj", "c03SingleResp02/"]
RUN dotnet restore "c03SingleResp02/c03SingleResp02.csproj"
COPY . .
WORKDIR "/src/c03SingleResp02"
RUN dotnet build "c03SingleResp02.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "c03SingleResp02.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "c03SingleResp02.dll"]
