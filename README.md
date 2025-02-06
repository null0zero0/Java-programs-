# Java-programs




1. Write a Java program that works as a simple calculator. Use a grid layout to arrange buttons for the digits and for the +, -,*, % operations. Add a text field to display the result. 

import java.awt.*;

import java.awt.event.*;

import javax.swing.*;



class SimpleCalculator extends JFrame implements ActionListener {

    JTextField display;

    double num1 = 0, num2 = 0;

    String operator = "=";



    SimpleCalculator() {

        // Set up the window

        setTitle("Calculator");

        setSize(300, 400);

        setLayout(new GridLayout(5, 1));



        // Display

        display = new JTextField();

        display.setHorizontalAlignment(SwingConstants.RIGHT);

        add(display);



        // Create number and operator buttons

        JPanel buttonPanel = new JPanel();

        buttonPanel.setLayout(new GridLayout(4, 4));

        String[] buttons = {"7", "8", "9", "/",

                            "4", "5", "6", "*",

                            "1", "2", "3", "-",

                            "0", ".", "=", "+"};



        for (String text : buttons) {

            JButton button = new JButton(text);

            button.addActionListener(this);

            buttonPanel.add(button);

        }

        add(buttonPanel);



        // Show window

        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        setVisible(true);

    }



    @Override

    public void actionPerformed(ActionEvent e) {

        String command = e.getActionCommand();



        if (command.chars().allMatch(Character::isDigit) || command.equals(".")) {

            display.setText(display.getText() + command);

        } else if (command.equals("=")) {

            num2 = Double.parseDouble(display.getText());

            switch (operator) {

                case "+": display.setText(String.valueOf(num1 + num2)); break;

                case "-": display.setText(String.valueOf(num1 - num2)); break;

                case "*": display.setText(String.valueOf(num1 * num2)); break;

                case "/": display.setText(num2 != 0 ? String.valueOf(num1 / num2) : "Error"); break;

            }

        } else {

            num1 = Double.parseDouble(display.getText());

            operator = command;

            display.setText("");

        }

    }



    public static void main(String[] args) {

        new SimpleCalculator();

    }

}





































2. Write a Java program that creates three threads. First thread displays “Good Morning” every one second, the second thread displays “Hello” every two seconds and the third thread displays “Welcome” every three seconds

import java.lang.*;

import java.io.*;



class ChildThread implements Runnable {

    Thread t;



    ChildThread(String name) {

        t = new Thread(this, name);

        t.start();

    }



    public void run() {

        for (int i = 1; i <= 5; i++) {

            try {

                if (t.getName().equals("First Thread")) {

                    Thread.sleep(1000);

                    System.out.println(t.getName() + ": Good Morning");

                } else if (t.getName().equals("Second Thread")) {

                    Thread.sleep(2000);

                    System.out.println(t.getName() + ": Hello");

                } else {

                    Thread.sleep(3000);

                    System.out.println(t.getName() + ": Welcome");

                }

            } catch (InterruptedException e) {

                System.out.println(t.getName() + " is interrupted");

            }

        }

    }

}



class ThreeThreads {

    public static void main(String args[]) {

        ChildThread one = new ChildThread("First Thread");

        ChildThread two = new ChildThread("Second Thread");

        ChildThread three = new ChildThread("Third Thread");

    }

}









3. Write a java program that simulates a traffic light. The program lets the user select one of three lights: red, yellow, or green. When a radio button is selected, the light is turned on, and only one light can be on at a time No light is on when the program starts 

import javax.swing.*;

import javax.swing.event.*;

import java.awt.*;

import java.awt.event.*;

class TrafficLightSimulator extends JFrame implements ItemListener {

    JLabel lbl1, lbl2;

    JPanel nPanel, cPanel;

    CheckboxGroup cbg;

    public TrafficLightSimulator() {

        setTitle("Traffic Light Simulator");

        setSize(600,400);

        setLayout(new GridLayout(2, 1));

        nPanel = new JPanel(new FlowLayout());

        cPanel = new JPanel(new FlowLayout());

        lbl1 = new JLabel();

        Font font = new Font("Verdana", Font.BOLD, 70);

        lbl1.setFont(font); 

        nPanel.add(lbl1);

        add(nPanel);

        Font fontR = new Font("Verdana", Font.BOLD, 20);

        lbl2 = new JLabel("Select Lights");

        lbl2.setFont(fontR);

        cPanel.add(lbl2);

        cbg = new CheckboxGroup();

        Checkbox rbn1 = new Checkbox("Red Light", cbg, false);

        rbn1.setBackground(Color.RED);

        rbn1.setFont(fontR);

        cPanel.add(rbn1);

        rbn1.addItemListener(this);

        Checkbox rbn2 = new Checkbox("Orange Light", cbg, false);

        rbn2.setBackground(Color.ORANGE);

        rbn2.setFont(fontR);

        cPanel.add(rbn2);

        rbn2.addItemListener(this);

        Checkbox rbn3 = new Checkbox("Green Light", cbg, false);

        rbn3.setBackground(Color.GREEN); 

        rbn3.setFont(fontR);

        cPanel.add(rbn3);

        rbn3.addItemListener(this);

        add(cPanel);

        setVisible(true);

        // to close the main window

        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    }

