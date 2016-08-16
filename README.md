import java.awt.*;
 import java.awt.event.*;
 import java.awt.geom.Ellipse2D;
 import javax.swing.*;
 import java.awt.geom.Rectangle2D;
 import java.awt.image.BufferedImage;
 import javax.swing.border.*;

public class Bridges {
     private final JPanel gui = new JPanel(new BorderLayout(3, 3));
     private JPanel field = new JPanel();
     private JPanel[][] feld = new JPanel[25][25];
     private MyButton cb2;
     private JRadioButton Fehlende;
     private JButton Auto;
     private JButton Naechste;
     
     private void Display(){
         JFrame frame = new JFrame("Andreas Moser / Mat-Nr. 9574557");
         frame.add(gui);
         gui.setBorder(new EmptyBorder(5, 5, 5, 5));
         JToolBar tools = new JToolBar();
         tools.setFloatable(false);
         gui.add(tools, BorderLayout.PAGE_START);
         tools.add(new JButton("Datei"));
         Box box = Box.createVerticalBox();
         gui.add(box);
         JPanel Spielfeld = new JPanel(new GridLayout(25, 25));
         box.add(Spielfeld);
         gui.setVisible(true);
         
         
         
         for (int i = 0; i < 25; i++) {
             for(int j = 0; j < 25; j++){
                 cb2 = new MyButton();
                 cb2.setBorder(new LineBorder(Color.WHITE));
                 cb2.setBackground(Color.WHITE);
                 cb2.setPreferredSize(new Dimension( 20, 20 ));
                 feld[i][j] = cb2;
                 
                 GridBagConstraints cl;
                 int x = 0;
                 cl = new GridBagConstraints();
                 cl.gridy = 0;
                 feld[i][j].add(new JLabel(""+x), cl);
             }}
         
         for (int i = 0; i < 25; i++) {
             for (int j = 0; j < 25; j++) {
                 Spielfeld.add(feld[i][j]);
                 //GridBagConstraints cl;
                 //int x = 0;
                 //cl = new GridBagConstraints();
                 //cl.gridy = 0;
                 //feld[i][j].add(new JLabel(""+x), cl, JLabel.CENTER);
                     }}
         box.add(Box.createVerticalStrut(5));
         
         Fehlende = new JRadioButton("Anzahl fehlender Brücken anzeigen", false);
         Auto = new JButton("Automatisch lösen");
         Naechste = new JButton("Nächste Brücke");
         
         box.add(Box.createHorizontalStrut(1));
         box.add(Fehlende);
         box.add(Box.createVerticalStrut(5));
         Box box1 = Box.createHorizontalBox();
         box.add(box1);
         box1.add(Auto, BorderLayout.WEST);
         box1.add(Box.createHorizontalStrut(200));
         box1.add(Naechste, BorderLayout.EAST);
         
         Box box2 = Box.createHorizontalBox();
         box.add(box2);
         JLabel statusLabel = new JLabel("Das Rätsel ist noch nicht gelöst!");
         statusLabel.setHorizontalAlignment(SwingConstants.LEFT);
         box2.add(statusLabel, BorderLayout.WEST);
                 
         frame.setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
         frame.pack();
         frame.setMinimumSize(frame.getSize());
         frame.setVisible(true);
     }
     
     public static void main(String[] args) {
         new Bridges().Display();}
     
     class MyButton extends JPanel{
         public void paintComponent(Graphics g){
             int diameter = 12;
             super.paintComponent(g);
             Color redColor = new Color(255,51,51);
             g.setColor(redColor);
             
             g.fillOval((getWidth()-diameter)/2, (getHeight()-diameter)/2, diameter, diameter);}
                 }
 }
