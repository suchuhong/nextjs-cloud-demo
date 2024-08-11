This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## 笔记

使用 github 在云主机部署 nextjs 应用

---

![image](https://hackmd.io/_uploads/HJU1KMB9R.png)

### 建立 github 项目

https://github.com/suchuhong/nextjs-cloud-demo.git

### 构建 nextjs 应用

1、拉取项目

```shell
git clone git@github.com:suchuhong/nextjs-cloud-demo.git
```

2、创建应用

```shell
(base) PS E:\N-nextjs\nextjs-cloud-demo> npx create-next-app@latest ./
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like to use `src/` directory? ... No / Yes
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to customize the default import alias (@/*)? ... No / Yes
Creating a new Next.js app in E:\N-nextjs\nextjs-cloud-demo.

Using npm.

Initializing project with template: app-tw


Installing dependencies:
- react
- react-dom
- next

Installing devDependencies:
- typescript
- @types/node
- @types/react
- @types/react-dom
- postcss
- tailwindcss
- eslint
- eslint-config-next

npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
npm warn deprecated @humanwhocodes/config-array@0.11.14: Use @eslint/config-array instead
npm warn deprecated rimraf@3.0.2: Rimraf versions prior to v4 are no longer supported
npm warn deprecated glob@7.2.3: Glob versions prior to v9 are no longer supported
npm warn deprecated @humanwhocodes/object-schema@2.0.3: Use @eslint/object-schema instead

added 360 packages in 21s

136 packages are looking for funding
  run `npm fund` for details
Success! Created nextjs-cloud-demo at E:\N-nextjs\nextjs-cloud-demo

npm notice
npm notice New patch version of npm available! 10.8.0 -> 10.8.2
npm notice Changelog: https://github.com/npm/cli/releases/tag/v10.8.2
npm notice To update run: npm install -g npm@10.8.2
npm notice
```

3、使用 vscode 打开，推送分支

.env 文件

4、配置 github 项目环境变量

https://github.com/suchuhong/nextjs-cloud-demo/settings/secrets/actions

![image](https://hackmd.io/_uploads/HJ0hCfS5R.png)

### 准备云服务器

1、购买腾讯云服务器（ubuntu）

2、登录云服务器

3、创建用户

```
sudo adduser susu
cat /etc/group | grep -E "sudo|wheel"

usermod -aG wheel susu
或者
usermod -aG sudo susu

sudo su - susu
```

4、切换用户

5、按照 nvm（Node Version Manager）

https://github.com/nvm-sh/nvm
https://github.com/nvm-sh/nvm?tab=readme-ov-file#git-install

网络原因，fork 到 gitee

1. clone this repo in the root of your user profile
2. cd ~/ from anywhere then git clone https://gitee.com/suchuhong/nvm.git .nvm
3. cd ~/.nvm and check out the latest version with git checkout v0.40.0
4. activate nvm by sourcing it from your shell: . ./nvm.sh

```
cd ~
git clone https://gitee.com/suchuhong/nvm.git .nvm

sudo vim ~/.bashrc

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

source ~/.bashrc

```

#### nvm 换源

```
sudo vim ~/.bashrc

export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node/

source ~/.bashrc
```

#### nvm 安装 node

```shell
[susu@VM-20-15-centos ~]$  nvm install v20.16.0
Downloading and installing node v20.16.0...
Downloading https://npmmirror.com/mirrors/node//v20.16.0/node-v20.16.0-linux-x64.tar.xz...
######################################################################## 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v20.16.0
Creating default alias: default -> v20.16.0

```

#### npm 镜像

要查看当前 npm 使用的镜像源，可以使用以下命令来检查 npm 配置的 registry 地址：

```bash
npm config get registry
```

这个命令会返回当前 npm 使用的镜像源的 URL。例如：

```
https://registry.npmjs.org/
```

这表示 npm 正在使用默认的官方镜像源。如果你使用了其他镜像源（例如淘宝镜像源），输出可能会是：

```
https://registry.npmmirror.com/
```

查看所有配置项
你也可以使用 npm config list 来查看所有的 npm 配置，包括镜像源：

```
npm config list
```

在输出的内容中，registry 选项会显示当前的镜像源地址。

修改 npm 镜像源
如果你想更改 npm 的镜像源，可以使用以下命令：

设置为淘宝镜像源：

```
npm config set registry https://registry.npmmirror.com/
```

设置回默认的官方镜像源：

```
npm config set registry https://registry.npmjs.org/
```

### 安装 pm2

Advanced, production process manager for Node.JS

https://pm2.keymetrics.io/

### 配置 runner

![image](https://hackmd.io/_uploads/BkvPwhBqA.png)

![image](https://hackmd.io/_uploads/BJm6whr9A.png)

![image](https://hackmd.io/_uploads/HyB5unHcR.png)

```shell

./svc.sh [install, start, stop, status, uninstall]


susu@VM-20-15-ubuntu:~/actions-runner$ sudo ./svc.sh install
Creating launch runner in /etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service
Run as user: susu
Run as uid: 1002
gid: 1002
Created symlink /etc/systemd/system/multi-user.target.wants/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service → /etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service.

susu@VM-20-15-ubuntu:~/actions-runner$ sudo ./svc.sh status

/etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service
○ actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service - GitHub Actions Runner (suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu)
     Loaded: loaded (/etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service; enabled; vendor preset: enabled)
     Active: inactive (dead)

susu@VM-20-15-ubuntu:~/actions-runner$ sudo ./svc.sh start

/etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service
● actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service - GitHub Actions Runner (suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu)
     Loaded: loaded (/etc/systemd/system/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-08-11 12:09:23 CST; 5ms ago
   Main PID: 249400 (runsvc.sh)
      Tasks: 2 (limit: 18436)
     Memory: 748.0K
        CPU: 4ms
     CGroup: /system.slice/actions.runner.suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu.service
             ├─249400 /bin/bash /home/susu/actions-runner/runsvc.sh
             └─249403 ./externals/node16/bin/node ./bin/RunnerService.js

Aug 11 12:09:23 VM-20-15-ubuntu systemd[1]: Started GitHub Actions Runner (suchuhong-nextjs-cloud-demo.VM-20-15-ubuntu).
Aug 11 12:09:23 VM-20-15-ubuntu runsvc.sh[249400]: .path=/home/susu/.nvm/versions/node/v20.16.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin


```

### 配置 workflow

![image](https://hackmd.io/_uploads/rJzV9nB5R.png)

```yml
# This workflow will do a clean installation of node dependencies, cache/restore them, build the source code and run tests across different versions of node
# For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-nodejs

name: Node.js CI

on:
  push:
    branches: ['main']

jobs:
  build:
    runs-on: self-hosted

    strategy:
      matrix:
        node-version: [20.16.0]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/
    env:
      NEXT_WEBSITE_URL: ${{secrets.NEXT_WEBSITE_URL}}

    steps:
      - uses: actions/checkout@v4
        # 使用自带的node
        # - name: Use Node.js ${{ matrix.node-version }}
        #   uses: actions/setup-node@v4
        #   with:
        #     node-version: ${{ matrix.node-version }}
        #     cache: 'npm'
      - name: Show Node.js version
        run: node --version

      - name: Show Node.js path
        run: which node

      - name: Show npm path
        run: which npm

      - name: npm config get registry
        run: npm config get registry

      - name: Install dependencies using npm ci
        run: npm ci

      - run: npm run build --if-present
```

![image](https://hackmd.io/_uploads/Syqyhnrc0.png)

### 使用 pm2 监控

```
susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ pm2 start npm --name "nextjs" -- start --watch

```

![image](https://hackmd.io/_uploads/S1n9Q6H5R.png)

### 验证是否部署成功

http://ip:3000/

![image](https://hackmd.io/_uploads/BJv-Epr9C.png)

![image](https://hackmd.io/_uploads/r15arpSqA.png)

### 配置 pm2 自启动

```shell
susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ pm2 startup


[PM2] Init System found: systemd
[PM2] To setup the Startup Script, copy/paste the following command:
sudo env PATH=$PATH:/home/susu/.nvm/versions/node/v20.16.0/bin /home/susu/.nvm/versions/node/v20.16.0/lib/node_modules/pm2/bin/pm2 startup systemd -u susu --hp /home/susu

susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo env PATH=$PATH:/home/susu/.nvm/versions/node/v20.16.0/bin /home/susu/.nvm/versions/node/v20.16.0/lib/node_modules/pm2/bin/pm2 startup systemd -u susu --hp /home/susu



[sudo] password for susu:

                        -------------

__/\\\\\\\\\\\\\____/\\\\____________/\\\\____/\\\\\\\\\_____
 _\/\\\/////////\\\_\/\\\\\\________/\\\\\\__/\\\///////\\\___
  _\/\\\_______\/\\\_\/\\\//\\\____/\\\//\\\_\///______\//\\\__
   _\/\\\\\\\\\\\\\/__\/\\\\///\\\/\\\/_\/\\\___________/\\\/___
    _\/\\\/////////____\/\\\__\///\\\/___\/\\\________/\\\//_____
     _\/\\\_____________\/\\\____\///_____\/\\\_____/\\\//________
      _\/\\\_____________\/\\\_____________\/\\\___/\\\/___________
       _\/\\\_____________\/\\\_____________\/\\\__/\\\\\\\\\\\\\\\_
        _\///______________\///______________\///__\///////////////__


                          Runtime Edition

        PM2 is a Production Process Manager for Node.js applications
                     with a built-in Load Balancer.

                Start and Daemonize any application:
                $ pm2 start app.js

                Load Balance 4 instances of api.js:
                $ pm2 start api.js -i 4

                Monitor in production:
                $ pm2 monitor

                Make pm2 auto-boot at server restart:
                $ pm2 startup

                To go further checkout:
                http://pm2.io/


                        -------------

[PM2] Init System found: systemd
Platform systemd
Template
[Unit]
Description=PM2 process manager
Documentation=https://pm2.keymetrics.io/
After=network.target

[Service]
Type=forking
User=susu
LimitNOFILE=infinity
LimitNPROC=infinity
LimitCORE=infinity
Environment=PATH=/home/susu/.nvm/versions/node/v20.16.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/susu/.nvm/versions/node/v20.16.0/bin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
Environment=PM2_HOME=/home/susu/.pm2
PIDFile=/home/susu/.pm2/pm2.pid
Restart=on-failure

ExecStart=/home/susu/.nvm/versions/node/v20.16.0/lib/node_modules/pm2/bin/pm2 resurrect
ExecReload=/home/susu/.nvm/versions/node/v20.16.0/lib/node_modules/pm2/bin/pm2 reload all
ExecStop=/home/susu/.nvm/versions/node/v20.16.0/lib/node_modules/pm2/bin/pm2 kill

[Install]
WantedBy=multi-user.target

Target path
/etc/systemd/system/pm2-susu.service
Command list
[ 'systemctl enable pm2-susu' ]
[PM2] Writing init configuration in /etc/systemd/system/pm2-susu.service
[PM2] Making script booting at startup...
[PM2] [-] Executing: systemctl enable pm2-susu...
Created symlink /etc/systemd/system/multi-user.target.wants/pm2-susu.service → /etc/systemd/system/pm2-susu.service.
[PM2] [v] Command successfully executed.
+---------------------------------------+
[PM2] Freeze a process list on reboot via:
$ pm2 save

[PM2] Remove init script via:
$ pm2 unstartup systemd

susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ pm2 save

[PM2] Saving current process list...
[PM2] Successfully saved in /home/susu/.pm2/dump.pm2


```

### 安装 nginx

```
sudo apt install nginx

systemctl status nginx



```

http://ip:80
![image](https://hackmd.io/_uploads/ByxXt6H9R.png)

### 配置 nginx-反向代理（端口不同）

```
susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo vim /etc/nginx/sites-available/nextjsdemo1

server {
  listen 3001;
  listen [::]:3001;

  server_name 106.53.186.99;

  location / {
    proxy_pass http://localhost:3000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
  }

}




susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo ln  -s /etc/nginx/sites-available/nextjsdemo1 /etc/nginx/sites-enabled/



susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo systemctl restart nginx


```

### 配置域名

https://porkbun.com/tld/chat?coupon=STARTACHAT&utm_source=Google&utm_medium=PaidAds&utm_campaign=DotChat2425&gad_source=1&gclid=Cj0KCQjwn9y1BhC2ARIsAG5IY-6fTCAFjOWPmg4fQW5iPyqXx2j_nANWyc9pRWIIXpI8yY4IaWv_yfIaAgfrEALw_wcB

### 配置 https

```
susu@VM-20-15-ubuntu:~/actions-runner/_work/nextjs-cloud-demo/nextjs-cloud-demo$ sudo apt install certbot python3-certbot-nginx

sudo certbot --nginx -d 域名1 -d 域名2

```

### 参考

https://www.youtube.com/watch?v=fkzpywlJcMA
https://github.com/nvm-sh/nvm
https://github.com/nvm-sh/nvm?tab=readme-ov-file#git-install
https://pm2.keymetrics.io/

https://www.cnblogs.com/kohler21/p/18331060
