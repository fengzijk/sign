# 验签工具 
## 简单,高效   不引入任何外部包 可使用于API以及接口




### 使用示例
 
### Latest Version: [![Maven Central](https://img.shields.io/maven-central/v/com.fengzijk/sign.svg)](https://search.maven.org/search?q=g:com.fengzijka:sign*)


``` xml
        <dependency>
            <groupId>com.fengzijk</groupId>
            <artifactId>sign</artifactId>
            <version>Latest Version</version>
        </dependency>
```




#### Object方式 加签验签


##### 继承验签基础类
~~~java

public class UserInfoDTO extends BaseSignDTO {
    /**
     * 姓名
     */
    private String username;

    /**
     * 昵称
     */
    private String nickname;

}
~~~

##### 加签验签
~~~ java


 // appid
String appId="fgdfgdg33ghfghf";
// APP秘钥 
String secretKey="jhghjffgdfgdgyy";

//对象 加签名
UserInfoDTO userInfoDTO= new UserInfoDTO();
userInfoDTO.setUsername("11111");
userInfoDTO.setNickname("test");
userInfoDTO.setAppId(appId);
// 加签类型
userInfoDTO.setSignType(SignatureUtils.SignType.MD5.name());
// 时间戳
userInfoDTO.setTimestamp(SignUtils.getTodayDateTime());
// 随机字符串
userInfoDTO.setNonce("hgghfgsdfdfsf");
// 设置签名
userInfoDTO.setSign(SignatureUtils.getSignV2(userInfoDTO,secretKey));

// 对象方式验签
boolean b = SignatureUtils.validateSignV2(userInfoDTO, secretKey);

System.out.println(b);
~~~
