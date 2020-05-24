FROM ubuntu:16.04

WORKDIR /mydir 

RUN apt-get update && apt-get install -y curl python

# Run youtube-dl
RUN curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
RUN chmod a+rx /usr/local/bin/youtube-dl

# Set the locale
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8 youtube-dl

ENTRYPOINT ["/usr/local/bin/youtube-dl"]