    // To read selected item 

    public void itemStateChanged(ItemEvent i) {

        Checkbox chk = cbg.getSelectedCheckbox();

        String str=chk.getLabel();

        char choice=str.charAt(0);

        switch (choice) {

        case 'R':lbl1.setText("STOP");

                 lbl1.setForeground(Color.RED);

                 break;

        case 'O':lbl1.setText("READY");

                 lbl1.setForeground(Color.ORANGE);

                 break;

        case 'G':lbl1.setText("GO");

                 lbl1.setForeground(Color.GREEN);

                 break;

        }

    }

    // main method

    public static void main(String[] args) {

        new TrafficLightSimulator();

    }

}



































4. Write a Java Program to Implement Hello world program using servlets.

Create, configure, and run a Java Servlet and JSP application using Eclipse IDE and Apache Tomcat.

Materials Needed

•	Java Development Kit (JDK)

•	Apache Tomcat Server

•	Eclipse IDE for Java EE Developers

Step 1: Set Up Your Environment

1. Install JDK: Ensure the Java Development Kit (JDK) is installed on your machine.

2.Install Apache Tomcat: Download and install Apache Tomcat from the Apache Tomcat   website.

3.Install Eclipse IDE: Download and install Eclipse IDE for Java EE Developers from the Eclipse website.

Step 2: Configure Tomcat in Eclipse

1.Open Eclipse: Launch the Eclipse IDE.

2.Open the Servers View: If the "Servers" tab is not visible, go to Window > Show View > Servers.

3.Add New Server:

•Right-click in the "Servers" view and select New > Server.

•Choose Apache > Tomcat v9.0 Server (or the version you installed) and click Next.

•Browse to the directory where you installed Tomcat and select it.

•Click Finish.

Step 3: Create a Dynamic Web Project

 1Create New Project:

•Go to File > New > Dynamic Web Project.

•Enter a project name (e.g., HelloServletApp).

•Ensure the Target Runtime is set to the Tomcat server you configured.

•Click Finish.

Step 4: Create the Servlet

1.Create a New Servlet:

•Right-click on the src folder in your project (e.g., HelloServletApp/src).

•Select New > Servlet.

•Enter the class name (e.g., HelloServlet) and package name (e.g., com.example).

•Click Finish.

2.Edit the Servlet Code:

•Open the HelloServlet.java file that was created.

•Replace the generated code with the following code

package com.example;

import java.io.IOException;

import javax.servlet.ServletException;

import javax.servlet.annotation.WebServlet;

import javax.servlet.http.HttpServlet;

import javax.servlet.http.HttpServletRequest;

import javax.servlet.http.HttpServletResponse;



@WebServlet("/HelloServlet")

public class HelloServlet extends HttpServlet {

    protected void doGet(HttpServletRequest request, HttpServletResponse response)

            throws ServletException, IOException {

        response.getWriter().println("Hello, Servlets!");

    }

}

Step 5: Create the JSP Page

1.Create a New JSP File:

•Right-click on the WebContent folder in your project (e.g., HelloServletApp/WebContent).

•Select New > JSP File.

•Name the file index.jsp and click Finish.

2.Edit the JSP Code:

•Open the index.jsp file that was created.

•Replace the generated code with the following code:









<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<html>

<head>

    <title>My First JSP Page</title>

</head>

<body>

    <h1>Welcome to JSP!</h1>

    <%

        String name = "Guest";

        out.println("Hello, " + name);

    %>

</body>

</html>

Step 6: Run the Application

1.Run on Server:

•Right-click on your project (e.g., HelloServletApp).

•Select Run As > Run on Server.

•Choose the Tomcat server you configured and click Finish.

























5. Write a Java Program to Create Thread using Interface and class. 

// Implementing the Runnable interface

class MyRunnable implements Runnable {

    @Override

    public void run() {

        for (int i = 0; i < 5; i++) {

            System.out.println("Runnable Thread: " + i);

            try {

                Thread.sleep(500); // Sleep for 500 milliseconds

            } catch (InterruptedException e) {

                System.out.println("Runnable Thread interrupted");

            }

        }

    }

}



