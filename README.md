<p align="center">
	<img src="https://github.com/nocodeleaks/quepasa/raw/main/src/assets/favicon.png" alt="Quepasa-logo" width="100" />	
	<p align="center">Quepasa é um software de código aberto, totalmente gratuito, para troca de mensagens com a plataforma Whatsapp</p>
</p>
<hr />
<p align="left">
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP Chatwoot : </span>
	<a href="https://chat.whatsapp.com/CLKge3hmHmmBcIL04mBzmT" target="_blank">Grupo</a>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP Quepasa: </span>
	<a href="https://chat.whatsapp.com/Cv5WfmujRzE09yQ6hagYim" target="_blank">Grupo</a>
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP N8N: </span>
	<a href="https://telinkei.com/gp-n8n-zap" target="_blank">Grupo</a>
</p>
<hr />
<details>
<summary>Manual de Instalação Chatwoot</summary>
</br>
 ```bash
# Atualize sua máquina com os últimos pacotes
sudo apt update && apt upgrade -y

# Baixe o instalador automático do Chatwoot, execute a permisão no arquivo install.sh
wget https://get.chatwoot.app/linux/install.sh
chmod +x install.sh

# Inicie a instalação, digite "yes" para SSL, em seguida digite seu dominio e prossiga confimando com yes.
# Esse processo vai levar média ~ 15
./install.sh --install
```

Use as opções abaixo

yes

chatwoot.dominio.com.br

contato@dominio.com.br

yes para todos

### Alterando Idioma e ativando sua tela de cadastro

nano /home/chatwoot/chatwoot/.env

Altere a linha:

`DEFAULT_LOCALE=pt_BR` para `ENABLE_ACCOUNT_SIGNUP=true`

`systemctl daemon-reload && systemctl restart chatwoot.target`

Acesse: seudominio.com.br

Faça seu cadastro

### Habilitando configurações ocultas do Chatwoot no banco de dados PostgreSQL

```bash
sudo -i -u postgres psql

\c chatwoot_production

update installation_configs set locked = false;

\q
```

NOMES CHATWOOT TERMOS E POLITICA DE PRIVACIDADE

**Acesse super Admin**

https://seudominio.com.br/super_admin

Opção>installation_configs

```bash
LOGO
LOGO_THUMBNAIL
NOMES CHATWOOT:
```

### Alterando nomes na Plataforma

```bash
INSTALLATION_NAME
BRAND_NAME
TERMOS E POLITICA DE PRIVACIDADE
TERMS_URL
PRIVACY_URL
BRAND_URL
WIDGET_BRAND_URL
```

</details>

<details>
<summary>Manual de Instalação N8N</summary>

cd

sudo npm install -g n8n@0.230.3

npm install pm2 -g

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

sudo apt install ./google-chrome-stable_current_amd64.deb

sudo nano /etc/nginx/sites-available/n8n

```bash
server {
  server_name conector.dominio.com;
  
  underscores_in_headers on;

  location / {

   proxy_pass http://127.0.0.1:5678;
   proxy_pass_header Authorization;
   proxy_set_header Upgrade $http_upgrade;
   proxy_set_header Connection "upgrade";
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-Proto $scheme;
   proxy_set_header X-Forwarded-Ssl on; # Optional
   proxy_set_header X-Real-IP $remote_addr;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   proxy_http_version 1.1;
   proxy_set_header Connection "";
   proxy_buffering off;
   client_max_body_size 0;
   proxy_read_timeout 36000s;
   proxy_redirect off;
  }
  add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
  ssl_protocols TLSv1.2 TLSv1.3;
} 
  ```

sudo ln -s /etc/nginx/sites-available/n8n /etc/nginx/sites-enabled

sudo certbot --nginx

sudo service nginx restart

pm2 start n8n --cron-restart="0 0 * * *" -- start


### EXECUTE COMANDO ABAIXO PARA NÃO CAIR QUANDO REINICIAR A VPS

sudo pm2 startup ubuntu -u root && sudo pm2 startup ubuntu -u root --hp /root && sudo pm2 save

