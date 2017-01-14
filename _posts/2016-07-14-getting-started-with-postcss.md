---
layout: post
title:  " آموزش PostCSS - معرفی و نصب"
date:   2016-07-14 23:00:42 +0330
category: web-developing
category-fa: توسعه وب
sitemap: true
tags: PostCSS,sass,less,stylus,Preprocessor,css,web-development, Post CSS, پست سی اس اس, توسعه وب, پیش پردازنده های سی اس اس
---

![شروع کار با جکیل!]({{site.baseurl}}/assets/images/posts/2016-07-14-getting-started-with-postcss/postcss.jpg)
تقریبا تمام توسعه دهنده های فرانت اند که زمان زیادی رو صرف کار کردن با css می کنن یک سری از کمبود ها رو حس کردن که با اومدن Preprocessor تا حد قابل توجهی برطرف شدن. همه ما تقریبا با Preprocessor هایی مثل sass، less و stylus آشنایی داریم یا حداقل اسمشون به گوشمون خورده،
این ابزار ها در طراحی و توسعه وب به یک بخش حیاتی تبدیل شده اند به حدی که استفاده نکردن از این ابزار ها یک اشتباه بزرگ محسوب میشه. خوشبختانه این ابزار ها روز به روز در حال افزایش هستند یکی از این ابزار های [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") هست که در ادامه معرفیش خواهم کرد.

### PostCSS چیست؟
اول از همه به این نکته توجه کنید که این ابزار یک Preprocessor نیست. [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") دستورات css را با استفاده از جاوا اسکریپت تبدیل می کنه.
[PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") کاملا وابسته به پلاگین هایی است که با جاوا اسکریپت براش نوشته شدن و به
تنهایی کاری انجام نمیده برای همین میشه گفت امکانات بیشتری نسبت به Preprocessor ها در اختیار ما میزاره البته این نکته هم فراموش نشه که شما می تونید [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") را به همراه Preprocessor ها استفاده کنید.<br>
برای مثال در یک پروژه نیاز دارید توی css متغییر بنویسید ، برای این کار یک پلاگین به اسم postcss-simple-vars وجود داره که این امکان رو به css اضافه می کنه.
{% highlight scss linenos %}
$dir:    top;
$blue:   #056ef0;
$column: 200px;

.menu_link {
    background: $blue;
    width: $column;
}
.menu {
    width: calc(4 * $column);
    margin-$(dir): 10px;
}
{% endhighlight %}
خروجی کد بالا:
{% highlight css linenos %}
.menu_link {
    background: #056ef0;
    width: 200px;
}
.menu {
    width: calc(4 * 200px);
    margin-top: 10px;
}
{% endhighlight %}
در حال حاضر بیش از ۲۰۰ پلاگین برای PostCSS وجود داره که لیست اون هارو می تونید از صفحه [Github](https://github.com/postcss/postcss "پلاگین های PostCSS") یا سایت [ postcss.parts](http://postcss.parts/ "پلاگین های PostCSS")  ببینید.

### چرا باید از PostCSS استفاده کنیم؟
شاید پیش خودتون بگید چه دلیلی داره که به جای Preprocessor ها از PostCSS استفاده کنیم. باید بگم که دلایل خوبی برای استفاده از این ابزار وجود داره که می تونید در زیر مشاهده کنید.

- <span class="list-label">۱ - سریع: </span> کامپایل سریعتر نسبت به Preprocessor ها.
- <span class="list-label">۲ - ماژولار: </span> شما  بر اساس نیاز پروژه می تونید پلاگین های مختلفی اضافه کنید.
- <span class="list-label">۳ - قدرتمند: </span> وجود بیش از ۲۰۰ پلاگین که این ابزار رو قدرتمند و کاربردی تر می کنه.

{% highlight plaintext %}
PostCSS 5.0.11: 40 ms
PostCSS 5.0.10: 60ms    (1.5 times slower)
Rework:         75 ms   (1.9 times slower)
libsass:        76 ms   (1.9 times slower)
Less:           147 ms  (3.7 times slower)
Stylus:         166 ms  (4.1 times slower)
Stylecow:       258 ms  (6.4 times slower)
Ruby Sass:      1042 ms (26.0 times slower)
{% endhighlight %}
در باکس بالا می تونید سرعت کامپایل ابزار های مختلف رو ببینید. یکی از مشکلاتی که با sass داشتم تاخیر در کامپایل فایل بود که با بزرگ شدن پروژه بوجود میومد. خوشبختانه [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") این مشکل رو حل کرده.

### نصب و راه اندازی PostCSS
PostCSS را از طریق npm نصب می کنیم.
{% highlight nginx %}
  npm install -g postcss-cli
{% endhighlight %}
برای اطمینان از صحت نصب کد زیر را در ترمینال وارد کنید:
{% highlight nginx %}
  postcss --help
{% endhighlight %}
پس از اجرای کد بالا باید خروجی زیر رو ببینید:

![شروع کار با جکیل!]({{site.baseurl}}/assets/images/posts/2016-07-14-getting-started-with-postcss/postcss1.jpg)

خب تا اینجای کار [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") رو با موفقیت نصب کردیم. در پست بعدی به معرفی پلاگین های محبوب و کاربردی [PostCSS](https://github.com/postcss/postcss "postcss در اصل تبدیل کننده دستور های css با استفاده از پلاگین های جاوا اسکریپته") و نحوه اجرای این ابزار توسط Task Runner های [Gulp](http://gulpjs.com/ "Gulp ابزاری هست که کارها را می تواند به صورت خودکار انجام دهد.") و [Grunt](http://gruntjs.com/ "Grunt ابزاری هست که کارها را می تواند به صورت خودکار انجام دهد.") می پردازم.
