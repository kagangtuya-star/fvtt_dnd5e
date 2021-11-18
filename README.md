## 如何使用jsd帮助服务器上的fvtt加速 fvtt核心为0.8.9 5e版本1.5.3

在配置nginx环境中，配置文件对应位置添加如下内容，自行搜索位置

```
server
	{
	listen 80;
	# server_name xxxx.top; 按需求加 换成你的域名
	#ssl_certificate     C:\phpstudy_pro1\Extensions\Nginx1.16.1\ssl2\kagangtuya.top.crt; ssl配置区域，注释了
	#ssl_certificate_key C:\phpstudy_pro1\Extensions\Nginx1.16.1\ssl2\kagangtuya.top.key;
	client_max_body_size 300M;
	location  ^~ /systems/dnd5e/
	{
	rewrite '^/systems/dnd5e/(.*)$' 'https://cdn.jsdelivr.net/gh/kagangtuya-star/fvtt_dnd5e/$1' permanent;
	}
	location /{
	proxy_set_header Host $host;
	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_set_header X-Forwarded-Proto $scheme;
	proxy_set_header Upgrade $http_upgrade;
	proxy_set_header Connection "Upgrade";
	proxy_pass http://127.0.0.1:30000;
	}
}
```






# Foundry Virtual Tabletop - DnD5e Game System

This game system for [Foundry Virtual Tabletop](http://foundryvtt.com) provides character sheet and game system 
support for the Fifth Edition of the world's most popular roleplaying game.

This system is offered and may be used under the terms of the Open Gaming License v1.0a and its accompanying
[Systems Reference Document 5.1 (SRD5)](http://media.wizards.com/2016/downloads/DND/SRD-OGL_V5.1.pdf).

This system provides character sheet support for Actors and Items, mechanical support for dice and rules necessary to
play games of 5th Edition, and compendium content for Monsters, Heroes, Items, Spells, Class Features, Monster 
Features, and more!

Data present under the `packs/` directory is taken from the [Systems Reference Document 5.1 (SRD5)](http://media.wizards.com/2016/downloads/DND/SRD-OGL_V5.1.pdf) and used under the terms of the OGL v1.0a, see OGL.txt.

Images present under the `icons/` directory are distributed under various terms, please see the `icons/LICENSE` file for full details.

The software component of this system is distributed under the MIT license.

## Installation Instructions

To install and use the DnD5e system for Foundry Virtual Tabletop, simply paste the following URL into the 
**Install System** dialog on the Setup menu of the application.

https://gitlab.com/foundrynet/dnd5e/raw/master/system.json

If you wish to manually install the system, you must clone or extract it into the ``Data/systems/dnd5e`` folder. You
may do this by cloning the repository or downloading a zip archive from the
[Releases Page](https://gitlab.com/foundrynet/dnd5e/-/releases).

## Community Contribution

See the [CONTRIBUTING](/CONTRIBUTING.md) file for information about how you can help this project.
