# چیت شیت دیزاین پترن‌ها برای لاراول

این راهنما به عنوان چیت شیتی برای آشنایی سریع با 23 الگوی طراحی (Design Patterns) ارائه شده است که به ترتیب میزان کاربرد و اهمیت آن‌ها در پروژه‌های لاراول مرتب شده‌اند. هر الگو شامل یک توضیح مختصر و مثال‌هایی از موقعیت‌های استفاده در لاراول می‌باشد.

> **توجه:** 
> - **Facade:** در لاراول به شدت استفاده می‌شود؛ بسیاری از امکانات مثل `Cache`، `DB` و `Log` از این الگو بهره می‌برند.
> - **Singleton:** مدیریت شیء مشترک در سرویس کانتینر لاراول نمونه‌ای از این الگو است.
> - **Factory:** الگوی مورد استفاده در ساخت Model Factory ها و ایجاد نمونه‌های کلاس‌ها بدون نیاز به وابستگی مستقیم.
> - **Observer:** الگوی استاندارد در Eloquent Events و Observers برای گوش دادن به تغییرات مدل‌هاست.

---

## 1. Facade Pattern
**شرح:** ارائه یک رابط ساده برای عملکرد‌های پیچیده پشت صحنه.  
**کاربرد در لاراول:** لاراول از Facade برای دسترسی سریع به سرویس‌های اصلی مانند Cache، Database، Queue و ... استفاده می‌کند.

---

## 2. Singleton Pattern
**شرح:** تضمین وجود تنها یک نمونه از یک کلاس در سراسر برنامه و فراهم آوردن نقطه دسترسی جهانی.  
**کاربرد در لاراول:** در سیستم Service Container لاراول، بسیاری از سرویس‌ها به صورت Singleton مدیریت می‌شوند تا از مصرف بهینه منابع اطمینان حاصل شود.

---

## 3. Factory Pattern (Factory Method)
**شرح:** الگوی ساخت شیء که بدون وابستگی مستقیم به کلاس‌های پیاده‌سازی، فرآیند ساخت را جداسازی می‌کند.  
**کاربرد در لاراول:** استفاده از Model Factory ها در زمان تست و بذر زدن (seeding) دیتابیس، که امکان تولید نمونه‌های مدل را فراهم می‌کند.

---

## 4. Observer Pattern
**شرح:** ایجاد ارتباط بین شیء اصلی (subject) و ناظران (observers) به‌گونه‌ای که تغییرات روی شیء موجب اطلاع‌رسانی به ناظران شود.  
**کاربرد در لاراول:** استفاده در Eloquent Observer ها برای انجام عملیات پس از رخدادهای مختلف مانند ایجاد، به‌روزرسانی یا حذف مدل‌ها.

---

## 5. Chain of Responsibility Pattern
**شرح:** ارسال درخواست از شیء به شیء به صورت زنجیره‌ای تا زمانی که یکی از آن‌ها مسئولیت پردازش درخواست را بر عهده بگیرد.  
**کاربرد در لاراول:** معماری Middleware در لاراول، که درخواست‌های ورودی را از طریق لایه‌های متعدد فیلتر و پردازش می‌کند.

---

## 6. Command Pattern
**شرح:** جداسازی درخواست از اجرای آن به صورت یک شیء مجزا برای افزایش انعطاف‌پذیری در مدیریت درخواست‌ها.  
**کاربرد در لاراول:** ساخت دستورات Artisan، عملکردهای مرتبط با job queues و پردازش رویداد‌ها.

---

## 7. Strategy Pattern
**شرح:** تعریف مجموعه‌ای از الگوریتم‌ها و اجازه دادن به تغییر آن‌ها در زمان اجرا به صورت داینامیک.  
**کاربرد در لاراول:** انتخاب استراتژی‌های مختلف برای پیاده‌سازی مسائل مانند درگاه‌های پرداخت یا الگوریتم‌های کش، بدون تغییر در ساختار اصلی برنامه.

