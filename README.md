# Test_System
The automatic test system of the course. It includes the function of question bank management, problem making, correction and so on.

#该程序使用Android Studoi软件进行编程设计

#登陆界面布局设计
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="登录界面"
            android:textSize="30sp"
            android:gravity="center"
            android:layout_marginBottom="10dp"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="5dp">
            <TextView
                android:layout_width="120dp"
                android:layout_height="wrap_content"
                android:text="用户名："
                android:textSize="28sp"/>
            <EditText
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/edit1"
                android:background="@android:drawable/editbox_background"/>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="5dp">
            <TextView
                android:layout_width="120dp"
                android:layout_height="wrap_content"
                android:text="密    码："
                android:textSize="28sp" />
            <EditText
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/edit2"
                android:inputType="textPassword"
                android:background="@android:drawable/editbox_background"/>
        </LinearLayout>

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="5dp"
            android:text="请选择你的身份："
            android:textSize="28sp" />
        <RadioGroup
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_marginLeft="30dp"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="35dp">
            <RadioButton
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/student"
                android:text="学生"
                android:textSize="26sp"
                android:layout_marginRight="15dp"/>
            <RadioButton
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/teacher"
                android:text="教师"
                android:textSize="26sp"
                android:layout_marginRight="15dp"/>
            <RadioButton
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/manager"
                android:text="管理员"
                android:textSize="26sp"/>
        </RadioGroup>

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="若还没有注册账号，请先进行注册！"
            android:textSize="20sp"
            android:gravity="center"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:gravity="center"
            android:layout_marginTop="5dp"
            android:layout_marginBottom="5dp">
            <Button
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/bt1"
                android:text="登录"
                android:textSize="26sp"
                android:layout_marginRight="20dp"/>
            <Button
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/bt2"
                android:text="注册"
                android:textSize="26sp"
                android:layout_marginRight="20dp"/>
            <Button
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/bt3"
                android:text="退出"
                android:textSize="26sp" />
        </LinearLayout>

    </LinearLayout>
#登陆界面程序
package com.example.apple.myapplication;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;

public class MainActivity extends AppCompatActivity {
    EditText edit1,edit2;
    Button bt1,bt2,bt3;
    RadioButton r1,r2,r3;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        edit1=(EditText)findViewById(R.id.edit1);
        edit2=(EditText)findViewById(R.id.edit2);
        bt1=(Button)findViewById(R.id.bt1);
        bt2=(Button)findViewById(R.id.bt2);
        bt3=(Button)findViewById(R.id.bt3);
        r1=(RadioButton)findViewById(R.id.student);
        r2=(RadioButton)findViewById(R.id.teacher);
        r3=(RadioButton)findViewById(R.id.manager);
        bt1.setOnClickListener(new mClick());
        bt2.setOnClickListener(new mClick());
        bt3.setOnClickListener(new mClick());
    }
    class mClick implements View.OnClickListener{
        @Override
        public void onClick(View view) {
            Intent intent =new Intent();
            if (view==bt1){
                if (r1.isChecked()){
                    intent.setClass(MainActivity.this,student.class);
                    startActivity(intent);
                }
                if (r2.isChecked()){
                    intent.setClass(MainActivity.this,teacher.class);
                    startActivity(intent);
                }
                if (r3.isChecked()){
                    intent.setClass(MainActivity.this,manager.class);
                    startActivity(intent);
                }
            }
            if (view==bt2){
                intent.setClass(MainActivity.this,sign.class);
                startActivity(intent);
            }
            if (view==bt3){
                MainActivity.this.finish();
            }
        }
    }
}



#注册界面布局设计
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="注册界面"
        android:textSize="30sp"
        android:gravity="center"
        android:layout_marginBottom="10dp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="5dp">
        <TextView
            android:layout_width="140dp"
            android:layout_height="wrap_content"
            android:text="用 户 名："
            android:textSize="28sp" />
        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/et1"
            android:background="@android:drawable/editbox_background"/>
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="5dp">
        <TextView
            android:layout_width="140dp"
            android:layout_height="wrap_content"
            android:text="密      码："
            android:textSize="28sp" />
        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/et2"
            android:inputType="textPassword"
            android:background="@android:drawable/editbox_background"/>
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="5dp">
        <TextView
            android:layout_width="140dp"
            android:layout_height="wrap_content"
            android:text="确认密码："
            android:textSize="28sp" />
        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/et3"
            android:inputType="textPassword"
            android:background="@android:drawable/editbox_background"/>
    </LinearLayout>

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="请选择你的身份："
        android:textSize="28sp"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="5dp"/>
    <RadioGroup
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="30dp"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="35dp">
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/student"
            android:text="学生"
            android:textSize="26sp"
            android:layout_marginRight="15dp"/>
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/teacher"
            android:text="教师"
            android:textSize="26sp"
            android:layout_marginRight="15dp"/>
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/manager"
            android:text="管理员"
            android:textSize="26sp"/>
    </RadioGroup>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center">
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/b1"
            android:text="注册"
            android:textSize="26sp"/>
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/b2"
            android:text="返回登录"
            android:textSize="26sp"/>
    </LinearLayout>
    
</LinearLayout>
#注册界面程序
package com.example.apple.myapplication;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.Toast;

