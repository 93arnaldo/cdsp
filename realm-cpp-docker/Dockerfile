# Use a base image with C++ support, ubuntu:latest
FROM ubuntu:latest

# Install necessary tools and libraries
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    build-essential \
    libcurl4-openssl-dev \
    libuv1-dev \
    libprocps-dev\
    libssl-dev\
    zlib1g-dev\
    cmake \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Clone and build the Realm SDK
RUN git clone https://github.com/realm/realm-cpp.git \
    && cd realm-cpp \
    && git checkout v1.0.0 \
    && git submodule update --init --recursive \
    && mkdir build.release \
    && cd build.release \
    && cmake -DREALM_CPP_NO_TESTS=1 .. \ 
    && cmake --build . --target install \
    && cd .. \ # back to root dir

COPY . .

# Set the working directory
WORKDIR /realm-playground

RUN mkdir build.release \
    && cd build.release \
    && cmake .. \ 
    && cmake --build . \
    && mv realm_cpp_app ../ 

# Command to build your project
CMD ["./realm_cpp_app"]

