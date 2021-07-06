FROM christroutner/ct-base-ubuntu
MAINTAINER Chris Troutner <chris.troutner@gmail.com>

RUN apt-get update -y

RUN apt-get install -y autoconf libtool

#Set the working directory to be the home directory
WORKDIR /home/safeuser

# Uninstall node v14 and replace with node v12
RUN apt-get -y remove nodejs
RUN curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN apt-get install -y nodejs build-essential

# Switch to user account.
USER safeuser
# Prep 'sudo' commands.
#RUN echo 'abcd8765' | sudo -S pwd

# Clone the Bitcore repository
WORKDIR /home/safeuser
RUN git clone https://github.com/christroutner/slpserve
# RUN git clone https://github.com/fountainhead-cash/slpserve
WORKDIR /home/safeuser/slpserve
RUN git checkout basic-auth
RUN npm install
COPY env .env

CMD ["npm", "start"]

# Used for debugging.
#COPY dummyapp.js dummyapp.js
#CMD ["node", "dummyapp.js"]
