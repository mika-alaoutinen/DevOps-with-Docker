FROM ubuntu:16.04

WORKDIR /mydir 

RUN apt-get update && apt-get install -y curl
COPY curl.sh .
RUN chmod +x curl.sh

CMD ["./curl.sh"]