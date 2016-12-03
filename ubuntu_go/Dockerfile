FROM codenvy/ubuntu_jre
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
    g++ \
    gcc \
    libc6-dev \
    make \
    && sudo rm -rf /var/lib/apt/lists/*

ENV GOLANG_VERSION 1.7.4
ENV GOLANG_DOWNLOAD_URL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz
ENV GOLANG_DOWNLOAD_SHA256 47fda42e46b4c3ec93fa5d4d4cc6a748aa3f9411a2a2b7e08e3a6d80d753ec8b

RUN sudo curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz \
    && echo "$GOLANG_DOWNLOAD_SHA256  golang.tar.gz" | sha256sum -c - \
    && sudo tar -C /usr/local -xzf golang.tar.gz \
    && sudo rm golang.tar.gz

RUN sudo sed -i '$ d' /home/user/.bashrc
ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN sudo mkdir -p "$GOPATH/src" "$GOPATH/bin" && sudo chmod -R 777 "$GOPATH"

EXPOSE 8080

CMD tail -f /dev/null
