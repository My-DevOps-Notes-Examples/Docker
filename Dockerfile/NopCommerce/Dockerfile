FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL author="nagasuribabukola" purpose="practice" project="learning"
ARG Download_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.70.3/nopCommerce_4.70.3_NoSource_linux_x64.zip
ARG Home_Dir=/nop
ADD ${Download_URL} ${Home_Dir}/nopCommerce_4.70.3_NoSource_linux_x64.zip
WORKDIR ${Home_Dir}
RUN apt update && apt install unzip -y && \
    unzip ${Home_Dir}/nopCommerce_4.70.3_NoSource_linux_x64.zip && \
    mkdir ${Home_Dir}/bin && mkdir ${Home_Dir}/logs
EXPOSE 5000
ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
CMD [ "dotnet", "Nop.Web.dll" ]