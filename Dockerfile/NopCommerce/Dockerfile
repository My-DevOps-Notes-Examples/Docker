FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL author="nagasuribabukola" purpose="practice" project="learning"
ARG user=nopcommerce
ARG group=nopcommerce
ARG uid=1000
ARG gid=1000
ARG Download_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.70.3/nopCommerce_4.70.3_NoSource_linux_x64.zip
ARG Home_Dir=/nop
RUN apt update && apt install unzip -y
RUN groupadd -g ${gid} ${group} \
    && useradd -d "$Home_Dir" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
USER ${user}
WORKDIR ${Home_Dir}
ADD --chown=${user}:${group} ${Download_URL} ${Home_Dir}/nopCommerce_4.70.3_NoSource_linux_x64.zip
RUN unzip ${Home_Dir}/nopCommerce_4.70.3_NoSource_linux_x64.zip && \
    mkdir ${Home_Dir}/bin && mkdir ${Home_Dir}/logs
EXPOSE 5000
ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
CMD [ "dotnet", "Nop.Web.dll" ]