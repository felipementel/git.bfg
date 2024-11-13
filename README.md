## Para instalar o BFG Repo-Cleaner no Ubuntu, você pode seguir estes passos:

### Instale o Java:

1. O BFG Repo-Cleaner é um aplicativo Java, então você precisa do Java instalado. Se ainda não tiver, instale com o comando:

````bash
sudo apt update -y && apt upgrade -y
````
````bash
sudo apt install default-jre -y
````

### Baixe o arquivo JAR do BFG Repo-Cleaner:

Você pode baixar diretamente do site com o comando wget:

````bash
wget -O bfg.jar https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar
````

Para executar o BFG, use o comando:

````bash
java -jar bfg.jar
````

Mova para um diretorio compartilhado e seguro
````bash
sudo mv bfg.jar /usr/local/bin/
````

Crie um script de execução para o BFG:

Para tornar o comando mais fácil de usar, crie um pequeno script shell chamado bfg que executará o arquivo JAR com o Java. Crie o arquivo de script com o editor de sua preferência, como nano:

````bash
sudo nano /usr/local/bin/bfg
````

Adicione o seguinte conteúdo ao script:

No editor, adicione esta linha para que o script execute o bfg.jar:

````bash
#!/bin/bash
java -jar /usr/local/bin/bfg.jar "$@"
````
O "$@" permite que você passe argumentos para o comando bfg como faria normalmente.

Salve e feche o editor e, em seguida, torne o script executável com o comando:

````bash
sudo chmod +x /usr/local/bin/bfg
````

Atualize o PATH (se necessário):

Como o diretório /usr/local/bin já está incluído no PATH por padrão, você não precisará alterar as variáveis de ambiente. Caso tenha usado outro diretório, precisará adicioná-lo ao PATH no arquivo ~/.bashrc:

````bash
echo 'export PATH=$PATH:/usr/local/bin/bfg' >> ~/.bashrc
````
````bash
source ~/.bashrc
````

Executando o BFG Repo-Cleaner:
````bash
bfg --help
````
Por exemplo, se você quiser remover arquivos grandes do histórico do seu repositório Git, você pode rodar:

````bash
java -jar bfg.jar --strip-blobs-bigger-than 100M my-repo.git
````
(Onde my-repo.git é o seu repositório Git local.)


# Oficial Website
````
https://rtyley.github.io/bfg-repo-cleaner/
````
# GitHub (how to use)
````
https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#using-the-bfg
````
