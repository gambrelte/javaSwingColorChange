package com.company;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
public class Main {
    public static class ColorFactory extends JFrame {
        private JPanel TopPanel = new JPanel();
        private JPanel BottomPanel = new JPanel();
        private JPanel CenterPanel = new JPanel();
        private JLabel messageLabel;
        private JButton redButton = new JButton("Red");
        private JButton orangeButton = new JButton("Orange");
        private JButton yellowButton = new JButton("Yellow");
        JRadioButton greenRadioButton = new JRadioButton("Green");
        private JRadioButton blueRadioButton = new JRadioButton("Blue");
        private JRadioButton cyanRadioButton = new JRadioButton("Cyan");
        final int WINDOW_WIDTH = 500;
        final int WINDOW_HEIGHT = 300;

        public ColorFactory() {
            setTitle("Color Factory");
            messageLabel = new JLabel("Top Buttons Change The Panel Color And" + "Bottom Radio Buttons Change The Text Color.");
            setSize(WINDOW_WIDTH, WINDOW_HEIGHT);
            setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            getContentPane().setLayout(new BorderLayout());
            setLayout(new BorderLayout());
            JPanel TopPanel = new JPanel();
            buildTopPanel();
            add(TopPanel, BorderLayout.NORTH);
            buildBottomPanel();
            add(BottomPanel, BorderLayout.SOUTH);
            add(CenterPanel, BorderLayout.CENTER);
            CenterPanel.add(messageLabel);
            setVisible(true);
        }
        private void buildTopPanel() {
            add(TopPanel, BorderLayout.NORTH);
            TopPanel.setBackground(Color.WHITE);
            redButton.setBackground(Color.RED);
            orangeButton.setBackground(Color.ORANGE);
            yellowButton.setBackground(Color.YELLOW);
            //setLayout(new FlowLayout());
            redButton.addActionListener(new ButtonListener());
            orangeButton.addActionListener(new ButtonListener());
            yellowButton.addActionListener(new ButtonListener());
            TopPanel.add(redButton);
            TopPanel.add(orangeButton);
            TopPanel.add(yellowButton);
        }
        private void buildBottomPanel() {
            BottomPanel.add(greenRadioButton);
            BottomPanel.add(blueRadioButton);
            BottomPanel.add(cyanRadioButton);
            setLayout(new FlowLayout());
            BottomPanel.setBackground(Color.WHITE);
            greenRadioButton.setBackground(Color.GREEN);
            blueRadioButton.setBackground(Color.BLUE);
            cyanRadioButton.setBackground(Color.CYAN);
            greenRadioButton.addActionListener(new RadioButtonListener());
            blueRadioButton.addActionListener(new RadioButtonListener());
            cyanRadioButton.addActionListener(new RadioButtonListener());
        }
        private class ButtonListener implements ActionListener {
            public void actionPerformed(ActionEvent e) {
               if(e.getSource() == redButton){
                   CenterPanel.setBackground(Color.RED);
               }else if(e.getSource() == orangeButton){
                   CenterPanel.setBackground(Color.ORANGE);
               }else if(e.getSource() == yellowButton){
                   CenterPanel.setBackground(Color.YELLOW);
               }
            }
        }
        private class RadioButtonListener implements ActionListener {
            public void actionPerformed(ActionEvent e) {
                if (e.getSource() == greenRadioButton) {
                    messageLabel.setForeground(Color.GREEN);
                } else if (e.getSource() == blueRadioButton) {
                    messageLabel.setForeground(Color.BLUE);
                } else if (e.getSource() == cyanRadioButton) {
                    messageLabel.setForeground(Color.CYAN);
                }
            }
        }
    }
    public static void main(String[] args) {
        new ColorFactory();
    }
}
