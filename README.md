# Instalando JDK 8 no Linux Ubuntu
  
Baixe o arquivo .tar.gz no [site da Oracle](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html), depois renomeie ele para "jdk8.tar.gz" para ficar mais fácil.  
  
Navegue até a pasta /usr/lib:  
  
```cd /usr/lib```  
  
Crie uma pasta chamada "jvm":  
  
```sudo mkdir jvm```  
  
Depois vá até a pasta de Downloads, e execute o seguinte código para extrair o arquivo "jdk8.tar.gz" na pasta que acabamos de criar:  
  
```sudo tar -xvzf ~/Downloads/jdk8.tar.gz -C /usr/lib/jvm```  
  
Agora que o arquivo já foi extraído e está dentro da pasta /usr/lib/jvm, vamos adicionar as variáveis de ambiente PATH:  
  
```sudo gedit /etc/environment```  
  
Com o novo arquivo que abriu, adicione as seguinte variáveis:  
  
~~~
/usr/lib/jvm/jdk1.8.0_231/bin
/usr/lib/jvm/jdk1.8.0_231/db/bin
/usr/lib/jvm/jdk1.8.0_231/jre/bin
~~~  
  
O código não deve ser adicionado dessa forma, deve haver dois pontos entre cada variável, dessa forma:  
  
```/usr/lib/jvm/jdk1.8.0_231/bin:/usr/lib/jvm/jdk1.8.0_231/db/bin:/usr/lib/jvm/jdk1.8.0_231/jre/bin``` 
  
E esses códigos devem estar **dentro das aspas** que correspondem aos caminhos do PATH. Ou seja, não adicione no fim de tudo, adicione antes da última aspa, *lembre de colocar dois pontos antes de colar o código acima*.  
  
Depois de ter feito isso, agora vamos adicionar as outras variáveis de ambiente:  
  
**Os códigos abaixo devem ser colados DEPOIS das aspas do PATH, ou seja, pule linha**  
  
~~~
J2SDKDIR="/usr/lib/jvm/jdk1.8.0_231"
J2REDIR="/usr/lib/jvm/jdk1.8.0_231/jre"
JAVA_HOME="/usr/lib/jvm/jdk1.8.0_231"
DERBY_HOME="/usr/lib/jvm/jdk1.8.0_231/db"
~~~  
  
Depois de ter feito todo o passo anterior, digite:  
  
```sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0_241/bin/java" 0```  
**Vale lembrar que /usr/lib/jvm/jdk1.8.0_241/bin/java a parte do JDK (jdk1.8.0_241) vai variar de acordo com a sua versão. Como você sabe a versão/nome do arquivo? Simples, navegando até /usr/lib/jvm e conferindo!**  
  
Depois:  
  
```sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0_241/bin/javac" 0```  
**Lembre de conferir a versão do JDK e mudar essa parte no código antes de executá-lo**  
  
```sudo update-alternatives --set java /usr/lib/jvm/jdk1.8.0_241/bin/java```  
**O mesmo vale aqui**  
  
```sudo update-alternatives --set javac /usr/lib/jvm/jdk1.8.0_241/bin/javac```  
**O mesmo continua valendo aqui também, altere o código com a versão do seu JDK antes de executar o código**  
  
UFA! Depois de ter executado **todos** os códigos passados, vamos checar se o JDK foi instalado mesmo:  
  
Execute ```javac -version``` ou ```java -version``` e se o comando resultar algo como:  

~~~
java version "1.8.0_241"
Java(TM) SE Runtime Environment (build 1.8.0_241-b07)
Java HotSpot(TM) 64-Bit Server VM (build 25.241-b07, mixed mode)
~~~  
**Não precisa ser da mesma forma**  
Então o JDK foi instalado na sua máquina!  
  
[Para qualquer erro ou consulta acesse esse material - (INGLÊS)](https://www.javahelps.com/2015/03/install-oracle-jdk-in-ubuntu.html)  
