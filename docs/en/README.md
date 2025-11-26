<p align="center">
  <img src="https://avatars.githubusercontent.com/u/149707645?s=400&v=4" width="180" alt="Vateron Media Logo"/>
</p>

<h1 align="center">📺 XC_VM IPTV Panel</h1>

<p align="center">
  A modern, open-source IPTV panel inspired by Xtream Codes.<br>
  Lightweight. Fast. Community-driven.
</p>

---

## ❓ What Is It?

**XC_VM** is a modern IPTV panel built on PHP, Nginx, FFmpeg, and MariaDB.

XC_VM helps you deploy a full IPTV infrastructure:

- Management of Live TV, Movies, and Series  
- Reseller and user management  
- Load Balancing  
- EPG and VOD system  
- Monitoring tools and API

💡 *Completely free. No licenses. No server locks.*

---

## ⭐ Features

- 🚀 Modern IPTV panel architecture  
- 🔀 Built-in load balancer support  
- 🎥 Management of VOD and live streams  
- 🧩 API compatible with Xtream Codes  
- 🔐 Enhanced security fixes  
- 📦 Fast FFmpeg-based transcoding  
- 🌍 Multi-language documentation  
- 🧭 Simple and intuitive interface  
- 🛠 Modular extension system  

---

## 🧰 Technologies

- **Nginx** — reverse proxy & web server  
- **PHP 8.2** — core backend  
- **MariaDB** — database  
- **KeyDB** — cache/session engine  
- **FFmpeg 8.0** — transcoding  
- **yt-dlp** — media acquiring  

XC_VM officially supports Ubuntu 22.04 and is tested on 24.04.

---

## 🌐 Community

XC_VM is a fully community-driven project.

- 💬 Issues: https://github.com/Vateron-Media/XC_VM/issues  
- ⭐ GitHub Stars: support the project by giving it a star  
- 🔧 Pull Requests: welcome  

If you want to contribute, read the:  
[Contributing Guide](https://github.com/Vateron-Media/XC_VM/blob/master/CONTRIBUTING.md)

---

## 🛠 Installation

Installation on Ubuntu 22.04+:

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y python3-pip unzip

latest_version=$(curl -s https://api.github.com/repos/Vateron-Media/XC_VM/releases/latest | grep '"tag_name":' | cut -d '"' -f 4)
wget "https://github.com/Vateron-Media/XC_VM/releases/download/${latest_version}/XC_VM.zip"

unzip XC_VM.zip
sudo python3 install
````

---

## ⚠️ Disclaimer

> You are fully responsible for your own use of this software.