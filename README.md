import java.awt.*;
import java.awt.event.*;
 import java.lang.Math; 
class JavaProject extends Frame implements ActionListener 
{
 
 TextField t;
 Panel p;
 
 String b[] = {"0","1", "2", "3", "4",
                 "5", "6", "7", "8",
                 "9", "+", "-", "*",
                 "/","%","C","X!" ,"=","1/X","x^y","√ ","3√","ln","log10","sin","cos","tan","e^x"};
                   
Button bt[] = new Button[28];   
 double num1 = 0.0, num2 = 0.0; double result = 0.0;
 String  op; 
 
 public JavaProject() 
 {
 
  Font f = new Font("Cambria", Font.BOLD, 28);
  t = new TextField(10);
t.setFont(f);
  p= new Panel();
  add(t, "North");
  add(p, "Center");
  
  p.setLayout(new GridLayout(4,4));
  
  for(int i=0; i < 28; i++) 
  {
   
   bt[i] = new Button(b[i]);
   bt[i].setFont(f);
   bt[i].addActionListener(this);

   bt[i].setBackground(Color.BLACK);

   bt[i].setForeground(Color.GRAY);
   p.add(bt[i]);
  
  }
  
  addWindowListener(new WindowAdapter(){
   
   public void windowClosing(WindowEvent we) {
    System.exit(0);
   }
  });
 }
 
 public void actionPerformed(ActionEvent ae
 ) 
 {
  
  String str = ae.getActionCommand();
  
  {
  
   
  if(str.equals("+")) 
   {       op = "+";
   num1 = Integer.parseInt(t.getText());
   t.setText("" );
}
   
  
  else if(str.equals("-")) 
  {
   op = "-";
   num1 = Integer.parseInt(t.getText());
   t.setText("" );
  }
  else if(str.equals("*")) {
   op = "*";
   
   num1 = Integer.parseInt(t.getText());
   
   t.setText("" );
   
  }
  else if(str.equals("/")) {
   op = "/";
   num1 = Integer.parseInt(t.getText());
   t.setText("");
  }
  else if(str.equals("x^y")) {
   op = "x^y";
   num1 = Integer.parseInt(t.getText());
   t.setText("");
  }
  else if(str.equals("%")) {
   op = "%";
   num1 = Integer.parseInt(t.getText());
   t.setText("");
  }
  else if(str.equals("√ ")) {
  
   num1 = Integer.parseInt(t.getText());
   result = Math.sqrt(num1);
   t.setText("ans = " +result+"");
  
  }
  else if(str.equals("X!"))
  {
   int fact=1;
   num1 = Integer.parseInt(t.getText());
     for(int i=1;i<=num1;i++)
     {    
      fact=fact*i;    
  }    
  
   result = fact;
   t.setText("ans = " +result+"");
  
  }
  else if(str.equals("1/X")) {
   
   num1 = Integer.parseInt(t.getText());
   result = 1/num1;
   if(num1==0)
   t.setText(" error! press C");
   else
   t.setText("ans " +result+"");
  }
  else if(str.equals("3√")) {
 
   num1 = Integer.parseInt(t.getText());
   result = Math.cbrt(num1);
  
  t.setText("ans = " +result+"");
  }
  else if(str.equals("ln")) {
  
   num1 = Integer.parseInt(t.getText());
   result = Math.log(num1);
   t.setText("ans = " +result+"");
  }
  else if(str.equals("log10")) {
   
   num1 = Integer.parseInt(t.getText());
   result = Math.log10(num1);
   t.setText("ans = " +result+"");
  }
   else if(str.equals("sin")) {
   
   num1 = Integer.parseInt(t.getText());
   result = Math.sin(num1);
   t.setText("ans = " +result+"");
  }
    else if(str.equals("cos")) {
  
   num1 = Integer.parseInt(t.getText());
   result = Math.cos(num1);
   t.setText("ans = " +result+"");
  }
  else if(str.equals("tan")) {
   
   num1 = Integer.parseInt(t.getText());
   result = Math.tan(num1);
   t.setText("ans = " +result+"");
  }
  else if(str.equals("e^x")) {
  
   num1 = Integer.parseInt(t.getText());
   result = Math.exp(num1);
   t.setText(result+"");
  }
  else if(str.equals("=")) {
   
   num2 = Integer.parseInt(t.getText());
   
   
   switch(op) 
   {
    
    case "+" : 
    result = num1 + num2;
    t.setText(num1+ op+ num2 +"=" +result + "");
   break;
    case "-" : result = num1 - num2;
    t.setText(num1+ op+ num2 +"=" +result + "");
     break;
    case "*": result = num1 * num2;
    t.setText(num1+ op+ num2 +"=" +result + "");
     break;
    case "/": result = num1 / num2;
    t.setText(num1+ op+ num2 +"=" +result + "");
     break;
     case"x^y": result=Math.pow(num1,num2);
     t.setText(num1+ "^"+ num2 +"=" +result + "");
     break;
      case"%": result=(num1/100)* num2;
      t.setText(num1+ op+ num2 +"=" +result + "");
     break;
    
   }
   
   result = 0.0;
  }
  else if(str.equals("C")) {
   
   t.setText("");
   num1 = num2 = result = 0.0;
  }
  else {
   t.setText(t.getText() + str);
  }
 }
}
 public static void main(String args[]) {
  
 JavaProject m = new JavaProject();
  m.setTitle("My Calculator");
  m.setSize(600,400);
  m.setVisible(true);
 }
}
