<p align="center">
	<img src="https://github.com/nocodeleaks/quepasa/raw/main/src/assets/favicon.png" alt="Quepasa-logo" width="100" />	
	<p align="center">Quepasa é um software de código aberto, totalmente gratuito, para troca de mensagens com a plataforma Whatsapp</p>
</p>
<hr />
<p align="left">
	<img src="https://telegram.org/favicon.ico" alt="Telegram-logo" width="32" />
	<span>Grupo e Canal Telegram: </span>
	<a href="https://t.me/quepasa_api" target="_blank">Grupo</a>
	<span> || </span>
	<a href="https://t.me/quepasa_channel" target="_blank">Canal</a>
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP: </span>
	<a href="https://chat.whatsapp.com/Cv5WfmujRzE09yQ6hagYim" target="_blank">Grupo</a>
</p>
----------------------------------------------------------------------------
</p>

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>

**PIX CNPJ**

```
45959142000119	
```
----------------------------------------------------------------------------

**Manual de Instalação API Quepasa**

```
git clone https://github.com/nocodeleaks/quepasa /opt/quepasa-source
</p>
bash /opt/quepasa-source/helpers/install.sh
</p>
sudo nano /etc/nginx/sites-available/quepasa
```

</p>

```
server {

  server_name quepasa.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:31000;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    
    proxy_cache_bypass $http_upgrade;

  }

  }
```

sudo ln -s /etc/nginx/sites-available/quepasa /etc/nginx/sites-enabled
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>

----------------------------------------------------------------------------

**Ativando SSL da API Quepasa**

nano /opt/quepasa-source/src/.env
</p>
Alterar linha 1
</p>
WEBSOCKETSSL=false
</p>
para
</p>
WEBSOCKETSSL=true
</p>
systemctl restart quepasa
</p>

----------------------------------------------------------------------------

**Instalação Finalizadas**

</p>
quepa.dominio.com.br/setup
</p>
Faça os cadastros em todos eles
</p>

----------------------------------------------------------------------------

**Pronto tudo Funcionando**

----------------------------------------------------------------------------

**Comando atualizar API Quepasa**

su - quepasa
</p>
cd /opt/quepasa
</p>
git pull
</p>
exit
</p>
systemctl daemon-reload
</p>

----------------------------------------------------------------------------
----------------------------------------------------------------------------

**Versão Docker**

**Manual de Instalação ChatWoot via Docker**

----------------------------------------------------------------------------

git clone https://github.com/aireset/quepasa
</p>
cd quepasa/docker
</p>
nano .env
</p></p></p>
WEBSOCKETSSL=false # http or Https
</p></p>
para
</p></p>
WEBSOCKETSSL=true # http or Https
</p>

----------------------------------------------------------------------------

**Ativando SSL Quepasa**

</p>
sudo apt-get install nginx
</p>
cd /etc/nginx/sites-enabled
</p>
sudo nano /etc/nginx/sites-available/quepasa

</p>

```
server {

  server_name quepasa.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:31000;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    
    proxy_cache_bypass $http_upgrade;

  }

  }
```

sudo ln -s /etc/nginx/sites-available/quepasa /etc/nginx/sites-enabled
</p>
</p>
sudo apt-get install snapd
</p>
sudo snap install --classic certbot
</p>
sudo certbot --nginx
</p>
Coloque Email:
</p>
Y
</p>
Y
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>

----------------------------------------------------------------------------

*Comandos para Iniciar*

```
docker-compose build
docker-compose up -d
```
ou 

```
docker-compose up -d --build
```
</p>

----------------------------------------------------------------------------

**Instalação Finalizadas**

</p>
quepa.dominio.com.br/setup
</p>
Faça os cadastros em todos eles
</p>

----------------------------------------------------------------------------

**Pronto tudo Funcionando**

----------------------------------------------------------------------------
----------------------------------------------------------------------------

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>


**PIX CNPJ**

```
45959142000119	
```

----------------------------------------------------------------------------
