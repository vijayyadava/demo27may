FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY ["Demo27May/Demo27May.csproj", "Demo27May/"]
RUN dotnet restore "Demo27May/Demo27May.csproj"
COPY . .
WORKDIR "/src/Demo27May"
RUN dotnet build "Demo27May.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "Demo27May.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Demo27May.dll"]