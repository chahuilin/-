下面使用的是JDK自带的类，没有引用任何第三方jar包。

    package com.xingbook.zxott.domian;

    import java.io.ByteArrayOutputStream;
    import java.io.OutputStream;
    import java.io.StringReader;

    import javax.xml.bind.JAXBContext;
    import javax.xml.bind.JAXBException;
    import javax.xml.bind.Marshaller;
    import javax.xml.bind.Unmarshaller;
    import javax.xml.bind.annotation.XmlRootElement;

    @XmlRootElement(name="xml")  
    public class UnifiedOrderResponse {
        /**
        * 返回状态码 SUCCESS/FAIL
        */
        private String return_code;

        /**
        * 返回信息
        */
        private String return_msg;

        /**
        * 公众账号ID
        */
        private String appid;

        /**
        * 商户号
        */
        private String mch_id;

        /**
        * 设备号
        */
        private String device_info;

        /**
        * 随机字符串
        */
        private String nonce_str;

        /**
        * 签名
        */
        private String sign;

        /**
        * 业务结果
        */
        private String result_code;

        /**
        * 错误代码
        */
        private String err_code;

        /**
        * 错误代码描述
        */
        private String err_code_des;

        /**
        * 交易类型
        */
        private String trade_type;

        /**
        * 预支付交易会话标识
        */
        private String prepay_id;

        /**
        * 二维码链接
        */
        private String code_url;
        
        @XmlElement(name = "return_code")
        public String getReturn_code() {
            return return_code;
        }

        public void setReturn_code(String return_code) {
            this.return_code = return_code;
        }

        public String getReturn_msg() {
            return return_msg;
        }

        public void setReturn_msg(String return_msg) {
            this.return_msg = return_msg;
        }

        public String getAppid() {
            return appid;
        }

        public void setAppid(String appid) {
            this.appid = appid;
        }

        public String getMch_id() {
            return mch_id;
        }

        public void setMch_id(String mch_id) {
            this.mch_id = mch_id;
        }

        public String getDevice_info() {
            return device_info;
        }

        public void setDevice_info(String device_info) {
            this.device_info = device_info;
        }

        public String getNonce_str() {
            return nonce_str;
        }

        public void setNonce_str(String nonce_str) {
            this.nonce_str = nonce_str;
        }

        public String getSign() {
            return sign;
        }

        public void setSign(String sign) {
            this.sign = sign;
        }

        public String getResult_code() {
            return result_code;
        }

        public void setResult_code(String result_code) {
            this.result_code = result_code;
        }

        public String getErr_code() {
            return err_code;
        }

        public void setErr_code(String err_code) {
            this.err_code = err_code;
        }

        public String getErr_code_des() {
            return err_code_des;
        }

        public void setErr_code_des(String err_code_des) {
            this.err_code_des = err_code_des;
        }

        public String getTrade_type() {
            return trade_type;
        }

        public void setTrade_type(String trade_type) {
            this.trade_type = trade_type;
        }

        public String getPrepay_id() {
            return prepay_id;
        }

        public void setPrepay_id(String prepay_id) {
            this.prepay_id = prepay_id;
        }

        public String getCode_url() {
            return code_url;
        }

        public void setCode_url(String code_url) {
            this.code_url = code_url;
        }

        @Override
        public String toString() {
            return "UnifiedOrderResponse [return_code=" + return_code + ", return_msg=" + return_msg + ", appid=" + appid
                    + ", mch_id=" + mch_id + ", device_info=" + device_info + ", nonce_str=" + nonce_str + ", sign=" + sign
                    + ", result_code=" + result_code + ", err_code=" + err_code + ", err_code_des=" + err_code_des
                    + ", trade_type=" + trade_type + ", prepay_id=" + prepay_id + ", code_url=" + code_url + "]";
        }
        
        public static void main(String[] args) throws JAXBException {
            String xmlStr="<xml><return_code><![CDATA[SUCCESS]]></return_code> <return_msg><![CDATA[OK]]></return_msg> <appid><![CDATA[wx541feb86de2d4f76]]></appid> <mch_id><![CDATA[1431668402]]></mch_id> <nonce_str><![CDATA[j09UhL1NjGTsGfXJ]]></nonce_str> <sign><![CDATA[6CFB69E9FEAA7E9DD784201461242C64]]></sign> <result_code><![CDATA[SUCCESS]]></result_code> <prepay_id><![CDATA[wx201701161111017d271b0cc50251279917]]></prepay_id> <trade_type><![CDATA[NATIVE]]></trade_type> <code_url><![CDATA[weixin://wxpay/bizpayurl?pr=ucKXnpr]]></code_url> </xml>";
            JAXBContext context = JAXBContext.newInstance(UnifiedOrderResponse.class);  
            
            //xml字符串转对象
            Unmarshaller unmarshaller = context.createUnmarshaller();
            UnifiedOrderResponse bean = (UnifiedOrderResponse)unmarshaller.unmarshal(new StringReader(xmlStr));  
            System.out.println(bean.appid);
            
            //对象转xml字符串转
            Marshaller marshaller = context.createMarshaller();  
            OutputStream os=new ByteArrayOutputStream();
            marshaller.marshal(bean, os);  
            System.out.println(os.toString());
        }
    }
