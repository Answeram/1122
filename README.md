# NGINX Reverse Proxy Installer

[English README](https://github.com/Ptechgithub/NginxReverseProxy/blob/main/README_ENGLISH.md)

## نصب
```
bash <(curl -fsSL https://raw.githubusercontent.com/Ptechgithub/NginxReverseProxy/main/install.sh)
```
![20](https://github.com/Ptechgithub/configs/blob/main/media/20.jpg)

---

این اسکریپت برای نصب و پیکربندی NGINX Reverse Proxy بر روی سرورهای لینوکسی استفاده می‌شود. با اجرای این اسکریپت، می‌توانید به سرعت و به صورت خودکار یک سرور وب را به عنوان یک پروکسی برای مسیردهی ترافیک به برنامه‌های دیگر (سرویس‌های GRPC و WebSocket) پیکربندی کنید.
گواهی  ssl بگیرید و یک قالب سایت  رایگان نصب کنید.

---
## استفاده
ابتدا در CDN خود مثلا Cloudflare یک A record بسازید و دامین یا ساب دامین خود را به آی پی سرور اشاره بدید و تیک پروکسی هم روشن کنید.

در بخش تنظیمات Network تیک گزینه ی GRPC را فعال کنید. 

در بخش SSL/TLS encryption mode گزینه ی Full را انتخاب کنید.

پس از اجرای اسکریپت، دامنه‌ی مورد نظر خود را وارد کنید و مراحل نصب را دنبال کنید.

با انتخاب install fake site مجموع `170` قالب سایت دانلود میشه و یک قالب به صورت رندوم نصب میشه برای دفعات بعدی مجدد  با انتخاب این گزینه قالب قبلی  حذف میشه و سریعا یک قالب جدید نصب میشه.(امکان داره قالب قبلی رو نشون بده به علت حافظه Cache مرورگر، توی یه مرورگر دیگه تست کنی میبینی که قالب جدید اعمال شده.)

در زمان نصب نیاز است که پورت 80 باز باشد و توسط سرویس دیگری در حال استفاده نباشد.تا بتواند گواهی `ssl ` بگیرد پس از نصب پورت آزاد است و میتوانید از ان استفاده کنید.

پس از نصب سرویس ، Nginx روی پورت `443` به طور پیش فرض کار میکند و لازم است که این پورت آزاد باشد و توسط سرویس دیگری در حال استفاده نباشد. اما از طریق خود اسکریپت میتوانید این پورت را با یکی دیگر از پورت های HTTPS  عوض کنید و از پورت `443 ` در سرویس های دیگر خود استفاده کنید.

با گزینه `5` میتوانید محدودیت ترافیک اعمال کنید. و کارکرد آن به این صورت است که بعد از انتخاب این گزینه از شما یک درصد مشخص میخواهد و شما پس از وارد کردن آن یک اسکریپت را فعال میکنید که هر `24` ساعت مقدار مصرف شما را محاسبه میکند و پس از `24` ساعت اگر مقدار مصرف شما نسبت به اولین باری که این گزینه را انتخاب کردید بیش تر از آن درصدی باشد که مشخص کردید. (مثلا : مصرف فردا نسب به امروز 50 درصد افزایش داشته باشد.) دستور `systemctl stop nginx` اجرا میشود و سرویس خود کار قطع میشود و لاگ هم در مسیر `root/usage` ذخیره میشود.( کرونتب هرروز ساعت `00:00` اجرا میشود) برای اجرای مجدد هم کافیه که دستور `systemctl start nginx` را وارد کنید یا سرور را ریبوت کنید.  نکته : پس از ریبوت شدن سرور مقدار مصرف سرور از صفر محاسبه خواهد شد.

تصاویر Client به صورت gif است اگر ثابت بود روی ان کلیک کنید تا پخش شود.

اسکریپت برای دامنه‌ی شما `SSL certificate` را  دریافت خواهد کرد و تنظیمات NGINX Reverse Proxy را اعمال می‌کند.
و در نهایت به شما مسیر سرتیفیکت را میدهد. که میتوانید در پنل خود استفاده کنید.
در این اسکریپت `Path` را خودتان انتخاب می‌کنید.
برای استفاده در پنل `x-ui` تنها کافیست به صورت زیر برای grpc و ws اقدام کنید:


---

## نحوی کانفیگ WebSocket

### Panel

![21](https://raw.githubusercontent.com/Ptechgithub/configs/main/media/21.jpg)

---

### Client

![23](https://raw.githubusercontent.com/Ptechgithub/configs/main/media/23.gif)

---
---
---

## نحوه ی کانفیگ GRPC

### Panel

![22](https://raw.githubusercontent.com/Ptechgithub/configs/main/media/22.jpg)

---

### Client

![24](https://raw.githubusercontent.com/Ptechgithub/configs/main/media/24.gif)



[website-templates](https://github.com/learning-zone)