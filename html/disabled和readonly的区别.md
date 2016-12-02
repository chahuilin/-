# 带有一个禁用输入字段的 HTML 表单

    <form action="form_action.asp" method="get">
        <p>First name: <input type="text" name="fname" /></p>
        <p>Last name: <input type="text" name="lname" disabled="disabled" /></p>
        <input type="submit" value="Submit" />
    </form>



# 带有两个文本字段和一个提交按钮的 HTML 表单：

    <form action="form_action.asp" method="get">
        Name:<input type="text" name="email" />
        Country:<input type="text" name="country" value="China" readonly="readonly" />
        <input type="submit" value="Submit" />
    </form>

readonly 属性规定输入字段为只读。字段不变灰，
disabled 属性规定应该禁用 input 元素。字段变灰，**拥有disabled属性的提交表单时是获取不到其值的**，而readonly则可以。