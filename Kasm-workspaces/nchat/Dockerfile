FROM kasmweb/terminal:1.15.0

# Set the user to root
USER root

# Set Environment Variables
#ENV HOME=/home/kasm-default-profile
#ENV STARTUPDIR=/dockerstartup
#ENV INST_SCRIPTS=$STARTUPDIR/install

### Container Customisations ###

# Install dependencies for building the software
RUN apt-get update && apt-get install -y build-essential autoconf automake libtool pkg-config git wget

# Clone the Github repository
RUN git clone https://github.com/d99kris/nchat /opt/my-software

# Set the working directory
WORKDIR /opt/my-software


# Build and install the software
RUN DEBIAN_FRONTEND=noninteractive ./make.sh --yes deps && ./make.sh build && ./make.sh install

# Clean up build dependencies if not needed
# RUN apt-get remove -y build-essential autoconf automake libtool pkg-config git wget && apt-get autoremove -y && apt-get clean

### End Customisations ###

#RUN chown 1000:0 $HOME
#RUN $STARTUPDIR/set_user_permission.sh $HOME

#ENV HOME=/home/kasm-user
WORKDIR $HOME
RUN mkdir -p $HOME && chown -R 1000:0 $HOME

USER 1000

# Set the default command to open a terminal
#CMD ["bash"]

