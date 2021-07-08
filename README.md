<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="Laboratorio_03__Vagrant_0"></a>Laboratorio 03 - Vagrant</h1>
<hr>
<p class="has-line-data" data-line-start="2" data-line-end="3">En este laboratorio se creará una Virtual Machine mediante líneas de comando usando <strong>Vagrant</strong></p>
<ol>
<li class="has-line-data" data-line-start="4" data-line-end="5">Creamos el directorio</li>
</ol>
<pre><code class="has-line-data" data-line-start="6" data-line-end="8" class="language-sh"><span class="hljs-variable">$mkdir</span> vagrant_V2
</code></pre>
<ol start="2">
<li class="has-line-data" data-line-start="8" data-line-end="9">Nos ubicamos en la carpeta creada e inicializamos <em>Vagrant</em></li>
</ol>
<pre><code class="has-line-data" data-line-start="10" data-line-end="20" class="language-sh"><span class="hljs-variable">$cd</span> vagrant_V2
$ vagrant init
==&gt; vagrant: A new version of Vagrant is available: <span class="hljs-number">2.2</span>.<span class="hljs-number">17</span> (installed version: <span class="hljs-number">2.2</span>.<span class="hljs-number">16</span>)!
==&gt; vagrant: To upgrade visit: https://www.vagrantup.com/downloads.html

A `Vagrantfile` has been placed <span class="hljs-keyword">in</span> this directory. You are now
ready to `vagrant up` your first virtual environment! Please <span class="hljs-built_in">read</span>
the comments <span class="hljs-keyword">in</span> the Vagrantfile as well as documentation on
`vagrantup.com` <span class="hljs-keyword">for</span> more information on using Vagrant.
</code></pre>
<ol start="3">
<li class="has-line-data" data-line-start="20" data-line-end="21">El comando anterior creará un documento de nombre <em>Vagrantfile</em>, lo cual se editará poniendo lo siguiente</li>
</ol>
<pre><code class="has-line-data" data-line-start="22" data-line-end="35" class="language-sh"><span class="hljs-variable">$vi</span> Vagrantfile
<span class="hljs-comment"># -*- mode: ruby -*-</span>
<span class="hljs-comment"># vi: set ft=ruby :</span>

Vagrant.configure(<span class="hljs-string">"2"</span>) <span class="hljs-keyword">do</span> |config|
  
  config.vm.box = <span class="hljs-string">"centos/7"</span>
  config.vm.hostname = <span class="hljs-string">"prueba-v1"</span>
  config.vm.network :private_network, ip: <span class="hljs-string">"192.168.0.254"</span>
  

end
</code></pre>
<ol start="4">
<li class="has-line-data" data-line-start="35" data-line-end="36">Luego se creará la máquina virtual con el siguiente comando</li>
</ol>
<pre><code class="has-line-data" data-line-start="37" data-line-end="84" class="language-sh"><span class="hljs-variable">$vagrant</span> up
Bringing machine <span class="hljs-string">'default'</span> up with <span class="hljs-string">'virtualbox'</span> provider...
==&gt; default: Box <span class="hljs-string">'centos/7'</span> could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: &gt;= <span class="hljs-number">0</span>
==&gt; default: Loading metadata <span class="hljs-keyword">for</span> box <span class="hljs-string">'centos/7'</span>
    default: URL: https://vagrantcloud.com/centos/<span class="hljs-number">7</span>
==&gt; default: Adding box <span class="hljs-string">'centos/7'</span> (v2004.<span class="hljs-number">01</span>) <span class="hljs-keyword">for</span> provider: virtualbox
    default: Downloading: https://vagrantcloud.com/centos/boxes/<span class="hljs-number">7</span>/versions/<span class="hljs-number">2004.01</span>/providers/virtualbox.box
Download redirected to host: cloud.centos.org
    default:
    default: Calculating and comparing box checksum...
==&gt; default: Successfully added box <span class="hljs-string">'centos/7'</span> (v2004.<span class="hljs-number">01</span>) <span class="hljs-keyword">for</span> <span class="hljs-string">'virtualbox'</span>!
==&gt; default: Importing base box <span class="hljs-string">'centos/7'</span>...
==&gt; default: Matching MAC address <span class="hljs-keyword">for</span> NAT networking...
==&gt; default: Checking <span class="hljs-keyword">if</span> box <span class="hljs-string">'centos/7'</span> version <span class="hljs-string">'2004.01'</span> is up to date...
==&gt; default: Setting the name of the VM: vagrant_V2_default_1625769985079_40113
==&gt; default: Clearing any previously <span class="hljs-built_in">set</span> network interfaces...
==&gt; default: Preparing network interfaces based on configuration...
    default: Adapter <span class="hljs-number">1</span>: nat
    default: Adapter <span class="hljs-number">2</span>: hostonly
==&gt; default: Forwarding ports...
    default: <span class="hljs-number">22</span> (guest) =&gt; <span class="hljs-number">2222</span> (host) (adapter <span class="hljs-number">1</span>)
