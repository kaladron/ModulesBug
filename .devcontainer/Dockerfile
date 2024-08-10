FROM ubuntu:latest  # Use the latest official Ubuntu image

# Update the system and install necessary dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        wget \
        gnupg \
        software-properties-common

# Add Kitware's repository and install CMake
RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null && \
    apt-add-repository 'deb https://apt.kitware.com/ubuntu/   
 $(lsb_release -cs) main' && \
    apt-get update && \
    apt-get install -y --no-install-recommends cmake   

# Add LLVM repository and install clang-20
RUN curl https://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add - && \
    add-apt-repository "deb http://apt.llvm.org/$(lsb_release -cs)/ llvm-toolchain-$(lsb_release -cs)-20   
 main" && \
    apt-get update && \
    apt-get install -y clang-20 libc++-20-dev lld-20 lldb-20 clang-tools-20

