```ruby
软件的交互方式
控制台的交互方式
图形界面的交互方式

java使用的图形类主要在java.awt和javax.swing包中
java.awt和javax.swing
java.awt主要依赖系统的图形库的
java.swing使用到的图形类是sun自己实现的
不需要依赖系统的图形库



# 对话框

package demo;

import javax.swing.JDialog;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

import demo.util.Frameutil;

/*
JDiag(Dialog owner,String title,boolean modal)
title：标题
owner:所有者
modal:true*/

public class diag {
	public static void main(String[] args) {
		JFrame frame=new JFrame("窗体");
		
		JDialog dialog=new JDialog(frame,"对话框",true);
		
		Frameutil.initFrame(frame, 300, 400);
		/*dialog.setBounds(500,400,100,200);
		
		dialog.setVisible(true);*/
		
		//消息对话框
		JOptionPane.showMessageDialog(frame,"明天不用上课", "通知", JOptionPane.INFORMATION_MESSAGE);
		//警告对话框

		JOptionPane.showMessageDialog(frame,"明天不用上课", "警告", JOptionPane.WARNING_MESSAGE);
		//错误对话框

		JOptionPane.showMessageDialog(frame,"明天不用上课", "通知", JOptionPane.ERROR_MESSAGE);
	
	   //输入对话框

		String money=JOptionPane.showInputDialog("请输入你的年龄");//返回一个数据来接收。
		System.out.println(money);
		//确认框

		int num=JOptionPane.showConfirmDialog(frame,"你确定卸载吗");
		System.out.println(num);
		
		
		
	}
	

}

# 包文件



package demo.util;

import java.awt.Dimension;
import java.awt.Toolkit;//获取分辨率的类

import javax.swing.JFrame;

public class Frameutil {
//设置初始化窗体的工具类
public static void  initFrame(JFrame frame,int width,int height){
		
		Toolkit toolkit=	Toolkit.getDefaultToolkit();//返回一个默认工具类对象
		Dimension d=toolkit.getScreenSize();//获取分辨率.Dimension:尺寸，容积
	/*	System.out.println("y轴"+d.getHeight());
		System.out.println("x轴"+d.getWidth());*/
		int x=(int)d.getWidth();
		int y=(int)d.getHeight();
		frame.setBounds((x-width)/2,(y-height)/2,width,height);
		frame.setVisible(true);
		//设置窗体的关闭事件
		  frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
			
		}

}



```