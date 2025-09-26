---
layout: page
title: 联系我
permalink: /contact/
---

<form action="https://formspree.io/f/mdkwkyyy" method="POST" style="max-width:520px">
  <label>你的名字
    <input name="name" required>
  </label>
  <label>邮箱
    <input name="email" type="email" required>
  </label>
  <label>想说的话
    <textarea name="message" rows="5"></textarea>
  </label>

  <!-- 反垃圾：隐藏的蜜罐字段，正常用户不会填写 -->
  <input type="text" name="_gotcha" style="display:none">

  <!-- 可选：提交后跳转的感谢页 -->
  <!-- <input type="hidden" name="_next" value="https://你的域名/thanks.html"> -->

  <button type="submit">发送</button>
</form>
