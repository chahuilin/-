代码需要commons-codec-1.10.jar,maven依赖:

    <!-- https://mvnrepository.com/artifact/commons-codec/commons-codec -->
    <dependency>
        <groupId>commons-codec</groupId>
        <artifactId>commons-codec</artifactId>
        <version>1.10</version>
    </dependency>

java代码如下：

    package com.zhahuilin.commonDemo.commons_codec;

    import java.io.UnsupportedEncodingException;
    import java.net.URLDecoder;
    import java.net.URLEncoder;

    import org.apache.commons.codec.binary.Base64;
    import org.apache.commons.codec.digest.DigestUtils;

    public class Commons_codecTest {
        public static void main(String[] args) throws UnsupportedEncodingException {

            // MD5加密
            System.out.println(DigestUtils.md5Hex("1"));

            // SHA1
            System.out.println(DigestUtils.sha1Hex("1"));

            // SHA256
            System.out.println(DigestUtils.sha256Hex("1"));

            // BASE64编码
            System.out.println(new String(Base64.encodeBase64("1".getBytes())));

            // BASE64解码
            System.out.println(new String(Base64.decodeBase64("MQ==")));
            
            //URL编码
            System.out.println(URLEncoder.encode("http://www.oschina.net/search?scope=bbs&q=C语言", "UTF-8"));
            
            //URL解码
            System.out.println(URLDecoder.decode("http%3A%2F%2Fwww.oschina.net%2Fsearch%3Fscope%3Dbbs%26q%3DC%E8%AF%AD%E8%A8%80", "UTF-8"));
            
        }
    }