---

## 8. Decorator Pattern
**شرح:** افزودن رفتار به شیء‌ها به صورت داینامیک بدون تغییر در ساختار اصلی آن‌ها.  
**کاربرد در لاراول:** سیستم Middleware و امکاناتی مانند افزودن قابلیت‌های اضافی به درخواست یا پاسخ HTTP بدون تغییر در کلاس اصلی.

---

## 9. Adapter Pattern
**شرح:** تبدیل رابط یک کلاس به رابطی که کلاینت انتظار دارد، بدون تغییر در کلاس اصلی.  
**کاربرد در لاراول:** ادغام کتابخانه‌ها و سرویس‌های شخص ثالث در پروژه و تطبیق آن‌ها با معماری و قراردادهای داخلی.

---

## 10. Template Method Pattern
**شرح:** تعریف اسکلت کلی الگوریتم در کلاس مادر و اجازه دادن به کلاس‌های فرزند برای بازنویسی یا تکمیل مراحل خاص آن.  
**کاربرد در لاراول:** پیاده‌سازی کلاس‌های پایه برای کنترل‌کننده‌ها یا Jobها که مراحل پردازش ثابت دارند و تنها جزئیات باید تغییر کنند.

---

## 11. Builder Pattern
**شرح:** جداسازی ساخت یک شیء پیچیده از نمایش نهایی آن به گونه‌ای که همان فرآیند ساخت بتواند اشیاء متفاوتی تولید کند.  
**کاربرد در لاراول:** نمونه بارز، Query Builder لاراول که به ساخت درخواست‌های پایگاه داده به شکل داینامیک کمک می‌کند.

---

## 12. Abstract Factory Pattern
**شرح:** فراهم آوردن واسطی برای تولید خانواده‌ای از اشیاء مرتبط بدون نیاز به مشخص کردن کلاس‌های دقیق آن‌ها.  
**کاربرد در لاراول:** در سناریوهای پیچیده که نیاز به تولید سرویس‌ها یا اجزای وابسته به پیکربندی‌های مختلف دارید.

---

## 13. Prototype Pattern
**شرح:** ساخت شیء جدید از روی یک نمونه (prototype) موجود به جای استفاده از سازنده به صورت مجدد.  
**کاربرد در لاراول:** در مواقعی که نیاز به کلون کردن اشیاء با تنظیمات اولیه مشخص و حفظ وضعیت اولیه داریم.

---

## 14. Composite Pattern
**شرح:** ترکیب اشیاء در یک ساختار درختی برای نمایش روابط جزء-کل (part-whole).  
**کاربرد در لاراول:** کاربرد در پیاده‌سازی منوها، دسته‌بندی‌ها یا سیستم‌های سلسله‌مراتبی که امکان مدیریت اجزای متعدد را به‌صورت یکجا فراهم می‌کند.

---

## 15. Bridge Pattern
**شرح:** جداسازی انتزاع از پیاده‌سازی به‌گونه‌ای که هر دو بتوانند به‌طور مستقل تغییر کنند.  
**کاربرد در لاراول:** در مواقعی که می‌خواهید بخش واسط کاربری (UI) و منطق تحت‌زمینه را از هم تفکیک کنید تا توسعه یا تست هر یک به‌طور مستقل صورت پذیرد.

---

## 16. Proxy Pattern
**شرح:** ایجاد یک نماینده یا واسطه برای کنترل دسترسی به شیء اصلی به‌منظور افزودن قابلیت‌هایی مانند lazy loading یا امنیت.  
**کاربرد در لاراول:** کاربرد در Eloquent برای به تأخیر انداختن بارگذاری داده‌ها (Lazy Loading) و کنترل دسترسی به منابع.

---

