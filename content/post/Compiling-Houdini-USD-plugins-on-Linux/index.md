+++
author = "Jakub Vondra"
title = "Compiling Houdini USD plugins on Linux"
date = "2019-07-31"
description = "A guide on compiling Houdini USD plugins on Linux"
tags = [
    "Houdini",
    "USD",
]
categories = [
    "guides",
    "tutorials",
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
image = "teaser.jpg"
+++
## USD
For more info about what is USD and why it could interest you, check here:<br>
[Pixar USD page](https://graphics.pixar.com/usd/docs/Introduction-to-USD.html)<br>
[SideFX's USD-based SOLARIS project.](https://youtu.be/emcT5qXdUsc)<br><br>

Since version 17 Houdini comes with USD plugins. There is a catch though, you have to compile them yourself.<br><br>
There is [a video from Rachid Abderrahmane.](https://www.sidefx.com/tutorials/compiling-usd-plugins-for-houdini-windows-10/) on compiling the plugins on Windows.<br>
Even though compiling the plugins on Linux is much more simple, this could save someone a couple minutes.<br>

## Steps
I'm using popOS which is based on Ubuntu. On other linux distros the commands migth slightly differ.<br><br>

Start by installing cmake in terminal:<br>
{% highlight shell %}
sudo apt install cmake
{% endhighlight %}

Let's say you have Houdini installed in /opt/hfs17.5.173/<br>
Under folder toolkit there is <i>usd_houdini_plugins</i> folder.<br>
![My helpful screenshot](01.jpg)<br>
Copy that folder to e.g. <i>home/YOUR_USER/Documents/temp/</i> <br>(to avoid problem with user premissions)<br>
![My helpful screenshot](02.jpg)<br>

Make folder called <i>build</i> under the <i>usd_houdini_plugins folder.</i><br>
![My helpful screenshot](03.jpg)<br>
<br>
in terminal cd to this folder:
{% highlight shell %}
cd /home/YOUR_USER/Documents/temp/usd_houdini_plugins
{% endhighlight %}

export CMAKE_PREFIX_PATH variable:
{% highlight shell %}
export CMAKE_PREFIX_PATH="/opt/hfs17.5.173/toolkit/cmake"
{% endhighlight %}

Build the plugins:
{% highlight shell %}
cmake /opt/hfs17.5.173/toolkit/usd_houdini_plugins
{% endhighlight %}

And install:
{% highlight shell %}
make -j8 install
{% endhighlight %}

![My helpful screenshot](06.jpg)

If everything went ok, then after starting Houdini you should be able to create USD nodes.
For more info about how to use them go to [USD Houdini documentation](https://graphics.pixar.com/usd/docs/A-Tour-of-USD-Houdini-Primitives.html)<br><br>

![My helpful screenshot](07.jpg)