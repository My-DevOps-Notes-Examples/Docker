FROM ubuntu:22.04 AS extractor
ARG Download_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.70.3/nopCommerce_4.70.3_NoSource_linux_x64.zip
RUN apt update && apt install unzip
ADD ${Download_URL} /nopCommerce/nopcommerce.zip
RUN cd /nopCommerce && unzip nopcommerce.zip && mkdir bin && mkdir logs \
    && rm nopcommerce.zip

FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL author="suresh"   purpose="learning"
ARG Home_Dir=/nopcommerce
ARG user=nopcommerce
ARG group=nopcommerce
ARG uid=1000
ARG gid=1000
ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
RUN groupadd -g ${gid} ${group} \
    && useradd -d "$Home_Dir" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
USER ${user}
WORKDIR ${Home_Dir}
COPY --from=extractor --chown=${user}:${group} /nopCommerce ${Home_Dir}
EXPOSE 5000
CMD [ "dotnet", "Nop.Web.dll" ]