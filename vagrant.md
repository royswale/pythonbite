this post was previously published on medium

[https://medium.com/p/6d40f6fb8032/edit](https://medium.com/p/6d40f6fb8032/edit)

Install VirtualBox and Vagrant to “D:\Program Files\xxx”

Change VirtualBox \[File -&gt; Preferences -&gt; Default Mchine Folder\] to “D:\Program Files\Oracle\VirtualBox\VMs”

![](https://cdn-images-1.medium.com/max/800/1*pOnp97zmE8fixXnX_M3mvg.png)

Set “VAGRANT\_HOME” environment variable as “D:\Program Files\HashiCorp\Vagrant.vagrant.d”

[**Environmental Variables - Vagrant by HashiCorp**  
\_Vagrant has a set of environmental variables that can be used to configure and control it in a global way. This page…\_www.vagrantup.com](https://www.vagrantup.com/docs/other/environmental-variables.html#vagrant_home)

[**Change VAGRANT\_HOME directory on windows \| Harv's World**  
\_I have no idea why this was so difficult. Maybe because I'm n00bsauce. I have an SSD for my boot drive, which I don't…\_harvsworld.com](https://harvsworld.com/2014/change-vagrant_home-directory-windows/)

![](https://cdn-images-1.medium.com/max/800/1*g1eHz5mZdsuXYa1MQ1PIfA.png)

Open powershell or git bash, in whatever directory.

```
vagrant box add debian/jessie64
```

Failed to connect to aws!

But from the prompt message you can download this box manually from “ [https://vagrantcloud.com/debian/boxes/jessie64/versions/8.9.0/providers/virtualbox.box](https://vagrantcloud.com/debian/boxes/jessie64/versions/8.9.0/providers/virtualbox.box)”.

After successfully download, rename it from “b643c094–1f49–44f1-a62b-d2aca5d37a2e” to “debian.jessie64.virtualbox.box”,this is not necessary, but looks straightforward as a vagrant box file.

![](https://cdn-images-1.medium.com/max/800/1*6CJVZMVYRSsMPZeE98KeXA.png)

```
vagrant box add debianjessie64 “C:\Users\royswale\Downloads\debian.jessie64.virtualbox.box”
```

![](https://cdn-images-1.medium.com/max/800/1*AaoUBEQiwzw0Axx6h4d46A.png)

You can find that the box is added to the directory “D:\Program Files\HashiCorp\Vagrant.vagrant.d\boxes”

![](https://cdn-images-1.medium.com/max/800/1*dRTPdVkky5LEFJR8or6Pjw.png)

Now change directory to “D:\Vagrant\tokyodebian”, this is project directory created by me manually.

```
vagrant init debianjessie64
```

![](https://cdn-images-1.medium.com/max/800/1*-MFTjmQW0HaHNMMQC_Awhw.png)

observe the project directory

![](https://cdn-images-1.medium.com/max/800/1*ql19ockILaBrmItxWseM2Q.png)

[**Up and SSH - Getting Started - Vagrant by HashiCorp**  
\_It is time to boot your first Vagrant environment. Run the following from your terminal - vagrant up\_www.vagrantup.com](https://www.vagrantup.com/intro/getting-started/up.html)

```
vagrant up


vagrant status


vagrant ssh
```

![](https://cdn-images-1.medium.com/max/800/1*rUUi7HEHyd4KzpwgY9VnZw.png)

```
vagrant halt
```

![](https://cdn-images-1.medium.com/max/800/1*e0fV-yhwet8G8iWCGAy66Q.png)

coming soon….

synced folders between host and guest

[**Synced Folders - Vagrant by HashiCorp**  
\_Synced folders enable Vagrant to sync a folder on the host machine to the guest machine, allowing you to continue…\_www.vagrantup.com](https://www.vagrantup.com/docs/synced-folders/)

[**Basic Usage - Synced Folders - Vagrant by HashiCorp**  
\_Synced folders are configured within your Vagrantfile using the config.vm.synced\_folder method.\_www.vagrantup.com](https://www.vagrantup.com/docs/synced-folders/basic_usage.html)

[https://www.vagrantup.com/docs/synced-folders/basic\_usage.html](https://www.vagrantup.com/docs/synced-folders/basic_usage.html)

synced folder configure like this in "/d/Vagrant/debian9js/Vagrantfile"

![](/assets/vagrant_synced_folder.png)disable the default synced folder, and sync '../../VMshare' to '/vagrant\_data'.

and set memory to 2G

[http://www.jianshu.com/p/3c3f35436c05](http://www.jianshu.com/p/3c3f35436c05 "Vagrant搭建虚拟化开发环境")

```
vagrant reload
```

![](/assets/mount_error.png)mount: unknown filesystem type 'vboxsf'

[https://github.com/hashicorp/vagrant/issues/6769\#issuecomment-252151694](https://github.com/hashicorp/vagrant/issues/6769#issuecomment-252151694)

![](/assets/virtualbox_guest_additions.png)

```
vagrant plugin install vagrant-vbguest
```

![](/assets/vbguest.png)notice: open shadowsocks on my host PC, and turn the mod to 'global' instead of 'PAC'

```
vagrant reload
```

![](/assets/reload.png)

got 34 packages newly installed.

and finally see the mount success infomation

![](/assets/mount.png)vagrant ssh

![](/assets/shared_folder.png)

configure private\_network, [http://www.jianshu.com/p/3c3f35436c05](http://www.jianshu.com/p/3c3f35436c05 "Vagrant搭建虚拟化开发环境")

![](/assets/private_network.png)

ping 192.168.33.10 from host PC

![](/assets/ping.png)

