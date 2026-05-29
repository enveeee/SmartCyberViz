# Stage 1 — Build
FROM mcr.microsoft.com/dotnet/sdk:10.0-preview AS build
WORKDIR /src
COPY ["SmartCyberViz.csproj", "./"]
RUN dotnet restore "./SmartCyberViz.csproj"
COPY . .
RUN dotnet publish "SmartCyberViz.csproj" -c Release -o /app/publish

# Stage 2 — Runtime
FROM mcr.microsoft.com/dotnet/aspnet:10.0-preview AS final
WORKDIR /app
COPY --from=build /app/publish .
ENV ASPNETCORE_URLS=http://+:10000
EXPOSE 10000
ENTRYPOINT ["dotnet", "SmartCyberViz.dll"]