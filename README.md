# Welcome to the Android Navigation-Drawer with Fragment!

ส่วนประกอบของ Navigation drawer มีทั้งหมด 4 อย่าง
1. Navigation Menu.
2. Navigation header.
3. ส่วนสมองที่ใช้ในการควบคุม navigation (Java file)
4. รูปที่จะใส่เข้าไปใน Menu (จะใส่หรือไม่ใส่ก็ได้)

ขั้นตอนการทำ Step by step ^w^

# step 1

มาเพิ่ม library ของ navigation กันก่อน
ดับเบิ้ลคลิกที่ Gradle Scripts จากนั้นเลือก build.gradle(Module:app)

![Image](https://drive.google.com/uc?id=1wN2pxEml2JVq7lg-rFj86o4V9cQD-MHq)
  
ให้ใส่สองบรรทัดนี้ลงไป
~~~~
dependencies{
    implementation "android.arch.navigation:navigation-fragment:1.0.0"
    implementation "android.arch.navigation:navigation-ui:1.0.0"
}
~~~~

หลังใส่สองบรรทัดข้างบนให้สังเกตุตรงมุมบนขวาของหน้าจะมีปุ่ม Sync now อยู่

### กดเลย!!!
![Image](https://drive.google.com/uc?id=16FFOiG1JHtl-oyJAJvzpvg6Pk319rW-p)

# Step 2

มาสร้าง Menu ให้กับ navigation กัน
กดไปที่ Tab RES ที่อยู่ทางซ้ายมือ
![Image](https://drive.google.com/uc?id=1lQSVyKNSbXrzXsHe1azULEYC9OQMPGRp)

\*ในรูปมีอยู่แล้ว เพราะสร้างเอาไว้แล้ว ^ ^\*

หลังจากนั้น คลิกขวา เลือก New แล้วต่อด้วย Android Resource Directory จะมีหน้าต่างโผล่ขึ้นมาให้ตั้งค่า

เลือกตามนี้เลย \*ส่วน Directory name จะชื่อว่าอะไรก็ได้\*
![Image](https://drive.google.com/uc?id=1SVUPYBwbivCDhDNFHRLgM92Qajwvbou-)

### กด OK แล้วลอ !!!

หลังจากที่โปรแกรม build เสร็จเรียบร้อบแล้ว ให้คลิกขวาที่ folder menu ที่สร้างไว้เมื่อกี้นี้เลือก New แล้วต่อด้วย Menu Resource File 

จะมีหน้าต่างโผล่ขึ้นมาแบบนี้ให้ตั้งค่า ส่วนชื่อจะตั้งว่าอะไรก็ได้ ^ ^ ในที่นี้ตั้ง nav_menu จะได้สื่อความหมายได้ตรงกับสิ่งที่กำลังจะสร้าง
![Image](https://drive.google.com/uc?id=1I58vg6855JmbV-mCakWLFDEd6GJ3GBSV)

### กด OK แล้วลอ !!!

หลังจากนั้น ก็จะได้หน้าต่าง Layout มา
![Image](https://drive.google.com/uc?id=1LoTN8AhFgFol6Bli70agp_o4hHBClf7m)

ให้มองข้างล่างจะมี Tab ระหว่าง Text กับ Design ให้เลือก Text เพื่อที่จะได้ง่ายต่อการสร้าง =w=

หลังจากที่เปลี่ยน Tab เป็น Text แล้วให้สังเกตุด้านขวาจะมี Tab Preview อยู่ถ้ายังไม่ได้เปิดให้เปิดเลย

## มาเริ่ม Code กันเลย !!
navigation drawer สามารถทำได้ 2 แบบคือ 1.แบบกดแล้วไม่มี Hover 2.แบบมี Hover ตาม menu ที่กด

ในตัวอย่างนี้จะทำแบบที่ 1
```xml
<menu ..... >
    <item
        android:id="@+id/menu_no1"
        android:title="Menu no.1"/>
    <item
        android:id="@+id/menu_no2"
        android:title="Menu no.2"/>
    <item
        android:id="@+id/menu_no3"
        android:title="Menu no.3"/>
    <item
        android:title="Communication">
        <menu>
            <item
                android:id="@+id/contact"
                android:title="Contact us"/>
        </menu>
    </item>
</menu>
```
ผลลัพท์ก็จะได้ออกมาหน้าตาประมาณนี้ **แต่อย่าพึ่งตกใจเพราะมันยังไม่เสร็จ!**
![Image](https://drive.google.com/uc?id=1Zr4Fb6pB2tuzKIkOvuwZjsHDOs_5XNcU)

### Menu เสร็จเรียบร้อย !! 

ต่อไปจะเป็นส่วน Header ของ navigation

# Step 3

ให้คลิกขวาที่ Folder Layout หลักจากนั้นเลือก New ต่อด้วย Android Resource File แล้วจะมีหน้าต่างโผล่ขึ้นมาให้ตั้งค่า

#### ตั้งค่าตามนี้เลย
![Image](https://drive.google.com/uc?id=1EE9A3ck_IlgzwPgbfha23lXqJaWnANFf)

### กด OK แล้วลอ !!!
หลังจากที่โปรแกรม Build เสร็จแล้ว

ให้มองข้างล่างจะมี Tab ระหว่าง Text กับ Design ให้เลือก Text เพื่อที่จะได้ง่ายต่อการสร้าง =w=

```xml
<LinearLayout
    ....
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="#2196F3"
    android:padding="16dp">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

    <ImageView
        android:id="@+id/nav_img"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@mipmap/ic_launcher_round" />

    <TextView
        android:id="@+id/nav_t1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:paddingTop="6dp"
        android:text="Navigation drawer"
        android:layout_below="@id/nav_img"
        android:textAppearance="@style/TextAppearance.AppCompat.Body1" />

    <TextView
        android:id="@+id/nav_t2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:paddingTop="6dp"
        android:text="version 1.0.0"
        android:layout_below="@id/nav_t1"
        android:textAppearance="@style/TextAppearance.AppCompat.Body1" />
        
    </RelativeLayout>
</LinearLayout>
```
จะได้หน้าตาออกมาประมาณนี้
![Image](https://drive.google.com/uc?id=1CM95I2GI-Kn-viKcNVWqqM8YZTqn5kGf)

### ต่อไป ได้เวลานำทุกอย่างมาประกอบเข้าด้วยกันแล้ว !!

# Step 4

หลังจากนั้นให้คลิก Folder ที่ MainActivity อยู่ 

![Image](https://drive.google.com/uc?id=1ixLmMWmaC7wjiW8L83zio7w0oVraEhag)

เลือก New ต่อด้วย Java class แล้วจะมีหน้าต่างโผล่ขึ้นมาให้ตั้งค่า

ตั้งต่าตามนี้เลย

![Image](https://drive.google.com/uc?id=1DbD2dJoNSS-t5Dnd_jjIwrSwxH4Ai-T_)

ตรงส่วน Subclass ให้พิมพ์คำว่า **Fragment** แล้วเลือกตามรูปเลย

### กด OK !!!

หลังจากนั้นก็ทำการสร้าง Layout ให้กับ Fragment1 โดยไปที่ Folder Layout คลิกขวา New ต่อด้วย Layout Resource File

ตรง Root element ให้เปลี่ยนเป็น Relativelayout แบบนี้

![Image](https://drive.google.com/uc?id=15JJdcYEqlchlwX6SG-zNZukGwp6aZuID)

### กด OK !!!

### Layout + Java file ของ Menu no.1 เสร็จแล้ว ให้ทำแบบนี้อีก 3 ครั้งสำหรับ No.2, No.3 และ Contact us

ไปที่ Folder values ดับเบิ้ลคลิกที่ styles.xml ตรง Parent เปลี่ยนเป็นตัวนี้ Theme.AppCompat.DayNight.NoActionBar

เพราะเราจะใช้ Tool bar ของเราเอง
```xml
<resources>
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.DayNight.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">#2196F3</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
</resources>
```
\* **ตรงส่วน colorPrimayDark สามารถเปลี่ยนสี เพื่อให้เหมือนกับสีของ Tool bar เราได้** \*

กลับมาที่ Layout (activity_main.xml) เราจะมาประกอบ navigation drawer กัน

ให้เปลี่ยนหัวข้างบนที่จากเดิมเป็น Constainlayout เป็น Drawerlayout 
```xml
<androidx.drawerlayout.widget.DrawerLayout
    .....
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">
    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="#2196F3"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
        app:popupTheme="@style/ThemeOverlay.AppCompat.Light"
        android:elevation="4dp"/>
    <FrameLayout
        android:id="@+id/fragment_container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
    </LinearLayout>
    
</androidx.drawerlayout.widget.DrawerLayout>
```
# Step 5

ให้ใส่ NavigationView เข้าไปใน Layout activity _main และ ใส่ Menu กับ Header

สุดท้าย Layout activity_main จะมี code ทั้งหมดแบบนี้
```xml
<androidx.drawerlayout.widget.DrawerLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/drawer_layout"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="#2196F3"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
        app:popupTheme="@style/ThemeOverlay.AppCompat.Light"
        android:elevation="4dp"/>

    <FrameLayout
        android:id="@+id/fragment_container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

    </LinearLayout>

    <com.google.android.material.navigation.NavigationView
        android:id="@+id/navigationView"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        app:headerLayout="@layout/nav_header"
        app:menu="@menu/nav_menu"/>

</androidx.drawerlayout.widget.DrawerLayout>
```
ลองกดเล่น แล้วเอาเม้าส์ลากตรงที่หน้าจอทางซ้ายออกมาก็จะเห็น Navigation drawer ของเราแล้ว

**แต่**มันควรจะมีปุ่มที่กดแล้ว navigation โผล่ออกมาเลย จริงไหม ?

### เราจะมาสร้างปุ่มที่ว่านั่นกัน !

ไปที่ Folder values ดับเบิ้ลคลิกที่ string.xml ให้เพิ่ม 2 บรรทัดนี้เข้าไป
```xml
<resources>
    .......
    <string name="navigation_draw_open">Open navigation drawer</string>
    <string name="navigation_draw_close">Close navigation drawer</string>
</resources>
```

กลับมาที่ Mainactivity.java 

```java
import androidx.appcompat.app.ActionBarDrawerToggle;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import androidx.drawerlayout.widget.DrawerLayout;
import androidx.fragment.app.FragmentManager;

import android.os.Bundle;
import android.view.MenuItem;

import com.google.android.material.navigation.NavigationView;

public class MainActivity extends AppCompatActivity implements NavigationView.OnNavigationItemSelectedListener {

    private DrawerLayout drawer;
    FragmentManager fragmentManager;
    NavigationView navigationView;
    Toolbar toolbar;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        fragmentManager = getSupportFragmentManager();
        navigationView = findViewById(R.id.navigationView);
        toolbar = findViewById(R.id.toolbar);
        drawer = findViewById(R.id.drawer_layout);

        setSupportActionBar(toolbar);
        ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(MainActivity.this,drawer,toolbar,
                R.string.navigation_draw_open,R.string.navigation_draw_close);
        drawer.addDrawerListener(toggle);
        toggle.syncState();
    }
}
```
หลังจากนั้นลองกดเล่นดู จะเห็นว่า มีปุ่นขึ้นมาให้กดแล้ว แถมตรง toolbar มีชื่อขึ้นมาให้้ด้วย เพราะว่าเราเพิ่มตัว

ActionBarDrawerToggle และ สั่งให้มันร้างตัวเองขึ้นมาที่ toolbar บน MainActivity หลังจากนั้น

ใช้คำสั่ง SyncState เพื่อทำให้ animation ของเจ้า toogle ตัวนี้เข้ากับการกดเข้าออกของ navigation ของเรา

**แต่!** Menu ที่อยู่ข้างในยังคลิกไม่ได้เลย ถึงส่วยสำคัญแล้ว เราจะมาทำให้มันคลิกแล้วเปลี่ยนหน้าได้กัน

# Step 6

### ยังอยู่ที่ MainActivity.java อยู่นะ

```java
import androidx.appcompat.app.ActionBarDrawerToggle;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import androidx.core.view.GravityCompat;
import androidx.drawerlayout.widget.DrawerLayout;
import androidx.fragment.app.FragmentManager;

import android.os.Bundle;
import android.view.MenuItem;

import com.google.android.material.navigation.NavigationView;

public class MainActivity extends AppCompatActivity implements NavigationView.OnNavigationItemSelectedListener {

    private DrawerLayout drawer;
    FragmentManager fragmentManager;
    NavigationView navigationView;
    Toolbar toolbar;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        fragmentManager = getSupportFragmentManager();
        navigationView = findViewById(R.id.navigationView);
        toolbar = findViewById(R.id.toolbar);
        drawer = findViewById(R.id.drawer_layout);

        setSupportActionBar(toolbar);
        navigationView.setNavigationItemSelectedListener(this);

        ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(MainActivity.this,drawer,toolbar,
                R.string.navigation_draw_open,R.string.navigation_draw_close);
        drawer.addDrawerListener(toggle);
        toggle.syncState();
    }

    @Override
    public boolean onNavigationItemSelected(MenuItem menuItem){
        switch (menuItem.getItemId()){

            case R.id.menu_no1:
                getSupportFragmentManager().beginTransaction().replace(R.id.fragment_container,new Fragment1()).addToBackStack(null).commit();
                break;

            case R.id.menu_no2:
                getSupportFragmentManager().beginTransaction().replace(R.id.fragment_container,new Fragment2()).addToBackStack(null).commit();
                break;

            case R.id.menu_no3:
                getSupportFragmentManager().beginTransaction().replace(R.id.fragment_container,new Fragment3()).addToBackStack(null).commit();
                break;

            case R.id.contact:
                getSupportFragmentManager().beginTransaction().replace(R.id.fragment_container,new     ContactFragment()).addToBackStack(null).commit();
                break;
        }
        drawer.closeDrawer(GravityCompat.START);
        return true;
    }

    @Override
    public void onBackPressed(){
        if(drawer.isDrawerOpen(GravityCompat.START)){
            drawer.closeDrawer(GravityCompat.START);
        }else {
            super.onBackPressed();
        }
    }
}
```
ทำการ Implement NavigationItemSelectedListener เข้ามาเพื่อดักฟัง ก็ตรงตัวไป =w= แต่ความหมายก็ตามนั้นเลย

ดักว่า User กำลังคลิกที่ Menu ไหนอยู่ ถ้าตรง Case ไหนก็ให้ทำการเปิด Menu หน้านั้นๆออกมา

### แต่!!! มันยังไม่เสร็จ เพราะฉะนั้นอย่างพึ่งกดเล่นนะ

เพราะว่า Fragment แต่ละอันของเรายังไม่มีอะไรที่จะ return กลับมาได้เลย

ไปที่ Fragment1.java

กด ctrl + o จะมีหน้าต่างโผล่ขึ้นมา ให้พิมพ์ว่า onCreateView 

### กด OK !!!

จะมี code โผล่ขึ้นมาให้อัตโนมัติ ให้ลบบรรทัด return ทิ้ง

แล้วใส่ตัวนี้เข้าไปแทน

```java
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;

public class Fragment1 extends Fragment {
    @Nullable
    @Override
    public View onCreateView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        return inflater.inflate(R.layout.fragment1_activity,container,false);
    }
}
```
ความหมายของบรรทัดที่แก้คือ ให้ทำการ return layout frangment1 โดนจะส่งไปที่ container(fragment_container) เพื่อเปลี่ยนหน้า

ทำแบบนี้กับ fragment ที่เหลือ แล้วก็ถ้ากดแล้วมีแต่หน้าสีขาวขึ้นมา อย่าตกใจเพราะ ไฟล์ Layout ของแต่ละ fragment 

เรายังไม่ได้เพิ่มอะไรเข้าไปให้เข้าไปที่ไฟล์ layout ของแต่ละอันแล้วลองใส่ TextView ดู หรือจะเอาตัวอย่างนี้ก็ได้

ไฟล์ทั้งหมดควรจะมีประมาณนี้นะ

![Image](https://drive.google.com/uc?id=1tiao6NXqv4PhDlCsBBSFf5AvqM3scrII)

# THE MOMENT OF TRUE

ลองกดเล่นได้เลย ^ ^

ขอบคุณที่สละเวลาอ่านครับ

**Created by Titiwat Kuarkamphun**
