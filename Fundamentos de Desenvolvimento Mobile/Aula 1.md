# HISTÓRIA DO MOBILE

- A ideia de comunicação sem fio entre telefones surgiu na década de 1940.
- 04/1973 - primeira chamado de um telefone móvel 
- O primeiro celular funcional foi o Motorola DynaTAC 8000x, lançado em 1983.
- As primeiras gerações de telefones celulares eram pesadas e não portáteis.
- A segunda geração (década de 90) trouxe tamanhos e pesos mais aceitáveis, mas ainda eram caros.
	- . Traziam como novidade novos padrões de comunicação: TDMA, CDMA e GSM.
- O serviço de mensagens de texto (SMS) surgiu em 1993.
- A evolução incluiu telas coloridas, acesso à internet e recursos como câmeras e reprodução de MP3.
- Os smartphones são dispositivos com sistema operacional, suporte a redes sem fio, câmera, Bluetooth e muito mais.
- A tecnologia 5G oferece maior velocidade de conexão, suporte à Internet das Coisas (IoT) e contribui para a Indústria 4.0.
- A rede 5G promete maior produtividade, competitividade e avanços na digitalização.

**1G**
- Totalmente analógico.
- Permitia apenas chamadas de voz.

**2G**
- Digital.
- Possibilidade de enviar mensagens de texto (SMS).

**3G**
- Acesso à internet para navegar em sites, redes sociais e serviço de e-mail. - inferior a velocidade dos computadores 
- paginas WAP
- Possibilidade de assistir a vídeos de alta definição, jogos on-line e transmissões de vídeo.

**4G**
- Serviço de e-mail e troca de mensagens de áudio.
- Realizar chamadas de vídeo.

**5G**
- Internet das Coisas (IoT), com dispositivos interconectados.
- Maior velocidade de processamento.

# GLOSSÁRIO DO MOBILE 

## Nativo vs Híbrido

### Desenvolvimento de Aplicativos Nativos:

- Tradicional, usando linguagens específicas para cada sistema operacional (iOS, Android, Windows).
- Configurados especialmente para sistemas operacionais móveis específicos.
- Utiliza APIs e ferramentas específicas fornecidas pelos fabricantes (Google, Microsoft, Apple).

**Desenvolvimento Nativo para Android:**

- Linguagens Java ou Kotlin com o Android Studio.
- Uso do sistema de construção Gradle.
- Interface gráfica amigável.

**Desenvolvimento Nativo para iOS:**

- Requer Mac OS X.
- Utiliza XCode 5 e iOS 7 SDK.
- Possível uso de Swift como linguagem de programação.

### Desenvolvimento Híbrido:

- Usa um framework para desenvolvimento multiplataforma.
- Economia de recursos, aproveita o mesmo código-fonte para Android e iOS.
- Desvantagens incluem desempenho inferior, menor personalização e dependência da plataforma e conexão com a internet.

## Frameworks JavaScript para Desenvolvimento Mobile:

**jQuery Mobile:**

- Biblioteca JavaScript.
- Cria aplicativos multiplataforma com HTML5.
- Possui widgets que facilitam interações em telas sensíveis ao toque.
- Adequado para desenvolvedores web que desejam criar aplicativos híbridos.

**React Native:**

- Biblioteca JavaScript criada pelo Facebook.
- Desenvolvimento nativo para Android e iOS.
- Executa código JavaScript diretamente no dispositivo final.
- Usa JSX para renderizar interfaces de usuário.

**NativeScript:**

- Desenvolvimento de aplicativos móveis para iOS e Android.
- Utiliza linguagens não nativas, como JavaScript, C# ou Dart.
- Transforma o código em código nativo do sistema operacional.
- Permite o uso de interfaces de usuário independentes de plataforma.

**Xamarin:**

- Framework .NET da Microsoft.
- Desenvolvimento de aplicativos móveis nativos.
- Aproveita as APIs nativas de cada plataforma.
- Suporta C# e permite a interoperabilidade com Objective-C, Java e C++.

**Flutter:**

- Framework do Google.
- Desenvolvimento nativo para Android e iOS.
- Usa a linguagem Dart.
- Compila código em código nativo do dispositivo.
- Excelente desempenho e acesso direto aos recursos do dispositivo.

**Ionic:**

- Framework de código aberto.
- Desenvolvimento de aplicativos híbridos com HTML, CSS e JavaScript.
- Design simples e funcional.
- CLI facilita o gerenciamento de projetos.
- Adequado para criar aplicativos multiplataforma com facilidade.

## Front-End, Back-end, API

