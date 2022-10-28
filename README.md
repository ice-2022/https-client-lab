# https-client-lab

实验一个异步的支持https的客户端，使用原生nio和ssl库实现

## 说明

因为实验性质，只支持GET请求，主要验证https的客户端实现和异步http请求的实现

## 用例

```java
public class Main {
    public static void main(String[] args) throws InterruptedException {
        HttpClient client = new HttpClient();
        client.init();
        String url = "https://www.baidu.com";
        HttpRequest request = HttpRequestParser.parse(url);
        client.get(request, response -> {
            System.out.println(new String(response.getBody()));
        });
        // 测试时防止主线程结束
        Thread.sleep(1000);
    }
}
```
