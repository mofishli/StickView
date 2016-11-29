# StickView

仿照QQ的粘性气泡控件，简洁易用，

package com.example.zhouli.stickview;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

StickView stickView;
TextView tv;
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);
stickView= (StickView) findViewById(R.id.stick);

tv= (TextView) findViewById(R.id.text);
stickView.setdismissListener(new DismissListener() {
@Override
public void dismiss() {
stickView.setNum(0);
tv.setText("目前未读消息数目:0");
Toast.makeText(MainActivity.this, "成功删除！", Toast.LENGTH_SHORT).show();
}
});

stickView.setNum(1);
stickView.setSize(70);

}

public void setnum(View v){
EditText editText= (EditText) findViewById(R.id.edittext);
String string=editText.getText().toString();
if(!string.isEmpty()){
int num=Integer.parseInt(string);
tv.setText("目前未读消息数目:" + num);
stickView.setNum(num);
}
}
}
