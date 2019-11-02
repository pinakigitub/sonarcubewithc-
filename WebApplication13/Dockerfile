FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app


FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY *.csproj ./
RUN dotnet restore "WebApplication13.csproj"


COPY . .
RUN dotnet build "WebApplication13.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication13.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication13.dll"]
