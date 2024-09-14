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


ASSINATURA DE IMAGEM
    cosign generate-key-pair 
        soloquei essa chave(Secreta@1)
        posso alterar o nome dos arquivos das chaves se quiser com o comando abaixo
            cosign generate-key-pair --output-key-prefix minha-chave

    assinando a imagem
        docker build -t ronaldojssilva/imagem-assinada:v1 .
        docker push ronaldojssilva/imagem-assinada:v1
        assinar a imagem
            cosign sign --key cosign.key ronaldojssilva/imagem-assinada:v1
        posso adicionar parametros na assinatura
            cosign sign --key cosign.key -a proprietario="Ronaldo Silva" ronaldojssilva/imagem-assinada:v1

    verificar se a imagem esta assinada
        cosign verify --key cosign.pub ronaldojssilva/imagem-assinada:v1

    gerar uma imagem com mesma tag sem assinatura pra simular uma tentativa de quebrar a imagem 
        alterei p server.js colocando console.log("Código safado");
        gerar a imagem sem assinatura e sobe para o registry
            docker build --push -t ronaldojssilva/imagem-assinada:v1 .
        observar que no hub o hash da imagem v1 é diferente do assinado
        verificar novamente 
            cosign verify --key cosign.pub ronaldojssilva/imagem-assinada:v1