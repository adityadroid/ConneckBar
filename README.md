# ConneckBar
ConneckBar lets you check current network state and display customisable snackbar upon receiving error.
You can also set custom action with the snackbar.

Step 1:
Copy ConneckBar.java and ConnectivityReceiver.java classes to your project. 

Step 2:
 Create a class MyApplication extending Application as shown :
 
```
import android.app.Application;

/**
 * Created by adi on 25/8/16.
 */
public class MyApplication extends Application {

    private static MyApplication mInstance;

    @Override
    public void onCreate() {
        super.onCreate();

        mInstance = this;


    }

    public static synchronized MyApplication getInstance() {
        return mInstance;
    }

    public void setConnectivityListener(ConnectivityReceiver.ConnectivityReceiverListener listener) {
        ConnectivityReceiver.connectivityReceiverListener = listener;
    }
}

```

Step 4:
Now in your manifest.xml add:
```

        <receiver
            android:name=".ConnectivityReceiver"
            android:enabled="true">
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
            </intent-filter>
        </receiver>
        
```
        
 and :
        
```
        
      android:name=".MyApplication"
      
```
 in the <application> tag.
      
and 
```
       <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
permissions.
      
     
Step 5:      
Now in you can call it in your activity class using any of these three constructors:
```
            public ConneckBar(Context currentApplicationContext, View view, String textToBeDisplayed, View.OnClickListener clickListener, int Duration , int colorBackGround, int colorText, int colorActionText );
            


            public ConneckBar(Context currentApplicationContext, View view, String textToBeDisplayed, View.OnClickListener clickListener, int Duration , int colorBackGround, int colorText);


            public ConneckBar(Context currentApplicationContext, View view, String textToBeDisplayed, View.OnClickListener clickListener, int Duration );
            
```
            Note: all the color arguments of type int expect a Color.COLORNAME(Ex: Color.WHITE) kind of argument.
            
            
            




