- Pallete tem componentes para usar 
- Atributos permite editar um atributo  especifico 



MainActivity.java

```java
package com.example.calculadora;  
  
import androidx.appcompat.app.AppCompatActivity;  
  
import android.os.Bundle;  
import android.view.View;  
import android.widget.Button;  
import android.widget.EditText;  
import android.widget.TextView;  
import android.widget.Toast;  
  
public class MainActivity extends AppCompatActivity {  
  
    EditText editTextNumber;  
    EditText editTextNumber2;  
  
    Button adicaoButton;  
    Button subtracaoButton;  
    Button multiplicacaoButton;  
    Button divisaoButton;  
  
    TextView resultadoTextView;  
  
  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_main);  
  
        vincularComponentes();  
    }  
  
    private void vincularComponentes() {  
  
        editTextNumber = findViewById(R.id.editTextNumber);  
        editTextNumber2 = findViewById(R.id.editTextNumber2);  
  
        adicaoButton = findViewById(R.id.adicaoButton);  
        subtracaoButton = findViewById(R.id.subracaoButton);  
        multiplicacaoButton = findViewById(R.id.multiplicacaoButton);  
        divisaoButton = findViewById(R.id.divisaoButton);  
  
        resultadoTextView =findViewById(R.id.resultadotextView);  
    }  
  
    private void criarListeners(){  
        adicaoButton.setOnClickListener(evt -> adicionar());  
        subtracaoButton.setOnClickListener(evt -> subtrair());  
        multiplicacaoButton.setOnClickListener(evt -> multiplicar());  
        divisaoButton.setOnClickListener(evt -> dividir());  
    }  
  
    private void adicionar() {  
  
        String numero1String = editTextNumber.getText().toString();  
        String numero2String = editTextNumber2.getText().toString();  
  
        if(numero1String.isEmpty() || numero2String.isEmpty()){  
            Toast.makeText(this, "Digite dois números", Toast.LENGTH_LONG).show();  
            return;        }  
  
        double numero1 = Double.parseDouble(numero1String);  
        double numero2 = Double.parseDouble(numero2String);  
  
        double resultado = numero1 + numero2;  
  
        resultadoTextView.setText(String.valueOf(resultado));  
    }  
  
    private void subtrair() {  
  
    }  
  
    private void multiplicar() {  
  
    }  
  
    private void dividir() {  
  
    }  
}
```

activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>  
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    tools:context=".MainActivity">  
  
    <LinearLayout        android:layout_width="328dp"  
        android:layout_height="100dp"  
        android:layout_marginStart="16dp"  
        android:layout_marginEnd="16dp"  
        android:orientation="horizontal"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintHorizontal_bias="0.49"  
        app:layout_constraintStart_toStartOf="parent"  
        tools:layout_editor_absoluteY="251dp">  
  
        <Button            android:id="@+id/adicaoButton"  
            style="@style/Widget.AppCompat.Button"  
            android:layout_width="wrap_content"  
            android:layout_height="match_parent"  
            android:layout_weight="1"  
            android:text="+" />  
  
        <Button            android:id="@+id/subracaoButton"  
            style="@style/Widget.AppCompat.Button"  
            android:layout_width="wrap_content"  
            android:layout_height="100dp"  
            android:layout_weight="1"  
            android:text="-" />  
  
        <Button            android:id="@+id/multiplicacaoButton"  
            style="@style/Widget.AppCompat.Button"  
            android:layout_width="wrap_content"  
            android:layout_height="100dp"  
            android:layout_weight="1"  
            android:text="*" />  
  
        <Button            android:id="@+id/divisaoButton"  
            style="@style/Widget.AppCompat.Button"  
            android:layout_width="wrap_content"  
            android:layout_height="100dp"  
            android:layout_weight="1"  
            android:text="/" />  
    </LinearLayout>  
    <TextView        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_marginStart="16dp"  
        android:layout_marginTop="16dp"  
        android:text="Digite os dois números"  
        android:textSize="34sp"  
        app:layout_constraintBottom_toBottomOf="parent"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintHorizontal_bias="0.384"  
        app:layout_constraintStart_toStartOf="parent"  
        app:layout_constraintTop_toTopOf="parent"  
        app:layout_constraintVertical_bias="0.064" />  
  
    <LinearLayout        android:layout_width="328dp"  
        android:layout_height="100dp"  
        android:layout_marginStart="16dp"  
        android:layout_marginEnd="16dp"  
        android:orientation="horizontal"  
        android:visibility="visible"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintHorizontal_bias="0.49"  
        app:layout_constraintStart_toStartOf="parent"  
        tools:layout_editor_absoluteY="123dp"  
        tools:visibility="visible">  
  
        <EditText            android:id="@+id/editTextNumber"  
            android:layout_width="wrap_content"  
            android:layout_height="match_parent"  
            android:layout_weight="1"  
            android:ems="10"  
            android:inputType="number|numberDecimal|numberSigned" />  
  
        <EditText            android:id="@+id/editTextNumber2"  
            android:layout_width="wrap_content"  
            android:layout_height="100dp"  
            android:layout_weight="1"  
            android:ems="10"  
            android:inputType="number|numberDecimal|numberSigned" />  
    </LinearLayout>  
    <TextView        android:id="@+id/resultadotextView"  
        android:layout_width="318dp"  
        android:layout_height="242dp"  
        android:layout_marginStart="16dp"  
        android:layout_marginEnd="16dp"  
        android:textSize="34sp"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintStart_toStartOf="parent"  
        tools:layout_editor_absoluteY="395dp" />  
  
</androidx.constraintlayout.widget.ConstraintLayout>

```