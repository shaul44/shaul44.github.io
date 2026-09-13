# מרכז בקרת סוכנים — shaul44.github.io

דף launcher סטטי המתארח על GitHub Pages, עם שער כניסה דרך Google וכפתורים לכל סוכן.

## הגדרת Google Sign-In (חובה לפני שימוש)

1. גשו ל-[console.cloud.google.com](https://console.cloud.google.com)
2. צרו פרויקט חדש (למשל `hermesvip-dashboard`)
3. **APIs & Services → OAuth consent screen** — צרו מסך הסכמה מסוג External עם פרטים בסיסיים בלבד
4. **Credentials → Create Credentials → OAuth client ID → Web application**
   - Authorized JavaScript origins: `https://shaul44.github.io`
5. העתיקו את ה-Client ID (מסתיים ב-`.apps.googleusercontent.com`) והדביקו אותו במקום
   `YOUR_GOOGLE_CLIENT_ID.apps.googleusercontent.com` בקובץ [index.html](index.html)
6. ברשימת `ALLOWED_EMAILS` בקובץ `index.html` הוסיפו/עדכנו את כתובות ה-Gmail המורשות להיכנס

## ⚠️ מגבלת אבטחה חשובה

זהו אתר סטטי בלבד (ללא backend). בדיקת ה-email המורשה מתבצעת **בצד הלקוח** (בקוד ה-JavaScript
שכל אחד יכול לצפות בו). זו הגנה נוחה מפני משתמשים אקראיים, אבל **לא הגנה אמיתית** מפני מישהו
שמתעסק בכוונה עם קוד הדפדפן. אל תניחו מאחורי המסך הזה מידע רגיש באמת — לאבטחה אמיתית יש להוסיף
אימות בצד שרת (למשל דרך Vercel Serverless Functions או Cloudflare Workers שמאמתים את ה-JWT).

## סטטוס הסוכנים בזמן הכתיבה

| סוכן | כתובת | סטטוס |
|---|---|---|
| Email AI Agent | `http://147.93.58.13:8085` | ציבורי ופעיל |
| Langfuse | `https://langfuse.147-93-58-13.sslip.io` | ציבורי ופעיל |
| Domain Agent / hermesvip.tech | — | בתחזוקה: הדומיין לא resolve-able (NXDOMAIN), הפריסה האחרונה נכשלה (503) |
| Dashboard API | `127.0.0.1:8999` | פנימי בלבד, לא חשוף לאינטרנט |
| Password Broker | `127.0.0.1:5001` | פנימי בלבד, לא חשוף לאינטרנט |
| QA Agent | `127.0.0.1:5002` | פנימי בלבד, לא חשוף לאינטרנט |

כדי לחשוף את הסוכנים הפנימיים בבטחה יש להוסיף reverse proxy עם HTTPS ו-אימות, ולתקן את
צינור הפריסה השבור של `domain-agent` (יש בעיית checksum/QA endpoint mismatch שתועדה בנפרד) —
זו עבודה נפרדת ומורכבת יותר מהקמת הדף הזה.
