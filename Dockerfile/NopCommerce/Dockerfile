FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL author="nagasuribabukola" purpose="practice" project="learning"
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.70.3/nopCommerce_4.70.3_NoSource_linux_x64.zip /nop/nopCommerce_4.70.3_NoSource_linux_x64.zip
WORKDIR /nop
RUN apt update && apt install unzip -y && \
    unzip /nop/nopCommerce_4.70.3_NoSource_linux_x64.zip && \
    mkdir /nop/bin && mkdir /nop/logs
EXPOSE 5000
CMD [ "dotnet", "Nop.Web.dll", "--urls", "http://0.0.0.0:5000" ]