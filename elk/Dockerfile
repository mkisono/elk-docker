FROM sebp/elk:742
# FROM sebp/elk:770

RUN apt update && apt install unzip

ENV ES_HOME /opt/elasticsearch
WORKDIR ${ES_HOME}

RUN curl -LO https://github.com/WorksApplications/elasticsearch-sudachi/releases/download/v7.4.2-1.3.2/analysis-sudachi-elasticsearch7.4-1.3.2.zip
# RUN curl -O https://github.com/WorksApplications/elasticsearch-sudachi/releases/download/v7.7.0-2.0.1/analysis-sudachi-elasticsearch7.7-2.0.1.zip

RUN yes | CONF_DIR=/etc/elasticsearch gosu elasticsearch bin/elasticsearch-plugin install file:///opt/elasticsearch/analysis-sudachi-elasticsearch7.4-1.3.2.zip
# RUN yes | CONF_DIR=/etc/elasticsearch gosu elasticsearch bin/elasticsearch-plugin install file:///opt/elasticsearch/analysis-sudachi-elasticsearch7.7-2.0.1.zip

RUN curl -O https://object-storage.tyo2.conoha.io/v1/nc_2520839e1f9641b08211a5c85243124a/sudachi/sudachi-dictionary-20200330-full.zip
RUN unzip sudachi-dictionary-20200330-full.zip
RUN mkdir /etc/elasticsearch/sudachi_tokenizer && mv ./sudachi-dictionary-20200330/system_full.dic /etc/elasticsearch/sudachi_tokenizer/system_core.dic
