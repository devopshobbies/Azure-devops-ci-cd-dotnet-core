FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /source 
COPY *.sln .
COPY SampleWebApiAspNetCore/*.csproj ./SampleWebApiAspNetCore/
RUN dotnet restore
COPY SampleWebApiAspNetCore ./SampleWebApiAspNetCore
RUN dotnet test
RUN dotnet publish -c release -o /app --no-restore

# Final image 
FROM mcr.microsoft.com/dotnet/aspnet:7.0 
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT [ "dotnet", "SampleWebApiAspNetCore.dll" ]



