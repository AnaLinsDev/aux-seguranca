# aux-seguranca

apt-get -y install openssl

openssl version

EXERCICIO A <br>
---------------------------
mkdir ~/CA <br>
cd ~/CA <br>
mkdir newcerts private <br>
echo '01' > serial <br>
touch index.txt <br>
wget https://tinyurl.com/opensslconfig -O openssl.cnf
openssl genrsa -aes256 -out private/CA.key 2048 <br>
senha "senha-ac"
cat private/CA.key ( ACHO Q NAO PRECISA)
openssl rsa -text -in private/CA.key | more <br>
openssl rsa -in private/CA.key -pubout -out CA.pub
---------------------------
---------------------------
---------------------------
EXERCICIO B <br>
Linha unica : <br>
openssl req -new -x509 -sha256 -key private/CA.key -extensions v3_ca -out CA_RAIZ.pem -days 3650 -config openssl.cnf
openssl x509 -in CA_RAIZ.pem -noout -text | more
---------------------------
---------------------------
---------------------------
EXERCICIO C <br>
mkdir ~/client-cert <br>
cd ~/client-cert <br>
Linha unica :  <br>
openssl req -new -nodes -out www.anaju.csr -keyout www.anaju.key -sha256 -config ~/CA/openssl.cnf <br>
openssl req -in www.anaju.csr -text -verify -noout  <br>
cp www.anaju.csr ~/CA  <br>
---------------------------
---------------------------
---------------------------
EXERCICIO D <br>
cd ~/CA <br>
Linha unica : <br>
openssl ca -out www.anaju.pem -keyfile private/CA.key -cert CA_RAIZ.pem -config ./openssl.cnf -infiles www.anaju.csr <br>
senha-ac <br>
cat serial <br>
cat index.txt <br>
ls -l newcerts <br>
more www.anaju.pem <br>
mv www.anaju.pem tmp.pem <br>
openssl x509 -in tmp.pem -out www.anaju.pem <br>
rm tmp.pem <br>
more www.anaju.pem <br>
openssl x509 -in www.anaju.pem -text -noout -purpose | more <br>

---------------------------
---------------------------
---------------------------
EXERCICIO E <br>
Linha unica : <br>
openssl s_server -accept 4433 -cert www.anaju.pem -key ~/client-cert/www.anaju.key -www <br>
https://localhost:4433 <br>
cp www.anaju.pem ~/client-cert <br>

---------------------------
---------------------------
---------------------------
EXERCICIO G <br>
sudo apt-get -y install nginx <br>
sudo mkdir /etc/nginx/certificate <br>
cd ~/client-cert <br>
sudo cp www.anaju.pem www.anaju.key /etc/nginx/certificate <br>
sudo gedit /etc/nginx/nginx.conf <br><br>

----
http {
# manter outras configurações existentes ...
# ...
# adicionar no fim, antes do final do bloco (linha com "}" )
# adicionado por anaju
server {
listen 443 ssl;
ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
ssl_certificate /etc/nginx/certificate/www.anaju.pem;
ssl_certificate_key /etc/nginx/certificate/www.anaju.key;
location / {
root /var/www;
}
}
} # final do bloco http { ... }
----
<br><br>

sudo service nginx restart <br>
"<<<>>>>''''////...
sudo su <br>
echo '<HTML><BODY><P>Parabens!. O certificado foi instalado com <br>
sucesso.</P></BODY></HTML>'> /var/www/index.html <br>
"



---------------------------
---------------------------
---------------------------
