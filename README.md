# מרכז בקרת סוכנים — shaul44.github.io

דף launcher סטטי המתארח על GitHub Pages, עם שער כניסה דרך Google וכפתורים לכל סוכן.

## Google Sign-In — כבר מוגדר

הפרויקט `worldcup-7ac6c` ב-Google Cloud מחזיק את ה-Client ID של הדף (`מרכז בקרת סוכנים`,
מסתיים ב-`...aheq`), מוגדר עם Authorized JavaScript origin ל-`https://shaul44.github.io`.
רשימת `ALLOWED_EMAILS` בקובץ `index.html` קובעת אילו כתובות Gmail יכולות להיכנס.

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
| מרכז בקרת סוכנים (Dashboard/Broker/QA) | `https://147-93-58-13.sslip.io` | ציבורי ופעיל — תעודת Let's Encrypt אמיתית דרך Traefik/Coolify, מוגן ב-Google login (`Agents Hub OAuth` client) |

`hermesvip.tech` הוסר מהתוכנית לפי החלטת בעלים — הדומיין הישן לא בשימוש יותר, כל הגישה
עוברת דרך `147-93-58-13.sslip.io` (subdomain ציבורי חינמי שמתעדכן אוטומטית ל-IP של השרת).

הדשבורד המלא (Password Broker, QA Agent, Deploy/Rollback) נמצא כטאבים בתוך אותו דף אחד אחרי
כניסה — אין endpoint נפרד לכל אחד.
