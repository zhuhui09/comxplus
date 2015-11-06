# comxplus
隔壁comx的升级版,去除大部分的菜单,完全隔离内核层,还原终端程序本来的面貌

# 超级终端 -H [串口号] [串口参数] 

串口参数格式:波特率-校验方式-数据位长度-停止位
串口号为0-255,波特率上限为256000,校验方式为N O E M,N为无校验,O为奇校验,E为偶校验,M为标记校验,数据位长度为4-8,停止位为1,2
输入3时为1.5停止位.

示例:comx -H 2 115200-N-8-1

# 接收数据 -R [串口号] [串口参数] [文件路径]

串口参数格式同上,文件路径可以是相对路径也可以是绝对路径,当下位机发送Dst后开始保存数据,当下位机在开始保存数据后发送Ded上位机终止
保存数据,按下ESC后,会在再次收到段终止符时停止保存数据.段终止符为#,最后一个#和Ded都会被写入文件中

示例:comx -R 2 115200-N-8-1 Data.re

# 设置蓝牙 -A [串口号] [蓝牙类型]

蓝牙类型目前只支持HC-05,因此只需要填入05即可.注意:此项功能需要在外部电路就绪的情况下开启

示例:comx -A 2 05

# 解析阶跃响应 -P [文件路径] [基础参数]

文件路径同上
基础参数格式:此次测试的限幅值-此次测试的输入值-此次测试的采样周期(ms)
限幅值为设定的测试过程中输出量最大不超过的值,输入值为阶跃响应的输入值,采样周期以毫秒记,为传入上位机的相邻数据的间隔的时间

示例:comx -P PID.re 10000-4500-10
