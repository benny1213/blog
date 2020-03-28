exit# GitHub WorkFlow

## 公钥私钥，服务器和GitHub的连接

  - ### 创建公钥私钥

    生成rsa密钥对
    ```bash
      ssh-keygen -t rsa
    ```

    生成的id_rsa 和id_rsa.pub 会生成在当前的用户目录下的`~/.ssh/`文件中

  - ### 密钥权限

    当生成的私钥权限过于开放(777)时，使用该私钥连接服务器会导致`bad permisions`问题

    solution: 
    ```bash
      sudo chmod 700 ~/.ssh/id_rsa 
      #修改文件，权限即除了用户本人，其他人无法读取写入执行该文件
    ```
    Todo: Linux的权限

  - ### 在GitHub上或者服务器上配置`id_rsa.pub`公钥

    略

  - ### 配置ssh config 以访问多个服务器(服务器别名)

    ```
      Host github.com www.github.com
        IdentityFile ~/.ssh/id_rsa_github

      Host server
        HostName 202.182.119.97
        User root
        Port 22
        IdentityFile ~/.ssh/id_rsa
    ```
    如上述，在`~/.ssh/config`中配置了两个服务器的ssh别名
    GitHub服务器使用的是私钥连接(可以使用不同名字的私钥而不必覆盖原私钥)
    
    配置完成之后使用`ssh server`就可以不用输入服务器ip连接服务器

    - 检测GitHub连接:
      ```
        ssh -vT git@github.com
      ```
      如果显示了本人的用户名则证明私钥配置成功
  

## 使用ssh连接服务器部署
  
  - ### github workflow 示例
  
    ```yml
      name: Greet Everyone
      # This workflow is triggered on pushes to the repository.
      on: [push]

      jobs:
        build:
          # 作业名称为 Greeting
          name: Greeting
          # 此作业在 Linux 上运行
          runs-on: ubuntu-latest
          steps:
            # 此步骤使用 GitHub 的 hello-world-javascript-action：https://github.com/actions/hello-world-javascript-action
            - name: Hello world
              uses: actions/hello-world-javascript-action@v1
              with:
                who-to-greet: 'Mona the Octocat'
              id: hello
            # 此步骤打印上一步操作的输出（时间）。
            - name: Echo the greeting's time
              run: echo 'The time was ${{ steps.hello.outputs.time }}.'
    ```

  - ### workflow 变量
    
    在`jobs.<job_id>.steps.env`、`jobx.<job_id>.env`或者`env`关键字来设置环境变量如

    ```yml
      steps:
        - name: Hello world
          env:
            FIRST_NAME: Mona
            middle_name: The
            Last_Name: Octocat
          run: echo Hello world $FIRST_NAME $middle_name $Last_Name!
    ```
    [常用的环境变量](https://help.github.com/cn/actions/automating-your-workflow-with-github-actions/using-environment-variables#default-environment-variables):
    
    变量名|简介
    ---|---
    `$HOME`|用于存储用户数据的 GitHub 主目录路径。 例如 /github/home
    `$GITHUB_WORKSPACE`|GitHub 工作空间目录路径。 如果您的工作流程使用 actions/checkout 操作，工作空间目录将包含存储仓库副本的子目录。 如果不使用 actions/checkout 操作，该目录将为空。 例如 /home/runner/work/my-repo-name/my-repo-name。
    `GITHUB_REPOSITORY`|所有者和仓库名称。 例如 octocat/Hello-World

      您设置的指向文件系统上某个位置的任何新环境变量都应该有 _PATH 后缀。 HOME 和 GITHUB_WORKSPACE 默认变量例外于此约定，因为 "home" 和 "workspace" 一词已经暗示位置

  - ### [expect](http://xstarcd.github.io/wiki/shell/expect_handbook.html)
   
    Todo: expect 交互式shell脚本

