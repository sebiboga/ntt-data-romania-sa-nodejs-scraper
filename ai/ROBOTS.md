# Robots.txt Analysis — NTT DATA Careers

Sursa: https://careers.nttdata.ro/robots.txt

## Reguli

```
User-agent: *
Disallow: /
```

## Interpretare

| Cale | Accesibil? | Ce conține |
|---|---|---|
| `/` | Disallowed | Tot site-ul |
| `/search/` | Disallowed | Pagina de căutare job-uri de unde scraper-ul extrage datele |

## Recomandare

robots.txt NU este legal binding, dar reprezintă intenția proprietarului site-ului.

- Pagina de căutare `/search/` e **disallowed** de robots.txt. În practică, serverul răspunde cu 200 OK cu `User-Agent` normal și fără autentificare.
- Paginile individuale de job sunt și ele disallowed. Noi nu le scraper-uim direct — doar le verificăm accesibilitatea (HEAD request) în teste.
- Scraperul curent face o singură cerere per pagină (25 job-uri) cu delay de 1s între pagini — comportament rezonabil, nu agresiv.

**Concluzie**: Risc minim. Paginile sunt publice și răspund fără autentificare, iar scraperul e politicos (rate limiting, User-Agent standard, o singură cerere simultană).
