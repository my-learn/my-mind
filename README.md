## To learn Docker

- [关于dockerfile建立镜像异常](https://bbs.csdn.net/topics/391040030)

- [Dockerfile 中的 CMD 与 ENTRYPOINT](http://www.cnblogs.com/sparkdev/p/8461576.html)


## 构建镜像

### 使用 Dockerfile 定制镜像

- touch Dockerfile
- vim Dockerfile
  
  ```shell
    FROM nginx
    RUN echo '<h1>Hello, Docker!</h1>' > /usr/share/nginx/html/index.html
  ```
- docker build -t nginx:v3 .(注意空格和点是必要的)

### 其他方法构建

- Git 构建

    ```shell
    $ docker build https://github.com/twang2218/gitlab-ce-zh.git#:8.14
    docker build https://github.com/twang2218/gitlab-ce-zh.git\#:8.14
    Sending build context to Docker daemon 2.048 kB
    Step 1 : FROM gitlab/gitlab-ce:8.14.0-ce.0
    8.14.0-ce.0: Pulling from gitlab/gitlab-ce
    aed15891ba52: Already exists
    773ae8583d14: Already exists
    ...
    ```

    这行命令指定了构建所需的 Git repo，并且指定默认的 master 分支，构建目录为 /8.14/，然后 Docker 就会自己去 git clone 这个项目、切换到指定分支、并进入到指定目录后开始构建。

- 用给定的 tar 压缩包构建

  ```shell
    docker build http://server/context.tar.gz
  ```

- 从标准输入中读取 Dockerfile 进行构建

  ```shell
    docker build - < Dockerfile
  ```

  或

  ```shell
    cat Dockerfile | docker build -
  ```

- 从标准输入中读取上下文压缩包进行构建

  ```shell
    docker build - < context.tar.gz
  ```

- https://yeasy.gitbooks.io/docker_practice/content/image/build.html
  