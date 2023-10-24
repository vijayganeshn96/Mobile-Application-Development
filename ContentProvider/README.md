# Ex.No:5 Create Your Own Content Providers to get Contacts details.


## AIM:

To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “contentprovider″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
## activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="148dp"
        android:text="Get contact"
        android:onClick="btnGetContactPressed"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.644" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## Main_Activity.java:
```
package com.example.phonecontact;

import androidx.annotation.RequiresApi;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

import android.Manifest;
import android.annotation.SuppressLint;
import android.content.ContentResolver;
import android.content.pm.PackageManager;
import android.database.Cursor;
import android.net.Uri;
import android.os.Build;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.util.Log;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    public void btnGetContactPressed(View v)
    {
        getPhoneContacts();
    }
    private void getPhoneContacts()
    {
        if(ContextCompat.checkSelfPermission(this, Manifest.permission.READ_CONTACTS)!=
        PackageManager.PERMISSION_GRANTED)
        {
            ActivityCompat.requestPermissions(this,new String[] {Manifest.permission.READ_CONTACTS},0);
        }

        ContentResolver cr = getContentResolver();
        Uri uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI;
        @SuppressLint({"NewApi", "LocalSuppress"}) Cursor cursor = cr.query(uri,null,null,null);
        Log.i("CONTACT_PROVIDER_DEMO0", "TOTAL # OF CONTACTS ::"+Integer.toString(cursor.getCount()));
        if (cursor.getCount() > 0)
        {
            while(cursor.moveToNext())
            {
                @SuppressLint("Range") String contactname = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));
                @SuppressLint("Range") String contactnumber = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));

                Log.i("CONTACT_PROVIDER_DEMO","CONTACT_NAME ::"+contactname+"PH # ::"+contactnumber);
            }
        }
    }
}
```
```
Program to print the text create your own content providers to get contacts details.
Developed by: Vijay Ganesh N
Registeration Number : 212221040177
```

## OUTPUT

![1](https://github.com/Anbuselvan04/Mobile-Application-Development/assets/119410896/2944fc0f-fef7-45a8-9963-82139296a888)
![2](https://github.com/Anbuselvan04/Mobile-Application-Development/assets/119410896/afeffd79-db9a-4245-b517-358eaed39a30)
![3](https://github.com/Anbuselvan04/Mobile-Application-Development/assets/119410896/86cb96be-d652-4ecc-b6fb-b6f8c46ddec9)



## RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
