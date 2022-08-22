- 👋 Hi, I’m @Hambty
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Hambty/Hambty is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.*;
import java.util.ArrayList;


public class JTextFieldDemo implements ActionListener {
    JFrame jf = new JFrame();
    JPanel jp1=new JPanel();
    JPanel jp2=new JPanel();
    JPanel jp3=new JPanel();
    JTextField jf1=new JTextField(10);
    JPasswordField jp=new JPasswordField(10);

    void initICU () {
        //创建窗口

        jf.setSize(300, 200);//设置顶层容器JFrame的大小尺寸
        jf.setLocationRelativeTo(null);
        jf.setBackground(Color.BLUE);//设置JFrame的背景颜色
        jf.setLayout(new FlowLayout(FlowLayout.CENTER));//关键字并将其设置为流式布局
        jf.setTitle("欢迎使用!");//设置窗体名称
        jf.setResizable(false);//设置JFrame是否为用户可调节大小
        jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);//设置窗口的关闭行为

        //创建中间容器JPanel


        //创建基本容器JLabel,JTextField,JPasswordField
        JLabel jl1=new JLabel("用户名");
        JLabel jl2=new JLabel("密码");



        JButton jb1=new JButton("登录");
        JButton jb2=new JButton("退出");
        JButton jb3=new JButton("注册");
        //分别将基本容器放到需要的中间容器中，再将中间容器放到需要的顶层容器中
        jp1.add(jl1);  jp1.add(jf1);
        jp2.add(jl2);   jp2.add(jp);
        jp3.add(jb1);   jp3.add(jb3);jp3.add(jb2);
        jf.add(jp1);    jf.add(jp2);
        jf.add(jp3);

        jb1.addActionListener(this);
        jb2.addActionListener(this);
       jb3.addActionListener(this);
        jf.setVisible(true);}
    public static void main(String[] args) {
        JTextFieldDemo jt = new JTextFieldDemo();
        jt.initICU();

    }

public void actionPerformed(ActionEvent e){
        if(e.getActionCommand()=="退出"){
            System.exit(0);
        }
        else if(e.getActionCommand()=="注册"){
            Demo1 d=new Demo1();
            d.qqq();
        }
        else if(e.getActionCommand()=="登录") {

            try {
                BufferedReader fi = new BufferedReader(new FileReader("D:password.txt"));
                    String s="";
                    String[] arr = null;
                    while ((s =fi.readLine()) !=null) {
                       arr=s.split(",");
                    }
                    //String qwe = String.valueOf(fi.read());
                    //String[] string = qwe.split(",");
                    String b1 = jf1.getText();
                    String b2 = String.valueOf(jp.getPassword());
                    if (arr[0].equals(b1) && arr[1].equals(b2)) {//将账户与其对应
                        jf.setVisible(true);
                        Demo2 de=new Demo2();
                        de.MenuDemo();
                        jf.setVisible(false);
                        fi.close();
                    }
                    else{
                        JLabel JL=new JLabel("登录失败");
                        jf.add(JL);jf.setVisible(true);
                    }
                } catch (FileNotFoundException ex) {

            } catch (IOException ex) {
                ex.printStackTrace();
            }

        }
        }

    }
class Demo1 implements  ActionListener{
    JFrame jf1 = new JFrame();
    JTextField JT = new JTextField(10);
    JPasswordField jp = new JPasswordField(10);
    public  void qqq() {

        jf1.setSize(360, 200);//设置顶层容器JFrame的大小尺寸
        jf1.setLocationRelativeTo(null);
        jf1.setBackground(Color.BLUE);//设置JFrame的背景颜色
        jf1.setLayout(new FlowLayout(FlowLayout.CENTER));//关键字并将其设置为流式布局
        jf1.setTitle("注册新账号");//设置窗体名称
        jf1.setResizable(false);//设置JFrame是否为用户可调节大小

        JPanel jp1 = new JPanel();
        JPanel jp2 = new JPanel();
        JLabel jl1 = new JLabel("新账号");
        JLabel jl2 = new JLabel("新密码");
        JButton jb = new JButton("确定");




         // ArrayList<String> al=new ArrayList<String>();
        //al.add(String.valueOf(oo));al.add(String.valueOf(aa));

        jp1.add(jl1);
        jp1.add(JT);
        jp2.add(jl2);
        jp2.add(jp);
        jf1.add(jp1);
        jf1.add(jp2);
        jf1.add(jb);
        jb.addActionListener(this);
        jf1.setVisible(true);

    }
    public static void main(String[] args) {
        Demo1 demo1=new Demo1();
        demo1.qqq();

        }

  public void actionPerformed(ActionEvent e){

        if(e.getActionCommand()=="确定"){
            File file=new File("D:password.txt");
            char[] oo=jp.getPassword(); String aa=JT.getText();
            ArrayList<String> al=new ArrayList<String>();
            al.add(aa);al.add(String.valueOf(oo));

            try {
                file.createNewFile();
            FileWriter fw=new FileWriter(file);
                fw.write(al.get(0)+",");fw.write(al.get(1));
                fw.flush();
            fw.close();
            jf1.setVisible(false);
            } catch (IOException ex) {
                ex.printStackTrace();
            }
        }
  }
    }
class Demo2 extends JFrame implements ActionListener{
   public void MenuDemo(){
       setTitle("二手物品管理系统");
        JMenuBar jm=new JMenuBar();
        String []qqq={"业务功能一","业务功能二","业务功能三"};
       String []rrr={"添加","删除","查询"};
        JMenu []www=new JMenu[3];
       JMenuItem[]eee=new JMenuItem[3];
       for(int i=0;i<3;i++){
    www[i]=new JMenu(qqq[i]);
    jm.add(www[i]);
eee[i]=new JMenuItem(rrr[i]);
      www[i].add(eee[i]) ;
       }
      setJMenuBar(jm);
     eee[0].addActionListener(this);
       eee[0].addActionListener(this);
       eee[0].addActionListener(this);
     setSize(400,400);
setDefaultCloseOperation(EXIT_ON_CLOSE);
       setLocationRelativeTo(null);
setVisible(true);
   }

    public static void main(String[] args) {
        Demo2 de=new Demo2();
    de.MenuDemo();
   }
public void actionPerformed(ActionEvent e) {
if(e.getActionCommand()=="添加"){
JOptionPane jo=new JOptionPane();

}



}

}
