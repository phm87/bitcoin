FROM ubuntu:18.04
RUN apt-get update && apt-get install -y curl

RUN mkdir -p /root/.gincoincore && \
    echo "rpcallowip=127.0.0.1" >> /root/.gincoincore/gincoin.conf && \
    echo "rpcuser=user123" >> /root/.gincoincore/gincoin.conf && \
    echo "rpcpassword=password123" >> /root/.gincoincore/gincoin.conf

RUN curl -L https://github.com/GIN-coin/gincoin-core/releases/download/v1.3.0.0/gincoin-binaries-1.3.0-linux-64bit.tar.gz > bin.tar.gz && \
    echo "64f2eaa39189bac1eb46de5fd98bf0ed4609dbeb36d2eabcb3c200f72d722860  bin.tar.gz" > CHECK && \
    sha256sum -c CHECK && \
    tar -zxvf bin.tar.gz && \
    mv gincoin-binaries/* /usr/local/bin/ && \
    rm -rf gincoin-binaries bin.tar.gz

ENTRYPOINT ["gincoind"]
