docker build -t ronaldojssilva/imagem-caotica:v1 .

docker container run -d -p 8080:8080 ronaldojssilva/imagem-caotica:v1

docker scout quickview ronaldojssilva/imagem-caotica:v1

docker scout cves --format markdown ronaldojssilva/imagem-caotica:v1

docker scout quickview fs://.



subir imagem para o docker hub

docker push ronaldojssilva/imagem-caotica:v1

colocar a imagem no scout

docker scout repo enable --org ronaldojssilva ronaldojssilva/imagem-caotica

docker scout recommendations ronaldojssilva/imagem-caotica:v1

docker build -t ronaldojssilva/imagem-caotica:v2 --push .

docker scout compare --to ronaldojssilva/imagem-caotica:v1 ronaldojssilva/imagem-caotica:v2

docker scout recommendations ronaldojssilva/imagem-caotica:v3

docker scout cves ronaldojssilva/imagem-caotica:v3

docker scout cves --format markdown ronaldojssilva/imagem-caotica:v3

npm install

npm audit fix --force

docker scout cves fs://.

docker build -t ronaldojssilva/imagem-caotica:v4 --push .

history | grep build