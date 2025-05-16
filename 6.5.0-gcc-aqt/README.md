`docker build -t $(cat VERSION) .`

Here is an example command to build your QT project from the directory just above it.

```
mkdir build
docker run -it --rm -v "./MyProject:/home/user/MyProject:ro" -v "./build:/home/user/build:rw" \
    ravenshub/qt-docker:6.5.0-gcc-aqt-0.1.0 \
    sh -c 'qt-cmake ./MyProject -G Ninja -B ./build && cmake --build ./build;
           linuxdeploy --plugin qt -e "$(find ./build -maxdepth 1 -type f -executable)" --appdir ./build/deploy'
```
