---
layout: default
title: 联系我
permalink: /contact/
---

<style>
/* —— 简洁表单样式（只影响本页） —— */
.contact-wrap{
  max-width: 720px; margin: 0 auto; padding: 12px;
}
.contact-card{
  background: #fff; border: 1px solid #e5e7eb; border-radius: 14px;
  box-shadow: 0 8px 24px rgba(0,0,0,.06); padding: 22px;
}
.contact-title{ margin: 0 0 6px; }
.contact-sub{ margin: 0 0 18px; color:#6b7280; }
.grid{ display:grid; grid-template-columns: 1fr 1fr; gap: 12px; }
@media (max-width: 640px){ .grid{ grid-template-columns: 1fr; } }
.label{ display:block; font-weight:600; margin-bottom:6px; color:#111827; }
.input, .textarea{
  width:100%; border:1px solid #e5e7eb; border-radius:12px; padding:12px 14px;
  font: inherit; background:#fff; color:#111827; transition:box-shadow .15s,border-color .15s;
}
.input:focus, .textarea:focus{
  outline: none; border-color:#22c55e; box-shadow:0 0 0 4px rgba(34,197,94,.15);
}
.textarea{ min-height:140px; resize:vertical; }
.actions{ display:flex; gap:10px; align-items:center; margin-top:10px; }
.btn{
  appearance:none; border:0; background:#22c55e; color:#0b1222; font-weight:700;
  padding:12px 18px; border-radius:12px; cursor:pointer; box-shadow:0 10px 20px rgba(34,197,94,.25);
}
.btn:hover{ filter:brightness(0.95); }
.note{ color:#6b7280; font-size:14px; }
.success{ background:#ecfdf5; border:1px solid #a7f3d0; color:#065f46; padding:10px 12px; border-radius:10px; }
.error{ background:#fef2f2; border:1px solid #fecaca; color:#991b1b; padding:10px 12px; border-radius:10px; }
</style>

<div class="contact-wrap">
  <div class="contact-card">
    <h2 class="contact-title">给我发个消息吧</h2>
    <p class="contact-sub">留下你的联系方式与想法，我会尽快回复。</p>

    <!-- 提交成功后的提醒（可选：用 Formspree 的 _next 跳转到 /thanks/ 页面） -->
    <div id="formMsg" style="display:none" class="success">已发送成功，感谢你的留言！</div>

    <form id="contactForm" action="https://formspree.io/f/mdkwkyyy" method="POST" onsubmit="return handleSubmit(event)">
      <div class="grid">
        <label class="label">名字
          <input class="input" name="name" required autocomplete="name" />
        </label>
        <label class="label">邮箱
          <input class="input" name="email" type="email" required autocomplete="email" />
        </label>
      </div>

      <label class="label" style="margin-top:10px">主题
        <input class="input" name="subject" placeholder="想聊点什么？" />
      </label>

      <label class="label" style="margin-top:10px">内容
        <textarea class="textarea" name="message" placeholder="请尽量描述清楚你的需求或问题～"></textarea>
      </label>

      <!-- 反垃圾：蜜罐字段（正常用户不会看到/填写） -->
      <input type="text" name="_gotcha" style="display:none" />

      <!-- 可选：提交后跳转到感谢页（先创建 /thanks/ 页面再启用）
      <input type="hidden" name="_next" value="{{ '/thanks/' | relative_url }}">
      -->

      <div class="actions">
        <button class="btn" type="submit">发送消息</button>
        <span class="note">预计 1–2 个工作日内回复</span>
      </div>
    </form>
  </div>
</div>

<script>
async function handleSubmit(e){
  e.preventDefault();
  const form = e.currentTarget;
  const res = await fetch(form.action, { method:'POST', body: new FormData(form), headers: { 'Accept':'application/json' }});
  if (res.ok) {
    document.getElementById('formMsg').style.display='block';
    form.reset();
  } else {
    alert('发送失败，请稍后再试或直接邮件联系。');
  }
  return false;
}
</script>
