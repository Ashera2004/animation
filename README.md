# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Design xml files for all operations such as blink, rotate, move, slide, zoom, fade.

Step 6: Display the button operations in MainActivity file.

Step 7: Save and run the application


## PROGRAM:
Developed by: Siddarth A S
Registeration Number : 212224040316

### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="300dp"
        android:layout_height="300dp"
        android:layout_marginTop="32dp"
        android:contentDescription="@string/anim_image"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/anim" />

    <!-- Row 1 -->
    <Button
        android:id="@+id/BTNblink"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/blink"
        app:layout_constraintBottom_toTopOf="@+id/BTNmove"
        app:layout_constraintEnd_toStartOf="@+id/BTNrotate"
        app:layout_constraintHorizontal_chainStyle="spread"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView" />

    <Button
        android:id="@+id/BTNrotate"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/rotate"
        app:layout_constraintBottom_toBottomOf="@+id/BTNblink"
        app:layout_constraintEnd_toStartOf="@+id/BTNfade"
        app:layout_constraintStart_toEndOf="@+id/BTNblink"
        app:layout_constraintTop_toTopOf="@+id/BTNblink" />

    <Button
        android:id="@+id/BTNfade"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/fade"
        app:layout_constraintBottom_toBottomOf="@+id/BTNblink"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/BTNrotate"
        app:layout_constraintTop_toTopOf="@+id/BTNblink" />

    <!-- Row 2 -->
    <Button
        android:id="@+id/BTNmove"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/move"
        app:layout_constraintBottom_toTopOf="@+id/BTNstop"
        app:layout_constraintEnd_toStartOf="@+id/BTNslide"
        app:layout_constraintHorizontal_chainStyle="spread"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/BTNblink" />

    <Button
        android:id="@+id/BTNslide"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/slide"
        app:layout_constraintBottom_toBottomOf="@+id/BTNmove"
        app:layout_constraintEnd_toStartOf="@+id/BTNzoom"
        app:layout_constraintStart_toEndOf="@+id/BTNmove"
        app:layout_constraintTop_toTopOf="@+id/BTNmove" />

    <Button
        android:id="@+id/BTNzoom"
        android:layout_width="110dp"
        android:layout_height="60dp"
        android:backgroundTint="#987371"
        android:text="@string/zoom"
        app:layout_constraintBottom_toBottomOf="@+id/BTNmove"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/BTNslide"
        app:layout_constraintTop_toTopOf="@+id/BTNmove" />

    <Button
        android:id="@+id/BTNstop"
        android:layout_width="220dp"
        android:layout_height="60dp"
        android:layout_marginBottom="32dp"
        android:backgroundTint="#987371"
        android:text="@string/stop_animation"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### MainActivity.java
```java
package com.example.animations;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {
    ImageView imageView;
    Button blinkBTN, rotateBTN, fadeBTN, moveBTN, slideBTN, zoomBTN, stopBTN;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBTN = findViewById(R.id.BTNblink);
        rotateBTN = findViewById(R.id.BTNrotate);
        fadeBTN = findViewById(R.id.BTNfade);
        moveBTN = findViewById(R.id.BTNmove);
        slideBTN = findViewById(R.id.BTNslide);
        zoomBTN = findViewById(R.id.BTNzoom);
        stopBTN = findViewById(R.id.BTNstop);

        blinkBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add blink animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.blink);
                imageView.startAnimation(animation);
            }
        });

        rotateBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add rotate animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.rotate);
                imageView.startAnimation(animation);
            }
        });

        fadeBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add fade animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.fade);
                imageView.startAnimation(animation);
            }
        });

        moveBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add move animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.move);
                imageView.startAnimation(animation);
            }
        });

        slideBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add slide animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.slide);
                imageView.startAnimation(animation);
            }
        });

        zoomBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To add zoom animation
                Animation animation = AnimationUtils.loadAnimation(getApplicationContext(), R.anim.zoom);
                imageView.startAnimation(animation);
            }
        });

        stopBTN.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // To stop the animation going on imageview
                imageView.clearAnimation();
            }
        });
    }
}

```

### blink.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0" android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500" android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```

### fade.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />
    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />
</set>
```

### move.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```

### rotate.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />
    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />
</set>
```

### slide.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <scale android:duration="500"
        android:fromXScale="1.0" android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```

### zoom.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <scale
        android:fromXScale="0.5" android:toXScale="3.0"
        android:fromYScale="0.5" android:toYScale="3.0"
        android:duration="1000" android:pivotX="50%"
        android:pivotY="50%" >
    </scale>
    <scale
        android:startOffset="1000" android:fromXScale="3.0"
        android:toXScale="0.5" android:fromYScale="3.0"
        android:toYScale="0.5" android:duration="1000"
        android:pivotX="50%"
        android:pivotY="50%" >
    </scale>
</set>
```
## OUTPUT

<img width="1918" height="1141" alt="Screenshot 2026-08-22 131250" src="https://github.com/user-attachments/assets/0a55038e-5493-467f-a622-423d4cb9c4df" />
<img width="1918" height="1135" alt="Screenshot 2026-08-22 131221" src="https://github.com/user-attachments/assets/fd6350e5-7f76-4cdd-b985-085f3a50c218" />
<img width="1918" height="1138" alt="Screenshot 2026-08-22 131630" src="https://github.com/user-attachments/assets/d390390b-4629-4e7a-a2a3-8a4289e3cefe" />
<img width="1918" height="1141" alt="Screenshot 2026-08-22 131611" src="https://github.com/user-attachments/assets/09beddda-3223-4f76-89c4-2e5070a55bb1" />
<img width="1918" height="1141" alt="Screenshot 2026-08-22 131553" src="https://github.com/user-attachments/assets/5e5cff9b-c0b5-4ba3-9e6e-a1dc3063d86c" />
<img width="1918" height="1129" alt="Screenshot 2026-08-22 131507" src="https://github.com/user-attachments/assets/f0a219fa-1ba4-451b-aabd-9490092ade38" />



## RESULT

Thus a Simple Android Application to add animations: Move,blink,fade,clockwise,zoom,slide operations using Android Studio is developed and executed successfully.
