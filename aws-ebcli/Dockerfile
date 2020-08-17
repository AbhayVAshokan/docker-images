FROM ubuntu

RUN sed -i'' 's/archive\.ubuntu\.com/us\.archive\.ubuntu\.com/' /etc/apt/sources.list
RUN apt-get -y update 
RUN apt-get -y install apt-utils
RUN apt-get -y install build-essential
RUN apt-get -y install zlib1g-dev
RUN apt-get -y install libssl-dev 
RUN apt-get -y install libncurses-dev
RUN apt-get -y install libffi-dev 
RUN apt-get -y install libsqlite3-dev 
RUN apt-get -y install libreadline-dev 
RUN apt-get -y install libbz2-dev 
RUN apt-get -y install git
RUN apt-get -y install curl

RUN mkdir setup
RUN cd setup

RUN git clone https://github.com/aws/aws-elastic-beanstalk-cli-setup.git
RUN ./aws-elastic-beanstalk-cli-setup/scripts/bundled_installer

RUN printf "\
\#!/bin/bash\n\
CONTAINER_ALREADY_STARTED=\".export_path\"\n\
if [ ! -e \$CONTAINER_ALREADY_STARTED ]; then \n\
    touch \$CONTAINER_ALREADY_STARTED\n\
    echo \'export PATH=\"/root/.ebcli-virtual-env/executables:\$PATH\"\' >> ~/.bash_profile && source ~/.bash_profile\n\
    echo \'export PATH=/root/.pyenv/versions/3.7.2/bin:\$PATH\' >> /root/.bash_profile && source /root/.bash_profile\n\
fi\n" >> startup_script.bash

RUN apt-get install python3-pip -y
RUN pip3 install awsebcli

CMD [ "chmod 664 ./startup_script.bash && bash startup_script.bash" ]
ENTRYPOINT [ "bash" ]