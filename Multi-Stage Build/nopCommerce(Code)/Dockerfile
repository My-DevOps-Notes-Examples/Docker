    FROM alpine/git AS code
    RUN cd / && git clone https://github.com/nopSolutions/nopCommerce.git

    FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder
    COPY --from=code /nopCommerce /nopcommerce
    WORKDIR /nopcommerce
    RUN dotnet restore src/Presentation/Nop.Web/Nop.Web.csproj && \
        dotnet nuget locals all --clear
    # RUN dotnet test src/Tests/Nop.Tests/Nop.Tests.csproj
    RUN dotnet publish src/Presentation/Nop.Web/Nop.Web.csproj -c Release -o /app/publish

    FROM mcr.microsoft.com/dotnet/aspnet:8.0
    WORKDIR /app
    COPY --from=builder /app/publish .
    EXPOSE 5000
    ENTRYPOINT ["dotnet", "Nop.Web.dll", "--urls", "http://0.0.0.0:5000"]