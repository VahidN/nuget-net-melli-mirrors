# 📦 nuget-net-melli-mirrors

آینه‌های داخلی NuGet برای توسعه‌دهندگان دات‌نت در ایران  
**زمانی که دسترسی به اینترنت بین‌الملل ندارید، این مخزن به کمک شما می‌آید.**

---

## 🎯 هدف

برنامه‌نویسان دات‌نت ایرانی در شرایط قطعی یا محدودیت اینترنت، می‌توانند با استفاده از آینه‌های (mirror) داخلی، پکیج‌های مورد نیاز خود را بدون مشکل دریافت کنند.  
این مخزن لیستی از معتبرترین و فعال‌ترین میرورهای NuGet داخل ایران را گردآوری کرده و یک فایل `nuget.config` آماده در اختیار شما می‌گذارد.

> **نکته مهم:** همیشه بهتر است ابتدا از **کش محلی** (Local Cache) استفاده کنید تا سرعت و پایداری بالاتری داشته باشید.

---

## 🗂 لیست آینه‌های NuGet داخلی

| نام منبع | آدرس (URL) | مرجع |
| -------- | ---------- | ----- |
| **ChabokMirror** | `https://mirror2.chabokan.net/nuget/v3/index.json` | [iran.chabokan.net](https://iran.chabokan.net/) |
| **DevNeeds** | `https://nuget.devneeds.ir/repository/nuget/index.json` | [devneeds.ir](https://devneeds.ir/) |
| **ParspackMirror** | `https://mirror.abrha.net/repository/nuget/index.json` | [docs.parspack.com](https://docs.parspack.com/reference/mirror/nuget/) |
| **RunFlare** | `https://mirror-nuget.runflare.com/v3/index.json` | [runflare.com/mirrors](https://runflare.com/mirrors/) |
| **Liara** | `https://package-mirror.liara.ir/repository/nuget/index.json` | [docs.liara.ir/mirrors/nuget](https://docs.liara.ir/mirrors/nuget/) |
| **Hamravesh** | `https://repo.hmirror.ir/nuget` | [hamravesh.com/blog](https://hamravesh.com/blog/container-registry-mirroring-and-caching/) |
| **IranServer** | `https://nuget.iranserver.com/repository/nuget/index.json` | [mirror.iranserver.com](https://mirror.iranserver.com/#nuget) |
| **NugetIran** | `https://repo.nugetiran.ir/repository/nuget/index.json` | [nugetiran.ir](https://nugetiran.ir/) |

---

## ⚙️ فایل آماده `nuget.config`

برای استفاده همزمان از تمام آینه‌ها (و همچنین کش محلی)، فایل زیر را در ریشه پروژه یا پوشه `%AppData%\NuGet\` قرار دهید:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <packageSources>
    <add key="LocalPackages" value="%USERPROFILE%\.nuget\packages" />
    <add key="ChabokMirror" value="https://mirror2.chabokan.net/nuget/v3/index.json" />
    <add key="DevNeeds" value="https://nuget.devneeds.ir/repository/nuget/index.json" />
    <add key="ParspackMirror" value="https://mirror.abrha.net/repository/nuget/index.json" />
    <add key="RunFlare" value="https://mirror-nuget.runflare.com/v3/index.json" />
    <add key="Liara" value="https://package-mirror.liara.ir/repository/nuget/index.json" />
    <add key="Hamravesh" value="https://repo.hmirror.ir/nuget" />
    <add key="IranServer" value="https://nuget.iranserver.com/repository/nuget/index.json" />
    <add key="NugetIran" value="https://repo.nugetiran.ir/repository/nuget/index.json" />
  </packageSources>
</configuration>
```
💡 اگر از یکی از توزیع‌های لینوکس استفاده می‌کنید، سطر ذيل را از فایل فوق پاک کنید، يا حتی می‌توانید مقدار `%USERPROFILE%` را به `$HOME` تغییر دهید:

```xml
<add key="LocalPackages" value="%USERPROFILE%\.nuget\packages" />
```
و مابقی را در ریشه‌ی پروژه و یا در مسیر زیر ذخیره کنید:

`HOME/.nuget/NuGet$`


---

## ⌨️ دستورات خط فرمان (هر منبع جداگانه)

اگر ترجیح می‌دهید هر منبع را به صورت مستقل امتحان کنید، دستورات زیر را اجرا نمایید.  
(پرچم `--ignore-failed-sources` خطاهای مربوط به عدم دسترسی به یک منبع را نادیده می‌گیرد و `-v diag` خروجی جزیی نشان می‌دهد.)

### 1. کش محلی (Local Cache)
```bash
dotnet restore --ignore-failed-sources -v diag --source %USERPROFILE%\.nuget\packages
```

### 2. چابکان (ChabokMirror)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://mirror2.chabokan.net/nuget/v3/index.json
```

### 3. DevNeeds
```bash
dotnet restore --ignore-failed-sources -v diag --source https://nuget.devneeds.ir/repository/nuget/index.json
```

### 4. پارس پک (ParspackMirror)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://mirror.abrha.net/repository/nuget/index.json
```

### 5. ران فلر (RunFlare)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://mirror-nuget.runflare.com/v3/index.json
```

### 6. لیارا (Liara)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://package-mirror.liara.ir/repository/nuget/index.json
```

### 7. هم‌روش (Hamravesh)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://repo.hmirror.ir/nuget
```

### 8. ایران سرور (IranServer)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://nuget.iranserver.com/repository/nuget/index.json
```

### 9. ایران نيوگت (NugetIran)
```bash
dotnet restore --ignore-failed-sources -v diag --source https://repo.nugetiran.ir/repository/nuget/index.json
```

> 💡 **یک دستور برای همه منابع** (با استفاده از فایل `nuget.config` بالا):
> ```bash
> dotnet restore --ignore-failed-sources -v diag
> ```

---

## 🚀 راه‌اندازی یک‌بار برای همیشه (اختیاری)

برای جلوگیری از تایپ مکرر `--ignore-failed-sources`، می‌توانید با ایجاد فایل `Directory.Build.props` در ریشه پروژه، این تنظیم را به صورت سراسری اعمال کنید:

```xml
<Project>
  <PropertyGroup>
    <RestoreIgnoreFailedSources>true</RestoreIgnoreFailedSources>
  </PropertyGroup>
</Project>
```

سپس دیگر نیازی به ذکر `--ignore-failed-sources` در دستور `dotnet restore` نیست.

---

## 🚫 غیرفعال‌سازی موقت NuGet Audit (افزایش سرعت)

قابلیت NuGet Audit در شرایط اینترنت داخلی ضرورتی ندارد و می‌توانید برای افزایش سرعت عملیات restore آن را غیرفعال کنید:

**در PowerShell:**
```powershell
$env:NuGetAudit="false"
```

**در Command Prompt (CMD):**
```cmd
set NuGetAudit=false
```

(این دستور در همان ترمینال جاری اثر می‌کند. برای دائمی کردن آن، متغیر محیطی را در سیستم تنظیم کنید.)


---

## 🔧 به‌روزرسانی ابزارهای دات‌نت (Dotnet Tools)

ابزارهای خط فرمان دات‌نت (مانند `dotnet-ef`، `swashbuckle` و غیره) نیز برای نصب و به‌روزرسانی نیاز به دسترسی به منابع NuGet دارند. برای اطمینان از کارکرد در شرایط داخلی، از دستور زیر استفاده کنید:

```bash
dotnet tool restore --ignore-failed-sources --add-source %USERPROFILE%\.nuget\packages -v diag
```

> می‌توانید به جای `--add-source` چندین بار از این سوئیچ استفاده کنید یا منابع دیگر (مانند DevNeeds، Liara و ...) را نیز اضافه نمایید.

---

## ➕ اضافه کردن یک بسته جدید (Add Package)

برای نصب و اضافه کردن یک بسته NuGet به پروژه، می‌توانید از کش محلی یا یکی از آینه‌های داخلی استفاده کنید:

**استفاده از کش محلی:**
```bash
dotnet add package MyPackageName --source %USERPROFILE%\.nuget\packages
```

**استفاده از یک آینه داخلی (مثال با DevNeeds):**
```bash
dotnet add package MyPackageName --source https://nuget.devneeds.ir/repository/nuget/index.json
```

---


## 📌 یافتن بسته‌های منقضی‌شده (Outdated Packages)

برای مشاهده پکیج‌هایی که نسخه جدیدتری از آن‌ها در میرورهای داخلی موجود است، از دستور `dotnet list package --outdated` همراه با تعیین صریح منابع استفاده کنید. مثال زیر از دو منبع DevNeeds و ParspackMirror استفاده می‌کند:

```bash
dotnet list package --outdated --source https://nuget.devneeds.ir/repository/nuget/index.json --source https://mirror.abrha.net/repository/nuget/index.json
```

> **توجه:** این دستور برخلاف `dotnet restore` از فایل `nuget.config` به طور کامل تبعیت نمی‌کند؛ بنابراین تعیین مستقیم `--source` ضروری است.

---

## 🧰 آینه SDK (مرجع دانلود مستقیم)

علاوه بر پکیج‌های NuGet، امکان دانلود مستقیم و به‌روز **ابزارهای توسعه (SDK)** نیز از طریق مخزن [DntSdkMirror](https://github.com/VahidN/DntSdkMirror) فراهم شده است. این مخزن هر روز به صورت خودکار تغییرات رسمی مایکروسافت را چک کرده و آخرین نسخه SDK را در خود ذخیره می‌کند.

---


## 🤝 نحوه مشارکت (Contribution)

اگر آینه جدید و معتبر دیگری از NuGet در داخل ایران سراغ دارید که در این لیست نیست، لطفاً در بخش **Issues** همین مخزن عنوان کنید تا پس از بررسی اضافه شود.  
همچنین در صورت عدم کارکرد هر یک از لینک‌ها، ما را مطلع سازید.

> **تذکر:** لطفاً تنها آدرس‌هایی را معرفی کنید که به صورت عمومی و رایگان در دسترس هستند.

---

## 📄 مجوز

این مخزن یک مجموعه اطلاعاتی آزاد است و تحت Licenses MIT منتشر می‌شود.

---

**با تشکر از همه توسعه‌دهندگان دات‌نت ایرانی ❤️**