**Front-end:**

- Responsável pela parte visível e interativa de uma página web para o cliente.
- Envolve recursos gráficos, elementos de interface e parte da lógica de programação.
- Utiliza linguagens como HTML, CSS e JavaScript.
- HTML para estrutura.
- CSS para layout e estilo.
- JavaScript para interatividade e lógica.

**Back-end:**

- Parte mais robusta e complexa da lógica de programação de um site.
- Lida com a lógica do servidor.
- Responde às requisições dos clientes.
- Gerencia conexão com banco de dados, segurança e APIs.

**API (Application Programming Interface):**

- Interface de programação que permite a comunicação entre diferentes softwares.
- Define métodos e protocolos para solicitar e fornecer dados ou funcionalidades entre sistemas.
- Facilita a integração de aplicativos, permitindo que eles se comuniquem e compartilhem informações.
- Elimina a necessidade de entender a implementação interna de um sistema, tornando o desenvolvimento mais eficiente.
- Amplamente usada para criar, estender e conectar aplicativos, serviços e recursos diversos.
- Exemplos incluem API do Google Maps, API do Facebook para login, API de pagamento em comércio eletrônico, etc.
- Desempenha um papel fundamental na construção de ecossistemas de software e na automação de processos.


## Interação Humano-Computador mobile first

- Estratégia de design e desenvolvimento que prioriza a usabilidade em dispositivos móveis.
- Foco inicial no planejamento de aplicativos e sites para uso em smartphones.
- Motivado pelo aumento do acesso à internet por dispositivos móveis.
- Iniciativa incentivada pelo Google, que favorece sites "mobile-friendly" nos resultados de busca.
- Conceito popularizado por Luke Wroblewski, diretor de produto do Google, em 2011.
- Abordagem visa criar sites otimizados para dispositivos móveis antes de adaptá-los para desktop.
- Evita problemas de adaptação de elementos de design em telas menores.
- Desafios incluem espaço reduzido, conexões limitadas e uso de telas sensíveis ao toque.
- Enfatiza a importância da arquitetura de informação, usabilidade e acessibilidade.
- Versões desktop podem ser aprimoradas com informações adicionais após a versão mobile-first.

# ARQUITETURAS MÓVEIS ANDROID

- O Android é um sistema operacional móvel open source inicialmente desenvolvido pela Google.
- Possui uma arquitetura baseada na versão 2.6 do kernel Linux.
- Desenvolvimento das novas versões do Android é liderado pela Open Handset Alliance (OHA).
- A plataforma Android é baseada em Linux e possui várias camadas de software.
- Principais camadas incluem o Kernel do Linux, Camada de Abstração de Hardware (HAL), Android Runtime (ART), Bibliotecas C/C++ nativas e Estrutura da Java API.
- **Kernel do Linux** lida com funcionalidades de baixo nível, como gerenciamento de memória e segurança.
- **HAL** fornece interfaces padrão para o componentes de hardware do dispositivo.
- **ART** executa aplicativos em dispositivos Android 5.0 ou superiores e usa arquivos DEX de bytecode.
- **Bibliotecas C/C++ nativas** são usadas para implementar componentes do sistema, como ART.
- **Estrutura da Java API Framework** fornece recursos para desenvolvimento de aplicativos, incluindo
	- sistema de visualização rico e extensivo útil para programar a IU 
	- gerenciador de recursos 
	- gerenciador de notificações
	- Um gerenciador de atividade que gerencia o ciclo de vida
	- Provedores de conteúdo que permitem que aplicativos acessem dados de outros aplicativos
- O Android possui um conjunto de aplicativos principais para e-mail, envio de SMS, calendários, navegador de internet e contatos.

![[Pasted image 20230915103812.png]]


# ARQUITETURAS MÓVEIS IOS

- O sistema operacional da Apple é chamado iPhone Operation System (iOS).
- Baseado no Sistema Operacional MAC OS X e projetado para dispositivos móveis da Apple.
- Abstrai a comunicação entre hardware e aplicativos.
- A arquitetura do iOS possui quatro camadas distintas:
    - **Cocoa Touch**: Fornece ferramentas e infraestrutura para implementar eventos e aplicativos para a interface do iPhone.
    - **Media**: Oferece recursos de áudio e vídeo usando bibliotecas como OpenGLES e QuartzCore.
    - **Core Services**: Camada que disponibiliza serviços essenciais do sistema, como AdressBook, Core Location, CFNNetwork, Security, SQLite, etc.
    - **Core OS**: Camada do kernel do sistema, que inclui drivers e interfaces básicas do sistema.