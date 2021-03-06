---
title: "Deploy Django to MS Azure with Fabric3"
date: 2017-06-10
layout: post
categories:
- django
- fabric
published: true
image: https://d1sr4ybm5bj1wl.cloudfront.net/img/azure.jpg
---

> 한국어 버전은 [Django MS Azure에 Fabric으로 배포하기](/2017/06/09/Deploy-Django-to-MS-Azure/)에서 보실 수 있습니다.

> This guide covers about deploying [DjangoGirls Tutorial](https://tutorial.djangogirls.org/en/) to MS Azure Virtual machine(Ubuntu 16.04 LTS) with Fabric3.

You're probably participant in [DjangoGirls Tutorial Workshop](https://tutorial.djangogirls.org/ko/) and you'll be now on 'deploy' step on it. 

Today we're going to deploy our django project to [Azure](http://azure.com) which is provided with MS.

If you didnt' register your `AzurePass` yet, please precede this guide first: [Register Azure and redeem AzurePass](/2017/06/21/Activate-MS-AzurePass/)

## (If Windows) Using `cmder`

You can't use linux commands like `git` or `ssh` on your `cmd`, so we're going to use great shell program which named `cmder`.

![]({{site.static_url}}/img/dropbox/2017-06-18%2010.30.18.png)

First, click this link:[cmder.zip](https://github.com/cmderdev/cmder/releases/download/v1.3.2/cmder.zip) to download cmder. (It may take times.)

Second, unzip downloaded `cmder.zip` file. (It'll take some times too.) And then you got this!:

![]({{site.static_url}}/img/azure_fabric/1-folder.PNG)

Execute `cmder.exe` in this folder. If you execute `cmder.exe` as a first time you'll be see Security Warning like this: just click `RUN`.

![]({{site.static_url}}/img/azure_fabric/2-securityWarning.PNG)

And one time more, if you execute cmder for the first time, there will be another warning like this: click first option, "Unblock and continue".

![]({{site.static_url}}/img/azure_fabric/3-UnblockBinaries.PNG)

It'll take some times when you run cmder first time. This wouln't appear next time, so please wait for a moment!

![]({{site.static_url}}/img/azure_fabric/4-firstlook.PNG)

If you see this, you're ready to use `cmder` NOW!

![]({{site.static_url}}/img/azure_fabric/5-final.PNG)


If you're following DjangoGirls Tutorial, you probably made folder named `djangogirls`. Let's get into it.

> `cd` is command to ender the folder! Let's get into `djangogirls` folder with `cd djangogirls`.

Let's start deploy then.

## Deploy Azure Virtual machine

You'll see this screen if you logged in to [Azure Portal](https://portal.azure.com/).

![Azure Portal Dashboard]({{site.static_url}}/img/dropbox/2017-06-23%2012.39.54.png)

Let's make Virtual machine with clicking `VirtualComputer(가상 컴퓨터)` button.

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.41.09.png)

Now let's add Virtual machine with '+Add' button.

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.41.22.png)

If you click `+ Add` button, you'll see another options which provides many OS. But  we're going to use `Ubuntu Server` today.

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.41.53.png)

If you clicked Ubuntu Server there'll be server lists like this: we'll use `Ubuntu Server 16.04 LTS`.

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.42.10.png)

Then you'll see `Create` button. Click it!

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.42.24.png)

You'll see configure window when you click `Create` button. Fillout blanks like picture lower.

![]({{site.static_url}}/img/dropbox/2017-06-23%2012.43.45.png)

> Username should be `django` (surelly this is not critical but you may encounter issues.

> You may set your password on your own, but it shoud be longer/equal than 12. Please remember not to reset it later.

> Select locaiton on Korea Centeral or SouthEast Asia(which available one).

Now we have to choose server size. We'll setup just one django server so we'll choose `DS1_V2`, the left one.

> Don't worry, you won't be charged :)

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.46.03.png)

Next step you have to setup storage settings. Just select `Use managed disks` to 'Yes'.

And then click `Network Security Group(Firewall)` settings. After click on it, you'll see pre-configured setting `SSH (TCP/22)`. We're going to add `HTTP (TCP/80)`

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.47.06.png)

Click `+ Inbound Rule add` Button, and fillout blanks like this and click OK button.

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.47.31.png)

Now default settings are finished! Just click OK button.

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.47.57.png)

And one more time, click confirm button.

![]({{site.static_url}}/img/dropbox/2017-06-10%2000.25.18.png)

And lastly, click confirm button more! I know you're tired with confirm button, but this is process of Azure :)

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.48.21.png)