## 17. Flyweight Pattern
**شرح:** به اشتراک گذاشتن داده‌های مشترک بین تعداد زیادی شیء به‌منظور بهینه‌سازی مصرف حافظه.  
**کاربرد در لاراول:** در پروژه‌هایی که تعداد زیادی شیء مشابه ایجاد می‌شود و بهینه‌سازی مصرف حافظه اهمیت دارد، مثلا در پردازش صف‌های بزرگ.

---

## 18. Iterator Pattern
**شرح:** فراهم آوردن یک روش یکنواخت برای پیمایش اعضای یک مجموعه بدون افشای ساختار درونی آن.  
**کاربرد در لاراول:** استفاده از امکانات زبان PHP برای پیمایش مجموعه‌های داده و کار با داده‌های بزرگ به صورت بهینه.

---

## 19. Mediator Pattern
**شرح:** کاهش وابستگی مستقیم بین اجزا از طریق یک شیء واسطه (Mediator) که وظیفه هماهنگی تعاملات میان آن‌ها را بر عهده دارد.  
**کاربرد در لاراول:** مدیریت تعامل بین بخش‌های مختلف سیستم از طریق event ها و listener ها به‌طوری که وابستگی‌های پیچیده کاهش یابد.

---

## 20. Memento Pattern
**شرح:** ذخیره و بازیابی وضعیت قبلی یک شیء بدون نقض اصول کپسوله‌سازی آن.  
**کاربرد در لاراول:** استفاده در پیاده‌سازی قابلیت‌های Undo/Redo یا ذخیره وضعیت پیچیده سیستم در بخش‌هایی مانند فرم‌های چند مرحله‌ای.

---

## 21. State Pattern
**شرح:** تغییر رفتار یک شیء بر اساس وضعیت داخلی آن به‌گونه‌ای که رفتار آن بدون تغییر کلاس داده شده تغییر کند.  
**کاربرد در لاراول:** مدیریت وضعیت‌های پیچیده در فرآیندهای تجاری مانند مراحل پردازش سفارش، وضعیت تراکنش‌ها یا جریان‌های کاری.

---

## 22. Visitor Pattern
**شرح:** جداسازی الگوریتم از ساختار داده‌ها به‌گونه‌ای که بتوان عملیات‌های جدیدی را بدون تغییر در کلاس‌های اصلی به ساختار داده اضافه کرد.  
**کاربرد در لاراول:** به کارگیری در سناریوهایی که نیاز به اعمال عملیات‌های متفاوت بر روی ساختارهای پیچیده داده وجود دارد، مثلاً در گزارش‌گیری یا پردازش مجموعه داده‌های بزرگ.

---

## 23. Interpreter Pattern
**شرح:** تعریف قواعد یک زبان دامنه خاص (DSL) و تفسیر آن عبارات به‌گونه‌ای که معنای آن‌ها استخراج شود.  
**کاربرد در لاراول:** در مواقعی که نیاز به پردازش عبارات یا دستورات سفارشی و توسعه زبان‌های کوچک در سیستم وجود داشته باشد.

---

### نکات پایانی

- **انتخاب الگو:** هر کدام از این الگوها مزایا و معایب خاص خود را دارند؛ بنابراین با بررسی دقیق نیاز پروژه و در نظر گرفتن پیچیدگی‌های معماری، الگوی مناسب را انتخاب کنید.  
- **انعطاف‌پذیری:** استفاده از این الگوها کمک می‌کند تا کد شما مقیاس‌پذیر و قابل نگهداری باقی بماند.  
- **توسعه و آموزش:** توصیه می‌شود علاوه بر آشنایی نظری، مسائل عملی و پروژه‌های کوچک را برای بهره‌برداری بهینه از این اصول و الگوها تجربه کنید.

امید است این چیت شیت به عنوان یک مرجع سریع و کاربردی در پروژه‌های لاراول شما مفید واقع شود و زمینه تبادل دانش و بهبود معماری نرم‌افزار را فراهم آورد.
