# Proyecto-final
Aplicación para android

package com.example.estephani.juego;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;
import java.util.Random;
public class JuegoPpt extends AppCompatActivity {
    Button btnPiedra,btnPapel,btnTijera;
    TextView txtMarcador;
    ImageView ImgJugador,ImgCPU;
    int JugadorPuntaje=0;
    int CPUPuntaje=0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_juego_ppt);
        btnPiedra = (Button) findViewById(R.id.btnPiedra);
        btnPapel = (Button) findViewById(R.id.btnPapel);
        btnTijera = (Button) findViewById(R.id.btnTijera);
        txtMarcador = (TextView) findViewById(R.id.txtMarcador);
        ImgJugador = (ImageView) findViewById(R.id.ImgJugador);
        ImgCPU = (ImageView) findViewById(R.id.ImgCPU);
        btnPiedra.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                ImgJugador.setImageResource(R.drawable.piedra);
                String mensaje = turno("Piedra");
                Toast.makeText(JuegoPPT.this, mensaje, Toast.LENGTH_SHORT).show();
                txtMarcador.setText("Jugador: " + Integer.toString(JugadorPuntaje) + "CPU:  " + Integer.toString(CPUPuntaje));
            }
        });
        btnPapel.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                ImgJugador.setImageResource(R.drawable.papel);
                String mensaje = turno("Papel");
                Toast.makeText(JuegoPPT.this, mensaje, Toast.LENGTH_SHORT).show();
                txtMarcador.setText("Jugador: " + Integer.toString(JugadorPuntaje) + "CPU:  " + Integer.toString(CPUPuntaje));
            }
        });
        btnTijera.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                ImgJugador.setImageResource(R.drawable.tijera);
                String mensaje = turno("tijera");
                Toast.makeText(JuegoPPT.this, mensaje, Toast.LENGTH_SHORT).show();
                txtMarcador.setText("Jugador: " + Integer.toString(JugadorPuntaje) + "CPU:  " + Integer.toString(CPUPuntaje));
            }
        });
    }
    public String turno (String elejido) {
        String dispositivo_selecciono=" ";
        Random r=new Random();
        int dispos_selecciono_numero=r.nextInt(3) +1;
        if (dispos_selecciono_numero==1 ) {
            dispositivo_selecciono="Piedra";
        }else
        if (dispos_selecciono_numero==2){
            dispositivo_selecciono="Papel";
        }else
        if (dispos_selecciono_numero==3){
            dispositivo_selecciono="Tijera";
        }
        if (dispositivo_selecciono=="Piedra"){
            ImgCPU.setImageResource(R.drawable.piedra);
        }else
        if (dispositivo_selecciono=="Papel") {
            ImgCPU.setImageResource(R.drawable.papel);
        }else
        if (dispositivo_selecciono=="Tijera") {
            ImgCPU.setImageResource(R.drawable.tijera);
        }
        if (dispositivo_selecciono==elejido){
            return "Empatados";
        }
        else if (elejido=="Piedra"&&dispositivo_selecciono=="Tijera") {
            JugadorPuntaje++;
            return   "la piedra a roto tijera        Felicidades Ganaste";
        }
        else if (elejido=="Piedra"&&dispositivo_selecciono=="Papel") {
            CPUPuntaje++;
            return "Papel gana a piedra  Perdiste";
        }
        else if (elejido=="Tijera"&&dispositivo_selecciono=="Piedra") {
            CPUPuntaje++;
            return "Piedra rompe Tijera       Perdiste";
        }
        else if (elejido=="Tijera"&&dispositivo_selecciono=="Papel") {
            JugadorPuntaje++;
            return "Tijera corta Papel          Ganaste";
        }
        else if (elejido=="Papel"&&dispositivo_selecciono=="Piedra") {
            JugadorPuntaje++;
            return "Papel cubre la Piedra            Ganaste";
        }
        else if (elejido=="Papel"&&dispositivo_selecciono=="Tijera") {
            CPUPuntaje++;
            return "Tijera corta a Papel          Perdiste";
        }
        else return  " no seguro";
    }
}



Pantalla para el grafico
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="16dp"
    android:paddingLeft="16dp"
    android:paddingRight="16dp"
    android:paddingTop="16dp"
    tools:context=".JuegoPpt"
    >
    <TextView
        android:id="@+id/txtJugador"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Eleccion Del Jugador"
        android:layout_centerHorizontal="true"
        />
    <ImageView
        android:id="@+id/ImgJugador"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:layout_below="@id/txtJugador"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="10dp"
        android:background="@drawable/boxeo"
        />
    <TextView
        android:id="@+id/txtCPU"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Eleccion del CPU"
        android:layout_centerHorizontal="true"
        android:layout_below="@id/ImgJugador"
        android:layout_marginTop="10dp"
        />
    <ImageView
        android:id="@+id/ImgCPU"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:background="@drawable/boxeo"
        android:layout_below="@+id/txtCPU"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="10dp"
        />
    <TextView
        android:id="@+id/txtMarcador"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Puntaje:   Jugador:0     CPU: 0"
        android:layout_below="@+id/ImgCPU"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="10dp"
        />
    <Button
        android:id="@+id/btnPiedra"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Piedra"
        android:layout_below="@id/txtMarcador"
        android:layout_marginTop="10dp"
        />
    <Button
        android:id="@+id/btnPapel"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Papel"
        android:layout_below="@id/txtMarcador"
        android:layout_marginLeft="120dp"
        android:layout_marginTop="10dp"
        />
    <Button
        android:id="@+id/btnTijera"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Tijera"
        android:layout_below="@id/txtMarcador"
        android:layout_marginLeft="240dp"
        android:layout_marginTop="10dp"
        />
</RelativeLayout>