cd /root/.n8n

nano .env

Altere as seguintes variaveis baixo no arquivo .env

C8Q_QP_DEFAULT_USER=coloque email do Quepasa

C8Q_QP_BOTTITLE=Nome da Plataforma

C8Q_CW_PUBLIC_URL=domniochatwoot

C8Q_QP_CONTACT=Seu email

C8Q_QP_CONTACT=Seu email

WEBHOOK_URL=https://conector.dominio.com.br

N8N_EDITOR_BASE_URL=https://conector.dominio.com.br

```
C8Q_SINGLETHREAD=false
C8Q_QUEPASAINBOXCONTROL=1001
C8Q_GETCHATWOOTCONTACTS=1002
C8Q_QUEPASACHATCONTROL=1003
C8Q_CHATWOOTPROFILEUPDATE=1004
C8Q_POSTTOWEBCALLBACK=1005
C8Q_POSTTOCHATWOOT=1006
C8Q_CHATWOOTTOQUEPASAGREETINGS=1007
C8Q_CW_PUBLIC_URL="chatwoot.seudominio.com.br"
C8Q_QP_DEFAULT_USER="contato@seudominio.com.br"
C8Q_QP_BOTTITLE="Chatwoot"
C8Q_QP_CONTACT="contato@seudominio.com.br"
N8N_EDITOR_BASE_URL="https://conector.dominio.com.br"
WEBHOOK_URL="https://conector.dominio.com.br"
```

# Cria um link simbólico chamado ".env" que aponta para o arquivo "./.n8n/.env" no sistema de arquivos.
ln -s ./.n8n/.env .env

pm2 restart all --update-env

</details>

<details>
<summary>Manual de Instalação API Quepasa</summary>

cd

```
git clone https://github.com/nocodeleaks/quepasa /opt/quepasa-source
bash /opt/quepasa-source/helpers/install.sh
bash /opt/quepasa-source/helpers/update-workflows.sh
```

sudo nano /etc/nginx/sites-available/quepasa

```bash
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

sudo certbot --nginx

sudo service nginx restart

### Ativando SSL da API Quepasa

nano /opt/quepasa-source/src/.env

Adicione na linha 1 `APP_TITLE=Nome da Sua Empresa`

Alterar linha 2 de `WEBSOCKETSSL=false` para `WEBSOCKETSSL=true`

Alterar linha 8 para `REMOVEDIGIT9=true`

systemctl restart quepasa

</details>

<details>
<summary>Opcional 1: Instalação do Redis</summary>

sudo add-apt-repository ppa:redislabs/redis

sudo apt update

sudo apt install redis

sudo apt-get install libvips
</details>

<details>
<summary>Opcional 2: Para individualizar conversas entre agentes</summary>

```bash

mv /home/chatwoot/chatwoot/app/javascript/dashboard/components/ChatList.vue /home/chatwoot/chatwoot/app/javascript/dashboard/components/ChatList.vue.old

```

cd /home/chatwoot/chatwoot/app/javascript/dashboard/components

```bash

wget "https://raw.githubusercontent.com/EngajamentoFlow/quepasa/main/ChatList.vue"

```

Após alterações acima, rebuildar seu Chatwoot

sudo -i -u chatwoot

cd chatwoot

rake assets:precompile RAILS_ENV=production

exit

systemctl daemon-reload && systemctl restart chatwoot.target

</details>

### Instalações finalizadas ✅

chatwoot.seudominio.com.br

conector.seudominio.com.br

api.dominio.com.br/setup

Faça os cadastros em todos eles

### Configue os Worflows no N8N

Adicione os community nodes ao seu N8N

n8n-nodes-chatwoot

n8n-nodes-quepasa

Acesse opção Credenciais, adicione suas credenciais Postgres, salve.

reboot

Após colocar credenciais nos Worflows salve todos 

### Criando sua Caixa de Entrada

Envia uma mensagem para Contato Criado

Quepasa Control

/qrcode

Leia QRCODE

**Pronto tudo Funcionando** ✅😎
