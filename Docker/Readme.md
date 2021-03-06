<img src="../Statics/docker.webp" alt="Sharif Web Programming Workshop"> 

<div align="center">
تهیه‌کنندگان:
پارسا رستمی، سید علی‌رضا هاشمی، ساعی سعادت، آرمان محمدی، علی پورقاسمی، اسماعیل پاهنگ و محمد فتاح‌پور
</div>

<div dir = 'rtl' style='text-align:justify'>

# Docker (بخش اول)

داکر یک پلتفرم متن باز برای توسعه، جابجا کردن و اجرای اپلیکیشن هاست. داکر به شما اجازه میدهد تا اپلیکیشن خود را از زیرساخت (infrastructure) جدا کنید تا بتوانید سریع تر  نرم افزار خود را توسعه دهید. با داکر میتوانید زیرساخت خود را همانند اپلیکیشن خود مدیریت کنید.

<br/>


```Docker``` به توسعه‌دهندگان کمک می‌کند تا ظروف نرم‌افزاری (software portable) سبک و قابل حمل را بسازند که کار توسعه، آزمایش و استقرار برنامه‌ها را ساده می‌کند. داکر از محیطی‌های کوچک و بزرگ اجزای هسته سیستم عامل به صورت مشترک استفاده می‌کند که کاربران بتوانند به راحتی یک اپلیکیشن را طراحی یا توسعه دهند که بهترین بخش این مسئله این است که داکر در صورت نیاز این اجزا را از یکدیگر جدا می‌کند و در محیطی که ایزوله نام دارد قرار می‌دهد،  به این محیط و بسته‌ی ایزوله، کانتینر ```Container``` می‌گویند.


## پلتفرم داکر
داکر این قابلیت را به ما میدهد تا یک اپلیکیشن را در یک محیط ایزوله به نام کانتینر ( Container ) اجرا کنیم. ایزوله بودن و امنیت کانینتر ها باعث میشود که بتوانیم تعداد زیادی کانتینر را روی هاست اجرا کنیم.
کانتینر ها سبک و سریع هستند زیرا نیازی ندارند که مانند ماشین های مجازی سربار Hypervisor را تحمل کنند و مستقیما روی هسته ( Kernel ) کامپیوتر سرویس دهنده اجرا میشوند. این به آن معناست که میتوان تعداد بیشتری کانتینر را روی یک ماشین نسبت به حالتی که از ماشین مجازی استفاده میکنیم اجرا کرد.
البته حتی این قابلیت را نیز داریم که از داکر درون ماشین مجازی نیز استفاده کنیم!

<br/>


## کاربرد داکر چیست؟
```Docker``` دسترسی کاربران به برنامه‌های مختلف حتی در سرور‌های قدیمی را فراهم می‌کند. همچنین داکر این قابلیت را دارد که ارسال و بسته‌بندی برنامه را راحت‌تر انجام دهد. تقریبا پنج سال پیش بود که شخصی به نام ```Solomon Hykes``` کسب و کاری با استفاده از دارکر تاسیس و راه‌اندازی کرد. مهم‌ترین هدفی که این عمل داشت این بود که کاربران راحتر بتوانند با ```Container``` ارتباط برقرار کنند یا به نوعی دیگر با آنان تعامل داشته باشند.

با انتشار نسخه Docker 1.0 خوشبختانه این کسب و کار با موفقیت چشم‌گیری روبه رو شد و با گذشت زمان مخصوصا در سال ۲۰۱۴ کاربران زیادی جذب داکر (Docker) شدند و دارکر محبوبیت زیادی در آن سال‌ها برای خود کسب کرد. با پیشرفت فوق‌العاده‌ی داکر شرکت‌هایی که از سرور‌های قدیمی و ماشین‌های مجازی استفاده می‌کردند، مجاب به استفاده از داکر شدند و سرویس‌ها و سرورهای خود را براساس بستر داکر راه‌اندازی کردند.

نکته حایز اهمیتی که برای داکر وجود داشت این بود که در آن زمان که هنوز داکر در نسخه 1.0 قرار داشت بانک‌های معروف و بزرگ از آن برای سرویس‌ها و سرورهای خود استفاده می‌کردند که این مورد نشان دهنده امنیت بالای داکر در آن زمان بود.

<br/>


## موتور داکر ( Docker Engine )

انجین داکر یک اپلیکیشن سمت کلاینت و سرور است که قابلیت های زیر را داراست:
- یک سرور که نوعی نرم افزار با مدت زمان اجرای طولانی است که به آن پروسه Deamon  گفته میشود.
- یک REST API که واسط کاربری نرم افزار ها برای ارتباط و دادن دستورات به deamon است.
- یک کلاینت Command Line Interface (CLI)

