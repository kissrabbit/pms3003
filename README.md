# 攀藤PMS3003传感器


## 生成工程文件
    gradle idea

## 数字管脚定义
    数字式通过颗粒物浓度传感器.
    PMS2001,PMS2003,PMS3003数字管脚定义.
    主要输出为单位体积内各浓度颗粒物质量及个数(视具体型号).

|PIN        |定义         |说明         |电压         |
|----------:|-----------:|------------:|-----------:|
|PIN1       |VCC         |电源正5V      |-            |
|PIN2       |GND         |电源负        |-            |
|PIN3       |SET         |设置pin       |/TTL电 平@3.3V|
|PIN4       |RXD         |串口接收管脚   |/TTL电 平@3.3V|
|PIN5       |TXD         |串口发送管脚   |/TTL电 平@3.3V|
|PIN6       |RESET       |模块复位信号   |/TTL电 平@3.3V|
|PIN7/8     |NC          |悬空          |-            |

> **NOTE:**
> * 1针为控制信号接口,采用高低电平控制.
> * 2针为串行数据通信接口,采用通用异步收发协议(UART);
> * 所有电平均为3.3V TTL电平.



## 传输协议
    数字式通过颗粒物浓度传感器PMS2003, PMS3003传输协议

|数据         |功能                                 |
|------------:|-----------------------------------:|
|起始符1       |0x42(固定)                           |
|起始符2       |0x42(固定)                           |
|帧长度高八位 <br /> 帧长度低八位  |帧长度=2x9+2(数据+校验位)              |
|数据1高八位 <br /> 数据1低八位  |数据1表示PM1.0浓度(CF=1,标准颗粒物)单位ug/m3              |
|数据2高八位 <br /> 数据2低八位  |数据2表示PM2.5浓度(CF=1,标准颗粒物)单位ug/m3              |
|数据3高八位 <br /> 数据3低八位  |数据3表示PM10浓度(CF=1,标准颗粒物)单位ug/m3              |
|数据4高八位 <br /> 数据4低八位  |数据4表示PM1.0浓度(大气环境下)单位ug/m3              |
|数据5高八位 <br /> 数据5低八位  |数据5表示PM2.5浓度(大气环境下)单位ug/m3              |
|数据6高八位 <br /> 数据6低八位  |数据6表示PM10浓度(大气环境下)单位ug/m3              |
|数据7高八位 <br /> 数据7低八位  |数据7(保留) |
|数据8高八位 <br /> 数据8低八位  |数据8(保留) |
|数据9高八位 <br /> 数据9低八位  |数据9(保留) |
|数据和校验高八位<br /> 数据和校验低八位    |校验码=起始符1+起始符2+...+数据9低八位 |

> **NOTE:**
> * 串口默认波特率9600Kbps, 校验位:无, 停止位:1位, 共24个字节.
> * CF=1        根据美国TSI公司的仪器校准
> * 大气环境下   根据中国气象局的数据校准



