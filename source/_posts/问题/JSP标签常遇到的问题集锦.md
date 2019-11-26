---
title: JSP标签常遇到的问题集锦
date: 2019-11-26 11:15:24
categories: 工具
---
## 在`form:input`属性中使用`<spring:message code='' />`

```jsp
<form:input path="effectiveDate" onchange="ckdate()" 
            cssClass="form-control input-sm form-date required" autocomplete="off"
            title="<spring:message code="AgreeQuantity.EffectiveDate"/>">
</form:input>
```

此时`title`属性值不能被识别。

修改后：

- 方案一

```jsp
<input id="effectiveDate" name="effectiveDate" onchange="ckdate()" 
            cssClass="form-control input-sm form-date required" autocomplete="off"
            title="<spring:message code="AgreeQuantity.EffectiveDate"/>">
</input>
```

- 方案二

```jsp
//这是相当于变量的传递
<spring:message code="AgreeQuantity.EffectiveDate" var="effectiveDate"/>

<form:input cssClass="required" cssErrorClass="error"
            id="effectiveDate" placeholder="${effectiveDate}">
</form:input>
```

[]: https://blog.csdn.net/u014291497/article/details/50332007	"如何在form:input中添加spring message code"

