# Ex.No:2b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1.Start the application.

2.Create the first Activity with an EditText to enter a number.

3.Create a Button to calculate the factorial.

4.Initialize the EditText and Button using findViewById().

5.Set an OnClickListener() for the Button.

6.Get the number entered by the user.

7.Create an Explicit Intent to navigate from MainActivity to SecondActivity.

8.Pass the entered number using putExtra().

9.Start the SecondActivity using startActivity().

10.Retrieve the number in SecondActivity using getIntent().getIntExtra().

11.Calculate the factorial of the given number.

12.Display the factorial result using TextView.

## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Mohamed Fazludeen
Registeration Number : 212225040240
*/
```
## MainActivity.java
```
package com.example.explicit;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;


import java.math.BigInteger;

public class MainActivity extends AppCompatActivity {
    EditText numberInput;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        numberInput = findViewById(R.id.editTextText);
    }
    public void newsScreen(View view) {
        String input = numberInput.getText().toString();
        if (input.isEmpty()) {
            Toast t = Toast.makeText(this, "Please enter a number", Toast.LENGTH_SHORT);
            t.show();
            return;
        }
        try {
            int n = Integer.parseInt(input);
            if (n < 0) {
                Toast.makeText(this, "Please enter a non-negative number", Toast.LENGTH_SHORT).show();
                return;
            }
            BigInteger factorial = calculateFactorial(n);

            Intent i = new Intent(MainActivity.this, MainActivity2.class);
            i.putExtra("RESULT", factorial.toString());
            startActivity(i);
        } catch (NumberFormatException e) {
            Toast.makeText(this, "Invalid number", Toast.LENGTH_SHORT).show();
        }
    }
    private BigInteger calculateFactorial(int n) {
        BigInteger result = BigInteger.ONE;
        for (int i = 2; i <= n; i++) {
            result = result.multiply(BigInteger.valueOf(i));
        }
        return result;
    }
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button"
        android:onClick="newsScreen"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="200dp"
        android:text="Calculate"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="168dp"
        android:ems="10"
        android:inputType="text"
        android:text=""
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity2.java
```
package com.example.explicit;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        TextView resultTextView = findViewById(R.id.resultTextView);
        String result = getIntent().getStringExtra("RESULT");

        if (result != null) {
            resultTextView.setText(result);
        }
    }
    public void homeScreen(View view) {
        Intent i = new Intent(getApplicationContext(), MainActivity.class);
        startActivity(i);
    }
}
```
## activity_main2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/resultTextView"
        android:layout_width="347dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="76dp"
        android:text="0"
        android:textAlignment="center"
        android:textSize="18sp"
        app:layout_constraintBottom_toTopOf="@+id/button2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="252dp"
        android:onClick="Back"
        android:text="Back"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
## OUTPUT

<img width="1917" height="1078" alt="Screenshot 2026-11-24 085409" src="https://github.com/user-attachments/assets/67806c9e-4040-42f6-aca8-5302443fe93b" />

<img width="1917" height="1077" alt="image" src="https://github.com/user-attachments/assets/4489a038-cd0b-4236-8c44-fc45fee21eea" />





## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


