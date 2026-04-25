# 📋 ინსტრუქციები საიტის პროგრამისტებისთვის

## 🎯 ამოცანა: ვაკანსიის გვერდის ატვირთვა საიტზე

გამარჯობა! აქ არის სრულად მზა HTML ფაილი, რომელიც უნდა გამოქვეყნდეს საიტზე. დიდი ცვლილებები არ გჭირდებათ — მხოლოდ რამდენიმე მარტივი ნაბიჯი.

---

## 📁 ფაილები

- **`team-development-manager.html`** — სრული, მზა ვაკანსიის გვერდი

---

## 🚀 გამოქვეყნების ნაბიჯები

### ნაბიჯი 1: ფაილის ატვირთვა

ატვირთეთ `team-development-manager.html` ფაილი საიტზე შემდეგ URL-ზე:

```
www.farmasi.ge/careers/team-development-manager
```

შესაბამისად:
- შექმენით ახალი საქაღალდე `/careers/`
- მის შიგნით — `/careers/team-development-manager/`
- ფაილის სახელი შეცვალეთ `index.html`-ზე

ანდა, CMS-ის მიხედვით (WordPress, Drupal, etc.) — შექმენით ახალი გვერდი შესაბამისი URL slug-ით.

---

### ნაბიჯი 2: მოკლე რედირექტის დაყენება

`.htaccess` ფაილში (Apache სერვერებისთვის) დაამატეთ:

```apache
Redirect 301 /tdm /careers/team-development-manager
```

ან Nginx-ისთვის:

```nginx
location = /tdm {
    return 301 /careers/team-development-manager;
}
```

**შედეგი:** `www.farmasi.ge/tdm` გადაამისამართებს მთავარ გვერდზე.

---

### ნაბიჯი 3: Google Analytics-ის ჩართვა (თუ არ არის)

ფაილში უკვე ჩასმულია `trackApplyClick()` ფუნქცია, რომელიც აგზავნის event-ებს Google Analytics-ში (GA4 და Universal Analytics).

თუ საიტზე **GA ჯერ არ არის ჩართული**, `<head>` ტეგში, `<title>`-ის წინ, დაამატეთ:

```html
<!-- Google Analytics 4 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

*`G-XXXXXXXXXX` შეცვალეთ თქვენი GA Measurement ID-ით*

---

### ნაბიჯი 4: ტესტი

გამოქვეყნების შემდეგ შეამოწმეთ:

- ✅ გვერდი იხსნება სწორ URL-ზე
- ✅ `/tdm` რედირექტი მუშაობს
- ✅ "განცხადების შევსება" ღილაკი ხსნის Google Form-ს ახალ tab-ში
- ✅ მობილურზე ნორმალურად გამოიყურება
- ✅ ქართული ტექსტი სწორად ჩანს
- ✅ ღილაკები 3 ადგილას გამოჩენილია (ზემოთ, შუაში, ბოლოში)
- ✅ მობილურზე sticky ღილაკი ქვემოთ ჩანს

---

## 🎨 ფაილის ტექნიკური დეტალები

### რა არის მზა:
- ✅ სრული HTML + CSS ერთ ფაილში (არ სჭირდება ცალკე CSS ან JS ფაილები)
- ✅ Mobile-responsive დიზაინი
- ✅ SEO-ოპტიმიზირებული (Meta tags, Open Graph, Schema.org JobPosting)
- ✅ Google Analytics event tracking
- ✅ 3 CTA ღილაკი + sticky ღილაკი მობილურზე
- ✅ Farmasi-ს ბრენდის ფერები (ვარდისფერი #EC008C)
- ✅ Noto Georgian ფონტები (Google Fonts-დან)
- ✅ Animation და hover ეფექტები
- ✅ Accessibility-მეგობრული (ALT ტეგები, semantic HTML)

### რას არ საჭიროებს:
- ❌ ცალკე CSS ფრეიმვორკი (არ გჭირდება Bootstrap, Tailwind, etc.)
- ❌ JavaScript ბიბლიოთეკა (არ გჭირდება jQuery, React, etc.)
- ❌ build პროცესი (არ გჭირდება webpack, etc.)

---

## 🔗 მნიშვნელოვანი ბმულები ფაილში

ფაილში უკვე ჩასმულია შემდეგი ბმულები:

**Google Forms (განცხადების შევსება):**
```
https://docs.google.com/forms/d/e/1FAIpQLSdQvMb1QrO5OJ0lSDlKb3HjNHpYXDeMoEj5Kpd_CFsOVUidpg/viewform
```

**ელფოსტა (დამატებითი ინფორმაცია):**
```
info@farmasi.ge
```

თუ ეს ბმული/ელფოსტა შეიცვალა — ფაილში გლობალურად ჩაანაცვლეთ (Ctrl+H).

---

## 🎯 თუ რაიმე პრობლემაა

### პრობლემა: ქართული ფონტი არ ჩანს
**გამოსავალი:** შეამოწმეთ, რომ `<head>`-ში Google Fonts preconnect-ები და link-ი შენარჩუნებულია:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+Georgian..." rel="stylesheet">
```

### პრობლემა: მობილურზე ლეიაუტი არ მუშაობს
**გამოსავალი:** `<meta name="viewport" content="width=device-width, initial-scale=1.0">` უნდა იყოს `<head>`-ში.

### პრობლემა: ღილაკი Google Form-ს არ ხსნის
**გამოსავალი:** შეამოწმეთ, რომ `href` ატრიბუტში Google Forms-ის სრული URL-ია, `target="_blank"` და `rel="noopener"`.

---

## 📊 SEO რეკომენდაცია

გამოქვეყნების შემდეგ:

1. **Google Search Console-ში** დაამატეთ ახალი URL ინდექსირებისთვის
2. **sitemap.xml**-ში ჩაამატეთ ახალი გვერდი:
   ```xml
   <url>
     <loc>https://www.farmasi.ge/careers/team-development-manager</loc>
     <lastmod>2026-04-24</lastmod>
     <priority>0.8</priority>
   </url>
   ```
3. **Google Jobs**-ში ავტომატურად გამოჩნდება Schema.org JobPosting-ის წყალობით

---

## 📞 საკონტაქტო ინფორმაცია

თუ რაიმე შეკითხვა გაქვთ:
- 📧 info@farmasi.ge

---

## ✅ საბოლოო checklist

- [ ] ფაილი ატვირთულია `/careers/team-development-manager` URL-ზე
- [ ] `/tdm` რედირექტი მუშაობს
- [ ] Google Analytics ჩართულია
- [ ] გვერდი მობილურზე სწორადაა
- [ ] "განცხადების შევსება" ღილაკი მუშაობს
- [ ] sitemap.xml განახლებულია
- [ ] Google Search Console-ში URL დამატებულია

---

**მადლობა!** 🙏
