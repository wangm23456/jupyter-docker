# step by step

1. build the Base
    ```shell
    cd Base
    docker build . -t "base-image"
    ```

2. build the Stack
    ```shell
    cd Stack
    docker build . -t "stack-image"
    ```

3. compose up the Jupyter
    ```shell
    cd Jupyter
    docker-compose -f "docker-compose.yml" up -d --build
    ```

note: in my case, I use the "namespace" to share the volume between host and container. 

# From jupyter/datascience-notebook

```shell
cd datasci
docker build . -t wangm/datasci-lab-base:v0.1
docker-compose -f "docker-compose.yml" up -d
```

note: in my case, I use the "namespace" to share the volume between host and container. 

reference: https://github.com/stefanproell/jupyter-notebook-docker-compose
