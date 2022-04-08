# opentelemetry-cpp development environment

## Prepare

### Install deps
```
git clone https://github.com/google/googletest.git -b release-1.11.0
mkdir -p googletest/build
cd googletest/build
cmake ..
make
sudo make install

git clone https://github.com/google/benchmark.git
mkdir -p benchmark/build
cd benchmark/build
cmake -DBENCHMARK_DOWNLOAD_DEPENDENCIES=on -DCMAKE_BUILD_TYPE=Release ..
make
sudo make install

sudo apt install libcurl4-openssl-dev
# gives curl version 7.68.0
sudo apt install libthrift-dev
# which gives 0.13.0 (alt. https://thrift.apache.org/lib/cpp.html)
```

### Prepare install directory
```
mkdir /tmp/install
```

### Build opentelemetry-cpp
```
git clone --recursive git@github.com:Nordix/opentelemetry-cpp.git -b v1.1.0
mkdir opentelemetry-cpp/build && cd opentelemetry-cpp/build
cmake -DWITH_JAEGER=ON -DCMAKE_INSTALL_PREFIX=/tmp/install/ ..
make -j8
make install
```