![enter image description here](https://docs.docker.com/engine/images/engine-components-flow.png)

CLI از REST API داکر برای کنترل و یا ارتباط با Deamon به وسیله نوشتن اسکریپت و یا دستورات مستقیم CLI استفاده میکند.

Deamon در واقع وظیفه ساخت و مدیریت Object های داکر را دارد. این Object ها شامل Image ها، Container ها، Network ها و Volume ها میشوند.

<br/>

## کارایی داکر
### تولید سریع و باثبات اپلیکیشن
سناریو زیر را در نظر بگیرید:
- توسعه دهندگان یک پروژه کد های خود را به صورت local روی کامپیوتر خود مینویسند و توسط کانتینر های داکر آن ها را با یکدیگر به اشتراک میگذارند.
- آن ها از داکر استفاده میکنند و اپلیکیشن خود را به یک محیط تست push میکنند و آن را تست میکنند.
- وقتی باگی در نرم افزار پیدا شود آن ها باگ را در محیط local یعنی روی کامپیوتر خود تصحیح میکنند و دوباره به محیط تست میفرستند.
- هنگامی که تست ها با موفقیت انجام شد برای رساندن اپلیکیشن به مشتریان تنها کافیست Image آپدیت شده خود را به محیط اصلی یعنی Production بفرستیم.

دلیل اینکه میتوانیم روی محیط اول یعنی کامپیوتر خود کد بزنیم و سپس روی محیط دوم تست کنیم و سپس کد را به محیط سوم برای استفاده اصلی بفرستیم این است که زیرساخت همه این محیط ها یکسان است و توسط داکر فراهم میشود.

### گسترش پذیری و ریسپانسیو بودن

کانتینر داکر میتواند روی محیط local شخص توسعه دهنده، روی ماشین مجازی یا ماشین فیزیکی درون یک دیتا سنتر، روی فضای ابری و یا ترکیبی از این محیط ها اجرا شود.

همچنین به وسیله داکر میتوانن در زمان بسیار کمی یعنی تقریبا به صورت real-time اپلیکیشن را به بخش ها کوچکتری تقسیم کرد و یا هر بخش آن را گسترش داد.

### انجام کار بیشتر روی سخت افزار یکسان
داکر سبک و سریع است. و نسبت به ماشین های مجازی که برپایه Hupervisor ها کار میکنند به شدت کارا و کم هزینه است. داکر برای نرم افزار هایی که زیرساخت فشرده و سنگینی دارند نیز بسیار عالیست.

<br/>


## چه کسانی از Docker استفاده می کنند؟
```Docker``` ابزاری است که هم به درد برنامه نویس ها می خورد و هم به درد مدیرهای شبکه و به همین خاطر هم برخی اوقات به نام ```DevOps``` از آن یاد می شود که ترکیبی از دو اسم Developer و Operations است. برای برنامه نویس ها ```Docker``` به این معنا است که فقط روی کد نویسی خودتان تمرکز کنید و دغدغه اینکه کد شما قرار است بر روی چه سیستم عاملی با چه نیازمندی هایی نصب شود را نداشته باشید اینکار را ```Docker``` برای شما انجام می دهد.

از طرفی هزاران برنامه و نرم افزار متنوع وجود دارند که برای کار کردن در محیط ```Docker``` طراحی شده اند و شما به عنوان یک ITPRO می توانید به راحتی از آنها در مجموعه خودتان در قالب یک Docker Container استفاده کنید. از طرفی در محیط های عملیاتی```Docker``` این امکان را به همه می دهد که چندین برنامه را همزمان بر روی یک سیستم فیزیکی نصب و اجرا کنند و اینها هیچکدام با یکدیگر کوچکترین ارتباطی نداشته باشند و بصورت کاملا ایزوله در مجموعه فعالیت کنند.
## کانتینرها و داکر
```Container``` این امکان را برای برنامه نویسان و توسعه دهندگان اپلیکیشن ها فراهم می کند تا یک برنامه را با تمام ماژول ها و کامپوننت‌های وابسته آن ( مانند کتابخانه ها ، توابع و … ) یکی کرده و به صورت یک پکیج درآورده تا آن برنامه تولید شده در پلتفرم ها و سیستمهای مختلف بدون مشکل اجرا شود، در حقیقت بدون نگرانی از تنظیمات و وابستگ‌های یک Application خاص در پلتفرم های دیگر، آن برنامه در هر محیطی اجرا شود.
## اصطلاحاتی که در زمینه ی داکر استفاده می شوند
### Docker file
داکر یک image را به وسیله ی خواندن دستورات موجود در یک dockerfile می سازد. یک dockerfile یک فایل text است که تمامی دستوراتی که نیاز برای صدا زده شدن است تا یک image ساخته شود.  یک کاربر برای ساختن یک فایل image از دستور ``` docker build ``` استفاده می کند و خود داکر به طور اتوماتیک با استفاده از خواندن دستورات dockerfile این فایل image را می سازد. ورودی و خروجی این کد را در زیر مشاهده می کنید.

<div dir = 'ltr'>
  
```
$ docker build .

Sending build context to Docker daemon  6.51 MB
...
```
</div>

![enter image description here](https://miro.medium.com/max/2400/1*p8k1b2DZTQEW_yf0hYniXw.png)

### Docker image
هنگامی که Dockerfile خود را نوشتید ، برای ساخت یک Image بر اساس آن Dockerfile ، از ابزار  Docker build استفاده می کنید. در حالی که Dockerfile مجموعه دستورالعملهایی است که نحوه ساخت image را به شما می گوید ،  Docker image یک فایل قابل حمل است که حاوی مشخصاتی است برای این که کدام  اجزا نرم افزاری container اجرا خواهند شد و چگونه اجرا می‌شوند. از آنجا که یک Dockerfile احتمالاً شامل دستورالعمل هایی در مورد گرفتن برخی از بسته های نرم افزاری از مخازن آنلاین است ، بنابراین باید دقیقاً نسخه های مناسب را مشخص کنید ، در غیر این صورت ممکن است بسته به زمان استناد ، Dockerfile شما imageهای متناقضی را ایجاد کند.Codefresh نگاهی به نحوه ساختن تصویر با جزئیات بیشتر ارائه می دهد.
### Docker containers
نمونه های در حال اجرایی از Image ها هستند. 
![enter image description here](https://miro.medium.com/max/700/0*ujI404Gnomn1Wz5h.png)

### Docker Hub
Docker Hub (داکر هاب) یک سرویس اشتراک‌گذاری تهیه شده توسط شرکت Docker است که شامل مخزنی از image های آماده برای Docker می‌باشد. این مخزن حاوی ده‌ها هزار برنامه و سیستم‌عامل است که می‌توان به آن image هایی را هم اضافه کرد.

شما می‌توانید هر Docker Image را به راحتی می‌توانید با دیگران به اشتراک بگذارید. برای این کار باید Repository مناسبی با یک عنوان درخور ایجاد کنید کاری که در سایتهایی مانند bitbucket یا gitlab انجام میشود. این فرآیندهای ایجاد Reposotiry، عضویت در آن، سهم داشتن در توسعه یک Repository و... در Docker Hub انجام می‌شود. ‌اگر قصد داشته باشید از یک Docker Image فقط pull بگیرید یا لیست Imageهای عمومی موجود را جست و جو کنید نیازی به داشتن اکانت در Docker Hub  ندارید اما اگر بخواهید push انجام دهید یا نظر بدهید یا like بزنید حتماً باید در Docker Hub عضو باشید.
### Docker deployment and orchestration
هنگامی که اپلیکیشن‌ها روی چند سیستم میزبانی مقیاس می‌یابند، توانایی مدیریت هر سیستمِ میزبان و انتزاع پیچیدگی پلتفرم زیربنایی، گزینه‌ای جذاب به نظر می‌رسد. هماهنگی (Orchestration) اصطلاحی کلی است که به زمان‌بندی کانتینر، مدیریت کلاستر و احتمالاً تدارک میزبان‌های بیشتر اشاره دارد. در این محیط، منظور از زمان‌بندی (scheduling) توانایی یک مدیر برای بارگذاری یک فایل سرویس روی یک سیستم میزبان و تعیین شیوه اجرای کانتینر خاص است. با این که زمان‌بندی به عمل خاص بارگذاری تعریف سرویس اشاره دارد؛ اما در یک معنای کلی‌تر ابزارهای زمانبندی مسئول قلاب شدن به سیستم init میزبان و مدیریت سرویس‌ها در هر ظرفیتی که لازم باشد هستند.

مدیریت کلاستر به فرایند کنترل کردن گروهی از میزبان‌ها گفته می‌شود. این مدیریت می‌تواند شامل افزودن و حذف میزبان‌ها از یک کلاستر، دریافت اطلاعات در مورد وضعیت کنونی میزبان‌ها و کانتینرها، و آغاز یا توقف پردازش‌ها باشند. مدیریت کلاستر ارتباط نزدیکی با زمانبندی دارد، زیرا ابزارهای زمان‌بندی باید به همه میزبان‌ها در کلاستر دسترسی داشته باشند تا بتوانند سرویس‌ها را زمان‌بندی کنند. به این منظور در اغلب موارد از ابزار یکسانی استفاده می‌شود.
### Docker compose
Docker همچنین هماهنگی رفتارهای بین کانتینرها را آسانتر می کند و بنابراین با قرار دادن کانتینرها روی هم ، پشته های برنامه را می سازد. Docker Compose توسط Docker ایجاد شده است تا روند توسعه و تست برنامه های چند کانتینر را ساده کند. این یک ابزارcommand-line است و یک فایل توصیف کننده با قالب بندی خاص برای جمع آوری برنامه های کاربردی از چندین کانتینر و اجرای آنها به صورت هماهنگ بر روی یک میزبان را در اختیار شما قرار می دهد
### kubernetes
 رایانش ابری نیازهای جدیدی را در دنیای سخت‌افزار و نرم‌افزار ایجاد کرد و شاهد نسل جدیدی از فناوری‌ها بودیم که تعامل با رایانش ابری را ساده‌تر می‌کردند. اپلیکیشن‌های بزرگ نیز به سمت ماژولار شدن پیش رفتند تا مدیریت و تعامل با آن‌ها از جانب توسعه‌دهندگان و کاربران ساده‌تر شود.

در همین راستا گوگل به عنوان یکی از بزرگترین غول‌های فناوری که حیات خود را مدیون رایانش ابری است به این فکر افتاد تا یکی از پروژه‌های بزرگ خود را که در داخل این مجموعه از آن استفاده می‌کرد به صورت متن باز منتشر کند. این پروژه از زیرساخت‌هایی بر اساس کانتینرها بهره می‌گرفت و در داخل گوگل با نام Borg شناخته می‌شد.
جالب است بدانید Borg نقش اساسی در اجرای سرویس‌‌های مهم گوگل مانند جی‌میل و موتور جستجوی این برند داشت. به این ترتیب با متن‌باز شدن این پروژه سایر شرکت‌ها نیز قادر بودند پروژه‌های خود را همانند گوگل در ابعاد بزرگ پیش بگیرند.

به این ترتیب به زبان ساده‌تر می‌توان کوبرنتیز را وارث Borg دانست. یکی از خاصیت‌های مهم متن‌باز شدن هر پروژه‌ای توسعه سریع و گسترش آن در میان کاربران است و کوبرنتیز نیز به‌سرعت راه خود را به جوامع فناوری باز کرد و به رقیب بزرگی برای ساز و کارهای دیگر کنترل کانتینرها مانند Apache Mesos و Docker Swarm تبدیل شد.

در حال حاضر هزاران توسعه‌دهندگان با اهداف تجاری و شخصی در توسعه و بهینه‌تر کردن کوبرنتیز فعالیت دارند و شاهد ایجاد نسخه‌های تجاری کوبرنتیز نیز هستیم که شر‌کت‌های بزرگی مانند RedHat سرمایه‌گذاری‌های زیادی را برای گسترش آن انجام داده‌اند.
اگر بخواهیم به‌زبان ساده کوبرنتیز را توضیح دهیم باید بگوییم کوبرنتیز اجرا و مدیریت کانتینرهای مختلف را در سرورهای متفاوت که در یک پایگاه داده یا چندین پایگاه قرار گرفته‌اند را بر عهده می‌گیرد. در کوبرنتیز کانتینرهای مختلفی که مشترکاً برنامه کاربردی خاصی را شامل می‌شوند در حالت جداگانه و مستقل تحت عنوان پاد (Pod)‌ دسته‌بندی خواهند شد. این کار فرآیند مدیریت و شناسایی آن‌ها را ساده‌تر می‌کند.
کوبرنتیز کمک می‌کند تا کانتینرها در گروهی‌ از ماشین‌ها به صورت خودکار و اتوماتیک اجرا شوند، به این ترتیب به زبان ساده‌تر می‌توان گفت کوبرنتیز نقش سیستم‌عاملی را ایفا می‌کند که بر روی چندین سرور در حالت یکپارچه اجرا می‌شود. در نتیجه نیازی به نگرانی برای وضعیت ماشین‌های مختلف وجود ندارد و کاربران در حالی که هیچ تغییری در سرویس‌های اجرا شده مشاهده نمی‌کنند قابل تعامل با اپلیکیشن‌ها و سرویس‌های مورد نظر هستند.


## معماری داکر
داکر از یک معماری کلاینت-سرور استفاده میکند. کلاینت داکر با Deamon در ارتباط است که ساخت و اجرا و پخش کردن کانتینر های داکر را بر عهده دارد. بخش کلاینت و سرور ( Deamon ) داکر میتوانند روی یک کامپیوتر باشند یا به صورت Remote  روی سیستم های مجزا با یکدیگر در ارتباط باشند. در هر صورت ارتباط میان این دو همانطور که قبلا توضیح داده شد توسط یک REST API انجام می شود.

![enter image description here](https://docs.docker.com/engine/images/architecture.svg)


### (Dockerd) Deamon داکر 

به API request های داکر 
گوش میدهد و Object های داکر را مدیریت میکند. 
همچنین یک Deamon میتواند با Deamon های دیگر نیز برای مدیریت سرویس های داکر در ارتباط باشد.

### کلاینت داکر ( Docker )
دستورات را توسط REST API به Deamon میدهد و میتواند به طور همزمان با بیش از یک Deamon در ارتباط باشد.

### رجیستری های داکر
یک رجیستری داکر Image های داکر را در خود نگهداری میکند. [Docker Hub](https://hub.docker.com/) یک رجیستری پابلیک است که داکر به صورت پیش فرض از آن استفاده میکند.

<br/>

## آبجکت های داکر ( Docker Objects )
وقتی که از داکر استفاده میکنید، درواقع در حال استفاده، ساخت و یا تغییر این آبجکت ها هستید.

### Images

به Image به چشم یک نقشه‌ی اولیه برای ساخت container نگاه کنید. در Image تمامی زیرساخت های مورد نیاز تعیین و چیده می‌شوند سپس می‌توان بر روی آن Image یک Container ساخت.
یک Image در واقع یک Read-Only Template حاوی دستوراتی برای ساخت یک کانتینر داکر است. معمولا استفاده ما از Image ها به اینصورت است که با تغییر یک Image، Image دیگری را که برای ما مناسب تر است میسازیم. مثلا میتوانیم Image ای بسازیم که برپایه Image اوبونتو است اما یک سرور Apache نیز روی آن نصب میشود.
شما میتوانید از Image های آماده استفاده کنید و یا Image مناسب خود را بسازید.
برای ساختن Image جدید کافی است یک Dockerfile ساده بسازید که در آن دستوراتی نشان دهنده چگونگی ساختن و اجرا کردن Image موجود است.

وقتی که Dockerfile خود را تغییر میدهیم و Image جدیدی میسازیم، تنها بخش های جدید دوباره ساخته میشوند و این یکی از دلایل عمده سرعت و عملکرد بهتر داکر نسبت به بقیه فناوری های شبیه سازی ( Virtualization ) است.
به عبارتی image های داکر به صورت لایه لایه روی هم ساخته می‌شوند. به عنوان مثال یک image مختص Debian وجود دارد، بر روی آن یک image مختص زبان PHP اضافه می‌شود و ... 
مثال هایی از Dockerfile برای Nginx+NodeJS در پوشه‌ی مربوطه موجود است.

برای مشاهده‌ی Imageهای موجود می‌توانید از دستور زیر استفاده کنید:

<div dir = 'ltr'>

    docker images

</div>

و برای Pullکردن یک Image می‌توانید از دستور زیر استفاده کنید:


<div dir = 'ltr'>

    docker pull NAME

</div>

هم‌چنین، برای پاک‌کردن یک Image از  دستور زیر می‌توانید استفاده کنید، فقط باید توجه داشته‌باشید که ابتدا باید Containerهایی که از روی آن Image ساخته‌شده‌اند را پاک کنید:

<div dir = 'ltr'>

    docker rmi IMAGE

</div>

### Containers

Container یک Instance قابل اجرای  یک Image است. میتوان یک کانتینر را به وسیله Docker API  یا CLI ساخت، 
اجرا، حذف و یا متوقف کرد.

معمولا کانتینر ها از دیگر کانتینر های به خوبی ایزوله میشوند. شما میتوانید میزان ایزوله بودن کانتینر ها را در مواردی مانند network آنها، حافظه مورد استفاده آنها و سیستم های پایه ای مورد استفاده آنها تنظیم کنید.

یک کانتینر در واقع با Image آن و همه تنظیماتی که در زمان اجرای آن انجام میدهید تعریف میشود. هنگامی که کانتینر حذف میشود هر تغییری فایلی که در آن به وجود آمده و راهی به بیرون از کانتینر ندارد از بین میرود.


برای مشاهده‌ی لیست Containerهای فعال می‌توانید از دستور زیر استفاده کنید:

<div dir = 'ltr'>

    docker ps

</div>

و برای مشاهده‌ی تمام containerها می‌توانید از دستور زیر استفاده کنید:

<div dir = 'ltr'>

    docker ps -all

</div>

برای پاک‌کردن یک Container از دستور زیر می‌توانید استفاده کنید:

<div dir = 'ltr'>

    docker rm CONTAINER

</div>


### Container ها و Virtual machine ها

یک کانتینر به صورت native روی لینوکس اجرا میشود و به صورت مشترک با سیستم عامل از کرنل استفاده میکند. کانتیر یک پروسه مجزا را اجرا میکند و مانند یک پروسه معمولی حجم کمی از RAM  را میگیرد.
در مقابل، VM یک سیستم عامل کامل مجازی guest را با دسترسی مجازی و شبیه سازی شده به منابع اصلی سیستم  را توسط یک hypervisor اجرا میکند. VM ها مقدار بسیار زیادی سربار نسبت به حجم پروسه مورد نیاز ما برای سیستم ایجاد میکنند.

![enter image description here](https://docs.docker.com/images/Container@2x.png)

![enter image description here](https://docs.docker.com/images/VM@2x.png)

<br/>


## چگونگی استفاده از Docker و دستورات آن
### چگونه از یک Docker image کانتینر بسازیم؟
همان طور که در بالاتر گفته شد برای ساخت یک کانتینر نیاز به Image داریم. با داشتن این ایمیج و دستور docker run می توان کانتینر مورد نظر را ساخت.

<div dir = 'ltr'>
  
```
sudo docker run -d IMAGE_ID_OR_NAME
sudo docker run -itd IMAGE_ID_OR_NAME
```
</div>

در یکی از دستورات بالا از آپشن d و در دیگری از آپشن i و t و d استفاده کردیم. در docker run آپشن های دیگری نیز وجود دارد که در زیر به آن ها اشاره می کنیم:

  - ```-i``` : که stdin را حتی در صورت متصل نبودن باز نگه می دارد.
  - ```-t``` : یک tty از کانتینر می سازد.
  - ```-p``` : یک پورت از کانتینر را به یک پورت از هاست متصل می کند.
  - ```-v``` : یک مسیر از کانتینر را به یک مسیر از هاست مپ می کند.
  - ```-a``` : به STDIN و STDOUT یا STDERR متصل می شود.
  - ```-d``` : کانتینر را در بک گراند اجرا می کند.
  - ```--rm``` : به صورت اتوماتیک کانتینر را اگر وجود داشت حذف میکند.
  - ```--name``` : به کانتینر یک نام اختصاص می دهد.
  
در این آدرس می توانید لیست کاملی از آپشن های Docker run را مشاهده کنید.

https://docs.docker.com/engine/reference/run
  
### چگونه از حال یک کانتینر باخبر شویم ؟
در این قسمت می خواهیم نسان دهیم چگونه می توان از حال یک داکر باخبر شد.

با دستور ``` docker ps ``` می توان تمامی کانتینر های در حال اجرا را نشان داد. به عنوان مثال در زیر می توان دید.

<div dir = 'ltr'>
  
```
$ docker ps

CONTAINER ID        IMAGE                        COMMAND                CREATED              STATUS              PORTS               NAMES
4c01db0b339c        ubuntu:12.04                 bash                   17 seconds ago       Up 16 seconds       3300-3310/tcp       webapp
d7886598dbe2        crosbymichael/redis:latest   /redis-server --dir    33 minutes ago       Up 33 minutes       6379/tcp            redis,webapp/db
```

</div>

برای دیدن تمامی کانتینر ها  از دستور ``` sudo docker ps -a ``` استفاده می کنیم.
برای دیدن log یک کانتینر از دستور زیر استفاده می کنیم.

<div dir = 'ltr'>

``` sudo docker logs ID_OR_NAME_OF_A_CONTAINER ```

</div>

برای دیدن اطلاعات یک کانتینر خاص از دستور زیر استفاده می کنیم.

<div dir = 'ltr'>

``` sudo docker inspect ID_OR_NAME_OF_A_CONTAINER ```

</div>

برای استارت یا استاپ یا ریستارت کردن یک کانتینر از دستور های زیر استفاده می کنیم.

<div dir = 'ltr'>

```
sudo docker start ID_OR_NAME_OF_A_CONTAINER
sudo docker stop ID_OR_NAME_OF_A_CONTAINER
sudo docker restart ID_OR_NAME_OF_A_CONTAINER
```
</div>

### چگونه وارد کانتینر شویم؟
برای وارد شدن به کانتینر از دستور ``` docker exec ``` استفاده می کنیم.

<div dir = 'ltr'>
  
``` docker exec [OPTIONS] CONTAINER COMMAND [ARG...] ```

</div>

به عنوان مثال دستور  ``` $ docker exec -d ubuntu_bash touch /tmp/execWorks ``` فایل /tmp/execWorks را درون کانتینر ubuntu_bash در پس زمینه اجرا می کند.

### چگونه کانتینرمان را پاک کنیم؟
برای پاک کردن یک کانتینر از دستور docker rm استفاده می کنیم.

<div dir = 'ltr'>
 
``` sudo docker rm ID_OR_NAME_OF_A_CONTAINER ``` 

</div>

با این دستور تنها کانتینر هایی که در حالت stop هستند را می توان اجرا کرد. اگر کانتینر در حالت start بود از آپشن ``` -f ``` استفاده می کنیم.


## مزیت‌های داکر
۱ - سادگی: نصب داکر بسیار ساده است. من می‌توانم Image خود را به شما بدهم، شما آن را اجرا کنید و دقیقا همان چیزی که من run کرده‌ام را اجرا کنید.

۲- همکاری (collaboration): چند توسعه‌گر می‌توانند روی یک داکر کار کنند و نگران تفاوت‌ها و وابستگی‌ها(dependencies) و مسائل دیگر نباشند.

۳- انعطاف‌پذیری (flexibility): شما می‌تواند داکر خود را هر چیزی که خودتان می‌خواهید بسازید.

۴- جامعیت (totality): وقتی من یک برنامه را run می‌کنم و آن را به شما می‌دهم، داکر تمام مواردی را که برای اجرای برنامه به همراه ورژنی که من از آن استفاده کرده‌ام را به شما می‌دهد.

۵- تکرارپذیری:
یک برنامه‌ی جاوا در هر دستگاهی است که قادر به اجرای یک ماشین مجازی جاوا باشد، دقیقا به صورت مشابه قابل اجراست. اجرای Docker نیز همانند جاوا، در هر سیستمی که می‌تواند Docker را اجرا کند، تضمین شده است. مشخصات دقیق container در یک فایل Dockerfile ذخیره می‌شود. با توزیع این فایل در بین اعضای تیم، یک سازمان می‌تواند تضمین کند که تمام فایل‌های image ساخته شده با همان Dockerfile یکسان کار می‌کنند. علاوه بر این، داشتن محیطی ثابت و مستند، باعث می‌شود که track کردن اپلیکیشن شما و شناسایی مشکلات آسان تر شود.

۶- جداسازی:
متعلقات و تنظیمات یک container، روی برنامه‌های دیگر رایانه‌ی شما تاثیر نمی‌گذارند. حتی اگر یک container دیگر نیز همزمان درحال اجرا باشد. با استفاده از container‌های جداگانه برای هر جزء یک برنامه (به عنوان مثال یک وب سرور، رابط کاربری و یا پایگاه داده برای میزبانی یک وب‌سایت)، می‌توانید از مغایرت متعلقات جلوگیری کنید. شما همچنین می‌توانید پروژه های متعددی را در یک سرور داشته باشید بدون آنکه نگران مغایرت‌ها باشید.

۷- امنیت:
جداسازی اجزای مختلف یک برنامه بزرگ در container‌های مختلف می‌تواند مزایای امنیتی داشته باشد. برای مثال اگر یک container به خطر بیافتد دیگران امن باقی می مانند.

۸- Docker Hub:
برای موارد رایج و ساده استفاده می‌شود، مانند یک استک LAMP. توانایی ذخیره image و انتقال آن‌ها به Docker Hub به این معنی است که همیشه تعداد زیادی image که به خوبی می‌توان آن‌ها را مدیریت و کنترل کرد، در دسترس هستند. این‌که بتوانیم به راحتی یک image را دریافت و تغییر داده و آن را build کنیم، بسیار به سرعت و سهولت روند راه‌اندازی کمک می‌کند.

۹- مدیریت محیط:
Docker مدیریت و نگهداری ورژن‌های مختلف را آسان می‌کند؛ مثلا ورژن‌های مختلف وب‌سایتی که از nginx استفاده می‌کند. شما می‌توانید برای هریک از اهداف آزمایش، توسعه و تولید، یک container جداگانه در یک Linode داشته باشید و به راحتی هریک را توسعه دهید.

۱۰- یکپارچه سازی مداوم:
Docker به عنوان جزئی از سری پیوسته integration با ابزارهایی مانند Travis، Jenkins و Wercker کار می‌کند. هر بار که کد source شما به روز می شود، این ابزار می تواند نسخه جدید را به عنوان یک Docker Image ذخیره کند، آن را با یک شماره نسخه برچسب‌گذاری کرده و به Docker Hub منتقل کند، سپس آن را deploy کند.

<br/>

## نصب داکر روی لینوکس

یکی از راحت ترین روش های نصب استفاده از اسکریپت ارائه شده توسط خود داکر است

<div dir = 'ltr'>

    curl -sSL https://get.docker.com/ | sh    

</div>

پس از آن میتوانید برای اینکه بتوانید بدون استفاده از دسترسی superuser (sudo) از داکر استفاده کنید، user خود را به گروه داکر اضافه کنید:

<div dir="ltr">

    sudo usermod -aG docker $USER
    
</div>

برای اطمینان یک بار logout کنید و سپس دوباره وارد شوید   تا دسترسی ها آپدیت شوند و یا اگر از اوبونتو استفاده میکنید با انجام دستور زیر این کار را انجام دهید:

<div dir="ltr">
       
    newgrp docker

</div>


حال برای تست کردن میتوانید دستور زیر را اجرا کنید:

<div dir="ltr">

    docker run hello-world
    
</div>

که خروجی مشابه زیر می‌دهد:

<div dir="ltr">

    // Unable to find image 'hello-world:latest' locally
    // latest: Pulling from library/hello-world
    // ca4f61b1923c: Pull complete
    // Digest: sha256:ca0eeb6fb05351dfc8759c20733c91def84cb8007aa89a5bf606bc8b315b9fc7
    // Status: Downloaded newer image for hello-world:latest
    // Hello from Docker!   
    // This message shows that your installation appears to be working correctly.
    
</div>

<br/>

## نصب داکر ورژن دسکتاپ روی مک و ویندوز
داکر یک ورژن دسکتاپ برای مک و ویندوز دارد که کار را برای مدیریت container ها و app های مختلف بسیار آسان تر می‌کند که می‌توانید آن را برای سیستم عامل خود از این لینک دانلود کنید:
<div dir="ltr">
    
    https://docker.com/products/docker-desktop
    
</div>

<br/>

## چگونه باید اپلیکیشن خود را به یک Container اضافه کنیم (چگونه Image خود بسازیم)؟


زمانی که شما container مورد نظر خودتان رو پیدا کردید قطعا میخواهید آن را customize کنید و dependency های خودتان رو به 
آن اضافه کنید . اینجا جاییست که Dockerfile مورد استفاده قرار میگیرد.

داکرفایل مشخص میکند که کانتینر شما چگونه باشد، یعنی از چه Image ای به عنوان پایه استفاده کند و چه تغییراتی روی آن اعمال کند و هنگام اجرا چه دستوراتی را اجرا کند.

در زیر یک داکرفایل نمونه به همراه توضیحات آن آمده است:

<div dir="ltr">

```dockerfile
    # Use the official Node.js runtime as a base image
    FROM node:alpine

    # Set the directory of my web application to /app
    WORKDIR /app

    # Copy over my project’s directory into the container /app folder
     Add . /app

    # Install all the dependencies for my web application
     RUN yarn install

    # Make the port 3000 accessible outside of Docker
     EXPOSE 3000

    # Execute the command yarn start
     CMD ["yarn", "start"]  

```
</div>

از روی این داکرفایل یک Image جدید ساخته شده و اجرا میشود. میتوان از روی یک Image که در اینجا بصورت داکر فایل است هر تعدادی Container ساخت.

با ساختن یک Image که تنظیمات شخصی خود را روی آن اعمال میکنیم، میتوانیم هر بار این کانتینر با تنظیمات شخصی سازی شده را بدون دوباره کاری اجرا کنیم.

در واقع Dockerfile شامل چند خط می‌باشد که هر خط شامل یک INSTRUCTION که تمامی حروف آن بزرگ و یک 
می‌باشد.
دستور FROM باید به یک OS و یا یک IMAGE دیگر اشاره کند. تمامی داکرفایل‌ها باید با دستور FROM شروع شوند.
دستور RUN دستوری که به عنوان ARGUMENT به آن داده می‌شود را اجرا می‌کند.
دستور COPY فایل‌ها را لوکال‌سیستم به IMAGE کپی می‌کند.



</div>