public class sign extends Activity {
    EditText et1,et2,et3;
    Button b1,b2;
    RadioButton r1,r2,r3;

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.sign);
        et1=(EditText)findViewById(R.id.et1);
        et2=(EditText)findViewById(R.id.et2);
        et3=(EditText)findViewById(R.id.et3);
        b1=(Button)findViewById(R.id.b1);
        b2=(Button)findViewById(R.id.b2);
        r1=(RadioButton)findViewById(R.id.student);
        r2=(RadioButton)findViewById(R.id.teacher);
        r3=(RadioButton)findViewById(R.id.manager);
        b1.setOnClickListener(new sClick());
        b2.setOnClickListener(new sClick());
    }
    class sClick implements View.OnClickListener{
        @Override
        public void onClick(View view) {
            if (view==b1){
                Toast.makeText(sign.this,"注册成功！",Toast.LENGTH_SHORT).show();
            }
            if (view==b2){
                Intent intent =new Intent();
                intent.setClass(sign.this,MainActivity.class);
                startActivity(intent);
            }
        }
    }
}



#学生考试界面布局设计
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="学生考试界面"
        android:textSize="30sp"
        android:gravity="center"
        android:layout_marginBottom="10dp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="5dp">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="科目选择："
            android:textSize="28sp"/>
        <Spinner
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/spinner"
            android:entries="@array/spinner" />
    </LinearLayout>
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn1"
        android:text="试题测试"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn2"
        android:text="试题分数查询"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn3"
        android:text="试题错题浏览"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn4"
        android:text="退出"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
</LinearLayout>
#学生考试界面程序（各按钮功能的程序，还未全部完成）
package com.example.apple.myapplication;

import android.app.Activity;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.view.View;
import android.widget.Button;

public class student extends Activity {
    Button btn1,btn2,btn3,btn4;
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.student);
        btn1=(Button)findViewById(R.id.btn1);
        btn2=(Button)findViewById(R.id.btn2);
        btn3=(Button)findViewById(R.id.btn3);
        btn4=(Button)findViewById(R.id.btn4);
        btn1.setOnClickListener(new btnClick());
        btn2.setOnClickListener(new btnClick());
        btn3.setOnClickListener(new btnClick());
        btn4.setOnClickListener(new btnClick());
    }
    class btnClick implements View.OnClickListener{
        @Override
        public void onClick(View v) {
            switch (v.getId()){
                case R.id.btn1:
                    break;
                case R.id.btn2:
                    break;
                case R.id.btn3:
                    break;
                case R.id.btn4:
                    student.this.finish();
                    break;
            }
        }
    }
}



#教师管理界面布局设计
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="教师管理界面"
        android:textSize="30sp"
        android:gravity="center"
        android:layout_marginBottom="10dp"/>
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn1"
        android:text="考生试卷结果查询"
        android:textSize="26sp"
        android:layout_gravity="center" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn2"
        android:text="查看考生信息"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn3"
        android:text="试题添加"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn4"
        android:text="试题删除"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn5"
        android:text="试题修改"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn6"
        android:text="退出"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
</LinearLayout>
#教师管理界面（各按钮功能的程序，还未全部完成）
package com.example.apple.myapplication;

import android.app.Activity;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.view.View;
import android.widget.Button;

public class teacher extends Activity {
    Button btn1,btn2,btn3,btn4,btn5,btn6;
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.teacher);
        btn1=(Button)findViewById(R.id.btn1);
        btn2=(Button)findViewById(R.id.btn2);
        btn3=(Button)findViewById(R.id.btn3);
        btn4=(Button)findViewById(R.id.btn4);
        btn5=(Button)findViewById(R.id.btn5);
        btn6=(Button)findViewById(R.id.btn6);
        btn1.setOnClickListener(new teacher.btnClick());
        btn2.setOnClickListener(new teacher.btnClick());
        btn3.setOnClickListener(new teacher.btnClick());
        btn4.setOnClickListener(new teacher.btnClick());
        btn5.setOnClickListener(new teacher.btnClick());
        btn6.setOnClickListener(new teacher.btnClick());

    }
    class btnClick implements View.OnClickListener{
        @Override
        public void onClick(View v) {
            switch (v.getId()){
                case R.id.btn1:
                    break;
                case R.id.btn2:
                    break;
                case R.id.btn3:
                    break;
                case R.id.btn4:
                    break;
                case R.id.btn5:
                    break;
                case R.id.btn6:
                    teacher.this.finish();
                    break;
            }
        }
    }
}



#管理员界面布局设计
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="管理员界面"
        android:textSize="30sp"
        android:gravity="center"
        android:layout_marginBottom="10dp"/>
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn1"
        android:text="试题管理"
        android:textSize="26sp"
        android:layout_gravity="center"/>
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn2"
        android:text="学生管理"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn3"
        android:text="教师管理"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/btn4"
        android:text="退出"
        android:textSize="26sp"
        android:layout_gravity="center"
        android:layout_marginTop="5dp" />
</LinearLayout>
#管理员界面（各按钮功能的程序，还未全部完成）
package com.example.apple.myapplication;

import android.app.Activity;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.view.View;
import android.widget.Button;

public class manager extends Activity {
    Button btn1,btn2,btn3,btn4;
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.manager);
        btn1=(Button)findViewById(R.id.btn1);
        btn2=(Button)findViewById(R.id.btn2);
        btn3=(Button)findViewById(R.id.btn3);
        btn4=(Button)findViewById(R.id.btn4);
        btn1.setOnClickListener(new manager.btnClick());
        btn2.setOnClickListener(new manager.btnClick());
        btn3.setOnClickListener(new manager.btnClick());
        btn4.setOnClickListener(new manager.btnClick());
    }
    class btnClick implements View.OnClickListener{
        @Override
        public void onClick(View v) {
            switch (v.getId()){
                case R.id.btn1:
                    break;
                case R.id.btn2:
                    break;
                case R.id.btn3:
                    break;
                case R.id.btn4:
                    manager.this.finish();
                    break;
            }
        }
    }
}
