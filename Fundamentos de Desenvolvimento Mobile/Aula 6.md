# SENSORES

- Um sensor é um dispositivo que responde a um estímulo físico - luz, som, temperatura, biometria, pressão e proximidade

# Sensor Manager

- O primeiro passo é instanciar a primeira classe apresentada, a SensorManager
- A grande maioria dos aplicativos Android será formada por algumas Activities, que podem ser imaginadas como telas do software
- A classe Activity possui um método chamado getSystemService, que permite que o desenvolvedor trabalhe com um serviço no nível de sistema operacional
- O serviço que será acessado depende do parâmetro que vamos passar para esse método
- A classe também fornece diversas constantes para acessar diferentes serviços
- Uma delas é a SENSOR_SERVICE, que faz com que o método citado retorne um SensorManager

```java
SensorManager mSensorManager = (SensorManager)
getSystemService(SENSOR_SERVICE);
```


# Conhecendo os sensores

- Apesar da API fornecer as classes necessárias para trabalhar com uma quantidade muito grande de sensores, é necessário que o smartphone possua estes hardwares
- Mas podemos criar uma rotina que verifique quais são os sensores disponíveis e quais as possibilidades que nos serão oferecidas

## Listando os sensores

```java
List<Sensor> lsita = mSensorManager.getSensorList(Sensor.TYPE_ALL);
Iterator<Sensor> iterator = lista.iterator();
String sensores = "... ";
while (iterator.hasNext()){
	Sensor sensor = iterator.next();
	sensores += " - " + sensor.getName() + "\n";
}

Toast.makeText(getApplicationContext(), sensores, Toast.LENGTH_LONG).show();
```

- Podemos mostrar essa variável no LogCat do Eclipse ou na tela do smartphone

# Utilizando os sensores

- Para a utilização de um sensor, basta recuperar uma instância do Sensor desejado
- O código a seguir recupera do device os sensores de luminosidade e proximidade:

```java
Sensor mluz = mSensoreManager.getDefaultSensor(Sensor.TYPE_LIGHT);
Sensor mProx = mSensorManager.getDefaultSensor(Sensor.TYPE_PROXIMITY);
```


- A SensorManager possui um método chamado getDefaultSensor, que retorna um a instância de Sensor e requere um parâmetro do tipo int
- Com as duas instâncias de sensor em mãos (mLuz, mProx), é possível registrar um listener para acompanhar possíveis mudanças nos valores de proximidade e da intensidade de luz ambiente

# Acelerômetro e lista de sensores

- Nesse exemplo, veremos como aplicar os comandos para determinar os devices disponíveis e a utilização do acelerômetro 
- Leitura dos valores dos 3 eixos - x,y,z do sensor de aceleração do device.

Leitura do eixo x (equivalente para y e x )
```xml
android:text = "Valor x:">
android:id = "@+id/tvValorX"
```

- Desses, os campos que possuem propriedade ID são os que apresentarão os dados e os demais serão utilizados como rótulos

Botão para apresentar os sensores do device

```xml
<Button
		android:layout_width = "match_parent"
		android:layout_height = "wrap_content"
		android:layout_gravity = "bottom"
		android:text = "Meus sensores"
		android:onClick = "btMeusSensoresOnClick"/>
```


# Sensores de proximidade e luminosidade

- Ao nos aproximarmos do aparelho, o microfone fica habilitado
- Em ambientes claros, o fundo do app fica preto. Em ambientes escuros, fica branco, para melhorar a usabilidade


```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:tools="http://schemas.android.com/tools"
	android: layout_width="match_parent"
	android: layout_height="match_parent"
	android:orientation="vertical"
	android:id="@+id/11Tela"
	tools:context=".GravadorPrincipalActivity">
	
	<ImageView
		android:id="@+id/ivMicrofone"
		android: layout_width="wrap_content"
		android: layout_height="wrap_content"
		android: layout_gravity-"center"
		android:src="@drawable/microfoneoff" />

</LinearLayout>

```

## Sensor de luminosidade

- Mede a quantidade de luz em um determinado ambiente 
- Para o app, se o valor for menor que 10, significa que a luz ambiente está abaixo de um nível aceitável definido pelo código
- Sendo assim, a cor de fundo da tela deve ser alterada para branco. Caso contrário, alterar para cor preta o fundo da tela

## Sensor de proximidade 
- Tem como objetivo indicar a  presença de um objeto a uma distância pré-definida
- O sensor de proximidade retorna apenas um valor, sendo assim, basta recuperar o valor no índice 0 do vetor values da SensorEvent
- Dependendo se a distância for maior que 10cm o usuário está distante do smartphone
- Caso contrário, ele estará próximo
- App serve para mostra par o usuário a distância para uma boa utilização do microfone 