==&gt; default: Booting VM...
==&gt; default: Waiting <span class="hljs-keyword">for</span> machine to boot. This may take a few minutes...
    default: SSH address: <span class="hljs-number">127.0</span>.<span class="hljs-number">0.1</span>:<span class="hljs-number">2222</span>
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair <span class="hljs-keyword">for</span> better security.
    default:
    default: Inserting generated public key within guest...
==&gt; default: Machine booted and ready!
==&gt; default: Checking <span class="hljs-keyword">for</span> guest additions <span class="hljs-keyword">in</span> VM...
    default: No guest additions were detected on the base box <span class="hljs-keyword">for</span> this VM! Guest
    default: additions are required <span class="hljs-keyword">for</span> forwarded ports, shared folders, host only
    default: networking, and more. If SSH fails on this machine, please install
    default: the guest additions and repackage the box to continue.
    default:
    default: This is not an error message; everything may <span class="hljs-built_in">continue</span> to work properly,
    default: <span class="hljs-keyword">in</span> <span class="hljs-built_in">which</span> <span class="hljs-keyword">case</span> you may ignore this message.
==&gt; default: Setting hostname...
==&gt; default: Configuring and enabling network interfaces...
==&gt; default: Rsyncing folder: /cygdrive/c/Users/mserg/Documents/All Git/vagrant_V2/ =&gt; /vagrant

</code></pre>
<ol start="5">
<li class="has-line-data" data-line-start="84" data-line-end="85">Revisamos el estado de lo creado</li>
</ol>
<pre><code class="has-line-data" data-line-start="86" data-line-end="97" class="language-sh"><span class="hljs-variable">$vagrant</span> status
Current machine states:

default                   running (virtualbox)

The VM is running. To stop this VM, you can run `vagrant halt` to
shut it down forcefully, or you can run `vagrant <span class="hljs-built_in">suspend</span>` to simply
<span class="hljs-built_in">suspend</span> the virtual machine. In either <span class="hljs-keyword">case</span>, to restart it again,
simply run `vagrant up`.

</code></pre>
<ol start="6">
<li class="has-line-data" data-line-start="97" data-line-end="98">Validaremos la IP asignada a la máquina</li>
</ol>
<pre><code class="has-line-data" data-line-start="99" data-line-end="123" class="language-sh"><span class="hljs-variable">$vagrant</span> ssh
[vagrant@prueba-v1 ~]$
[vagrant@prueba-v1 ~]<span class="hljs-variable">$sudo</span> su -
[root@prueba-v1 ~]<span class="hljs-comment"># ip a</span>
<span class="hljs-number">1</span>: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu <span class="hljs-number">65536</span> qdisc noqueue state UNKNOWN group default qlen <span class="hljs-number">1000</span>
    link/loopback <span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span> brd <span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>:<span class="hljs-number">00</span>
    inet <span class="hljs-number">127.0</span>.<span class="hljs-number">0.1</span>/<span class="hljs-number">8</span> scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::<span class="hljs-number">1</span>/<span class="hljs-number">128</span> scope host
       valid_lft forever preferred_lft forever
<span class="hljs-number">2</span>: eth0: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu <span class="hljs-number">1500</span> qdisc pfifo_fast state UP group default qlen <span class="hljs-number">1000</span>
    link/ether <span class="hljs-number">52</span>:<span class="hljs-number">54</span>:<span class="hljs-number">00</span>:<span class="hljs-number">4</span>d:<span class="hljs-number">77</span>:d3 brd ff:ff:ff:ff:ff:ff
    inet <span class="hljs-number">10.0</span>.<span class="hljs-number">2.15</span>/<span class="hljs-number">24</span> brd <span class="hljs-number">10.0</span>.<span class="hljs-number">2.255</span> scope global noprefixroute dynamic eth0
       valid_lft <span class="hljs-number">84151</span>sec preferred_lft <span class="hljs-number">84151</span>sec
    inet6 fe80::<span class="hljs-number">5054</span>:ff:fe4d:<span class="hljs-number">77</span>d3/<span class="hljs-number">64</span> scope link
       valid_lft forever preferred_lft forever
<span class="hljs-number">3</span>: eth1: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu <span class="hljs-number">1500</span> qdisc pfifo_fast state UP group default qlen <span class="hljs-number">1000</span>
    link/ether <span class="hljs-number">08</span>:<span class="hljs-number">00</span>:<span class="hljs-number">27</span>:<span class="hljs-number">3</span>c:<span class="hljs-number">8</span>a:e4 brd ff:ff:ff:ff:ff:ff
    inet <span class="hljs-number">192.168</span>.<span class="hljs-number">0.254</span>/<span class="hljs-number">24</span> brd <span class="hljs-number">192.168</span>.<span class="hljs-number">0.255</span> scope global noprefixroute eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:<span class="hljs-number">27</span>ff:fe3c:<span class="hljs-number">8</span>ae4/<span class="hljs-number">64</span> scope link
       valid_lft forever preferred_lft forever

</code></pre>
<blockquote>
<p class="has-line-data" data-line-start="123" data-line-end="124">En “eth1” no muestra la IP que se asignó en la configuración.</p>
</blockquote>
