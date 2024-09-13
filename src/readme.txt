docker build -t ronaldojssilva/imagem-caotica:v1 .

docker container run -d -p 8080:8080 ronaldojssilva/imagem-caotica:v1

docker scout quickview ronaldojssilva/imagem-caotica:v1

docker scout cves --format markdown ronaldojssilva/imagem-caotica:v1

docker scout quickview fs://.