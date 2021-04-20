# aux-seguranca

apt-get -y install openssl

openssl version

---------------------------
mkdir ~/CA <br>
cd ~/CA <br>
mkdir newcerts private <br>
echo '01' > serial <br>
touch index.txt <br>
---------------------------
wget https://tinyurl.com/opensslconfig -O openssl.cnf
---------------------------
openssl genrsa -aes256 -out private/CA.key 2048 <br>
senha "senha-ac"
---------------------------
cat private/CA.key ( ACHO Q NAO PRECISA)
---------------------------
openssl rsa -text -in private/CA.key | more <br>
openssl rsa -in private/CA.key -pubout -out CA.pub
---------------------------
Linha unica : <br>
openssl req -new -x509 -sha256 -key private/CA.key -extensions v3_ca -out CA_RAIZ.pem -days 3650 -config openssl.cnf
---------------------------

---------------------------


---------------------------

---------------------------

---------------------------


---------------------------

---------------------------

---------------------------

---------------------------

---------------------------

---------------------------

---------------------------

---------------------------

---------------------------