If you see your azure dashboard again like this, your server deployment is finished :)

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.48.36.png)

Please wait until your server is successfully installed! (This will take upto 5mins.)

> Your browser will redirected to your server info page when your server is successfully installed.

## Get Azure Server Configurations

You can access to your server info with clicking server icon-which tells `Running`.

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2012.52.43.png)

On this page you can see your server's 'Public IP Address'. `ip` is set of numbers which provides your computer access to internet. We can upload and deploy our django project through this ip.

You can see this example server's ip, `13.67.60.234`. Surelly we can access to our server with this numbers but we can't remember easily with it.

So we're going to use `domain` like `djangogirls.com` to that `ip`.

First of all, copy(CTRL+C) your virtual machine's ip!

## Get free domain and connect to Virtual Machine

You may know about popular domains like `.com` or `.net`. But they are paid one(10 dollars per year) so we're going to use free domain.

Let's go to [Dot.tk](http://dot.tk).

This [Dot.tk](http://dot.tk) provides `.tk` domains as free! I'll check `djangogirls-seoul-tutorial-en.tk` as example. You should think of your own domain name and click `Check Availability`!

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2013.05.00.png)

Oh, it's available! Just click 'get it now' button and add to cart.

![]({{site.static_url}}/img/dropbox/2017-06-10%2000.38.28.png)

You'll see this page when you clicked 'checkout' button. Just click 'Use DNS' button and input ip address of your virtual machine(azure) and click 'Continue'.

![]({{site.static_url}}/img/dropbox/Screenshot%202017-06-23%2013.06.02.png)

> If you forgot ip address of your virtual machine, go to [Azure portal](https://portal.azure.com) and check your machine's ip again!

You'll see checkout page and you have to login. You can login with your social media account like Google or Facebook!

> Sometimes there are some errors(404 or others..) then you can restart from "Get free domain and connect to Virtual Machine" on this guide.

![]({{site.static_url}}/img/dropbox/2017-06-10%2000.40.52.png)

If you successfully logined, you'll see form to input your info, but you don't have to fill it all. Just click Agress Terms and conditions and Conitnue button, your order will be finished!

![]({{site.static_url}}/img/dropbox/2017-06-10%2000.42.39.png)


![]({{site.static_url}}/img/dropbox/2017-06-10%2000.45.21.png)

Great! You've just connect your own domain to your server!

## Install Fabric3

Now your server is connected with `yourdomainname.tk` domain. But if you try to access to that address, you can see nothing at all. 

Because your server doesn't have any django code and ofcourse, even django!

We'll upload and deploy our django project with just one command line through `Fabric3`.

Let's install `fabric3` on our computer. You can install `fabric3` with this command:

```sh
pip install fabric3
```

> Remember: NOT `fabric` BUT `fabric3`! Don't forget 3. `fabric` is python2 project.

## Downlaod `fabfile.py` and edit `deploy.json`

Download [Fabfile for Django](https://gist.github.com/Beomi/0cc830bd5cda029c277cba648386b28c/archive/0152df8617a63c6678b7b64c54892dc5b4ce19d8.zip) and unzip it.

You can see `deploy.json` and `fabfile.py` inside of it. Move 2 files into your django folder(where `manage.py` exists)

Inside `deploy.json`, we can edit our server(virtual machine) info.

```json
{
  "REPO_URL":"Your Github Repository URL",
  "PROJECT_NAME":"DjangoProject folder's name(where settings.py exists)",
  "REMOTE_HOST":"Your domain(ex: djangogirls-seoul-tutorial-en.tk )",
  "REMOTE_USER":"django",
  "STATIC_ROOT":"static",
  "STATIC_URL":"static",
  "MEDIA_ROOT":"media"
}
```

Change `REPO_URL`, `PROJECT_NAME`, `REMOTE_HOST`. Other values are already setup for djangogirls tutorial we followed.

> Every values must be in ""!

## Upload and deploy code thorugh Fabric3

We can use fabric through `fab` command. Like this: `fab new_server`, `fab deploy`, `fab create_superuser`. This commands will execute commands on remote server(azure virtual machine which we made)

When you use fabric for new server, just type this command and execute: `fab new_server`. this will install python3, apache2, and mod_wsgi to run django.

```sh
fab new_server
```

When you edit django code and committed & pushed to github, then use `fab deploy` command. This will fetch latest code on github and migrate db.

```sh
fab deploy
```

When you want to create superuser, just execute `fab create_superuser` and there'll be creating superuser prompt.

```sh
fab create_superuser
```

## Whoa!

You've just upload and deploy **REAL** working web service on Azure! Congratulation!