// Extending the Thread class

class MyThread extends Thread {

    @Override

    public void run() {

        for (int i = 0; i < 5; i++) {

            System.out.println("Thread Class: " + i);

            try {

                Thread.sleep(500); // Sleep for 500 milliseconds

            } catch (InterruptedException e) {

                System.out.println("Thread Class interrupted");

            }

        }

    }

}



public class ThreadExample {

    public static void main(String[] args) {

        // Creating a thread using Runnable interface

        MyRunnable myRunnable = new MyRunnable();

        Thread thread1 = new Thread(myRunnable);

        

        // Creating a thread by extending Thread class

        MyThread thread2 = new MyThread();



        // Starting both threads

        thread1.start();

        thread2.start();



        // Wait for threads to finish

        try {

            thread1.join();

            thread2.join();

        } catch (InterruptedException e) {

            System.out.println("Main thread interrupted");

        }



        System.out.println("Both threads have finished execution.");

    }

}





















































6. Write a Java program that handles all mouse events 40-42 and shows the event name at the centre of the window when a mouse event is fired. (Use adapter classes).

import java.awt.*;

import java.applet.*;

import java.awt.event.*;

/*<applet code="MouseDemo" width=300 height=300>

</applet>*/

public class MouseDemo extends Applet implements MouseListener,MouseMotionListener

{

int mx=0;

int my=0;

String msg="";

public void init()

{

addMouseListener(this);

addMouseMotionListener(this);

}

public void mouseClicked(MouseEvent me)

{

mx=20;

my=40;

msg="Mouse Clicked";

repaint();

}

public void mousePressed(MouseEvent me)

{

mx=30;

my=60;

msg="Mouse Pressed";

repaint();

}

public void mouseReleased(MouseEvent me)

{

mx=30;

my=60;

msg="Mouse Released";

repaint();

}

public void mouseEntered(MouseEvent me)

{

mx=40;

my=80;

msg="Mouse Entered";

repaint();

}

public void mouseExited(MouseEvent me)

{

mx=40;

my=80;

msg="Mouse Exited";

repaint();

}

public void mouseDragged(MouseEvent me)

{

mx=me.getX();

my=me.getY();

showStatus("Currently mouse dragged"+mx+" "+my); 

repaint(); }

public void mouseMoved(MouseEvent me)

{

mx=me.getX();

my=me.getY();

showStatus("Currently mouse is at"+mx+" "+my);

repaint();

}

public void paint(Graphics g)

{

g.drawString("Handling Mouse Events",30,20);

g.drawString(msg,60,40);

}

}



















































7. Develop an Applet that receives an integer in one text field & compute its factorial value & returns it in another text filed when the button “Compute” is clicked.

import java.awt.*;

import java.lang.String;

import java.awt.event.*;

import java.applet.Applet;

public class Fact extends Applet implements ActionListener

{

String str;

Button b0;

 TextField t1,t2;

 Label l1;

 public void init(){

 Panel p=new Panel();

 p.setLayout(new GridLayout());

 add(new Label("Enter any Integer value"));

 add(t1=new TextField(20));

 add(new Label("Factorial value is: "));

 add(t2=new TextField(20));

 add(b0=new Button("compute"));

 b0.addActionListener(this);

 }

 public void actionPerformed(ActionEvent e)

 {

 int i,n,f=1;

 n=Integer.parseInt(t1.getText());

for(i=1;i<=n;i++)

 f=f*i;

 t2.setText(String.valueOf(f));

 repaint();

 }

}































8.  Write a Java Program to Implement proxy design pattern using java

public interface Image {

    void display();

}

public class RealImage implements Image {

    private String filename;

    public RealImage(String filename) {

        this.filename = filename;

        loadImageFromDisk();

    }

    private void loadImageFromDisk() {

        System.out.println("Loading " + filename);

    }

    @Override

    public void display() {

        System.out.println("Displaying " + filename);

    }

}

public class ProxyImage implements Image {

    private RealImage realImage;

    private String filename;

    public ProxyImage(String filename) {

        this.filename = filename;

    }

    @Override

    public void display() {

        if (realImage == null) {

            realImage = new RealImage(filename);

        }

        System.out.println("Proxy: Displaying " + filename);

        realImage.display();

    }

}

public class ProxyPatternDemo {

    public static void main(String[] args) {

        Image image1 = new ProxyImage("photo1.jpg");

        Image image2 = new ProxyImage("photo2.jpg");

        // Image will be loaded from disk

        image1.display();

        System.out.println();     

        // Image will not be loaded from disk again

        image1.display();

        System.out.println();     

        // Image will be loaded from disk

        image2.display();

    }

}


