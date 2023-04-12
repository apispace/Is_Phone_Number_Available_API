# APISpace 介绍

**本** **API** **服务由** **[APISpace（apispace.com）](https://www.apispace.com/?utm_source=github&utm_term=zaiwangzhuangtai)** **提供。**

APISpace 是 Eolink 旗下专业的 API 开放与交易平台，为广大企业以及个人开发者提供多维度、全方位的API接口，覆盖短信验证、天气查询、快递物流、OCR文字识别等海量 API 服务，帮助用户快速获取数据，降低获取数据的成本和难度，提升开发效率。

APISpace 提供15种开发语言的代码示例，分别是：

-   Java(OK HTTP)
-   HTTP
-   cURL
-   微信小程序
-   PHP(pecl_http)、PHP(cURL)
-   Python(http.client)、Python(Requests)
-   JavaScript(Jquery AJAX)、JavaScript(XHR)
-   NodeJS(Native)、NodeJS(Request)
-   Ruby(Net:Http)
-   Shell(Httpie)、Shell(cUrl)

  


# **手机在网状态**

传入手机号码，查询手机号在网状态，返回在网、在网不可用、不在网（销号/未启用/停机）等多种状态。支持移动、电信、联通手机号码。

**使用该产品前，您需要通过** **[https://www.apispace.com/eolink/api/zwsjmd/introduction](https://www.apispace.com/eolink/api/zwsjmd/introduction?utm_source=github&utm_term=zaiwangzhuangtai)** **申请** **API** **服务。**

本文档末尾提供了 Python(httpClient) 的调用代码示例，可以前往文档末尾查看。

更多代码示例：[https://www.apispace.com/eolink/api/zwsjmd/guidence/](https://www.apispace.com/eolink/api/zwsjmd/guidence/?utm_source=github&utm_term=zaiwangzhuangtai)



### 应用场景

#### **1. 话务中心电话营销**

手机号查询除去无效手机号节约时间成本费和提升工作效能。每一次无效语音通话的人工成本大概1.9元钱，查询接口只需其几十分之一。

  


#### **2. 群发短信**

企业通过查询并除去无效手机号，让营销推广信息内容发给每一个真正的顾客手机上，极大提高推送效率和转化率。

  


#### **3. 打击羊毛党**

手机号查询能够为互联网平台用户反作弊行为提供大数据分析能力，高效拦截羊毛党，减少损失提高运营能力。

  


#### **4. 网络平台运营**

互联网平台租运营过程中，会积累大量的注册用户，却不太了解每个ID的真假和实时状态，通过查询接口能精准筛选出活跃的目标用户，提高运营转化能力。

  


### 返回示例

```
{
    "chargeStatus": 1,
    "message": "成功",
    "data": {
        "result": {
            "provider": 1, // 返回号码当前归属的运营商，正数为非携号转网，负数为携号转网，具体如下： 非携号转网：1 移动、2 电信、3 联通； 携号转网：-1 移动、-2 电信、-3 联通。
            "status": 1 // 1.移动 1-->正常 2-->单停/停机/预销号 3-->在网不可用 4-->销号/未启用 2.电信 1-->正常 2-->停机 3-->未启用/在网但不可用 4-->销户/不在网 3.联通 1-->正常 2--> 停机 3--> 在网但不可用4-->销号/未启用
        },
        "msg": "请求成功",
        "code": "0",
        "fee": 1 // 是否收费 0：不收费 1：收费
    }, 
    "code": "200000"
}
```



### 服务保障

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a080abd15a534df18d47f0351edeeb24~tplv-k3u1fbpfcp-watermark.image?)
  


### **Python(http.client) 调用代码示例**


```
import http.client

conn = http.client.HTTPSConnection("eolink.o.apispace.com")

payload = "mobile=&encrypt=&encryptFields="

headers = {
    "X-APISpace-Token":"",
    "Authorization-Type":"apikey",
    "Content-Type":"application/x-www-form-urlencoded"
}

conn.request("POST","/zwsjmd/mobile_netstatus", payload, headers)

res = conn.getresponse()

data = res.read()

print(data.decode("utf-8"))



```
