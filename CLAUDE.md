# CLAUDE.md — caissaviva-website

## Contexto del Proyecto

Sitio web oficial de la **Fundación CaissaViva**, ONG de ajedrez educativo en República Dominicana, enfocada en niños y jóvenes de 5 a 18 años.

- **Dominio:** caissaviva.com
- **Hosting:** GitHub Pages (gratuito)
- **Registrador DNS:** GoDaddy
- **Cuenta GitHub:** Pacosbell-ai
- **Repositorio:** https://github.com/Pacosbell-ai/caissaviva-website
- **Rama principal:** `main`
- **Responsable:** Omar A. Martinez — Fundador (`omartinez@gmh.do`)

---

## Arquitectura del Sitio

Sitio **estático multi-idioma** servido directamente desde GitHub Pages. HTML + CSS + JS en un solo archivo por idioma (sin build step, sin framework, sin dependencias).

```
caissaviva-website/
├── index.html              ← Español (default, caissaviva.com/)
├── logo.png                ← Logo compartido por todas las versiones
├── en/
│   └── index.html          ← English (caissaviva.com/en/)
├── fr/
│   └── index.html          ← Français (caissaviva.com/fr/)
├── CLAUDE.md               ← Este archivo
└── SESSION-LOG.md          ← Historial detallado de cambios por sesión
```

### Convenciones

- **Idioma por defecto:** Español (raíz del sitio)
- **Versiones traducidas:** Subdirectorios `en/` y `fr/`
- **Referencia al logo:** Desde subdirectorios usar `../logo.png`, desde raíz usar `logo.png`
- **IDs de sección:** Traducidos por idioma (ej. `#contacto` en ES, `#support` en EN, `#soutien` en FR)
- **Selector de idioma:** Presente en el nav de las 3 versiones con enlaces cruzados
- **Formulario:** FormSubmit.co (sin cuenta) → `fundacion@caissaviva.com`. El campo `_subject` identifica el idioma del origen

---

## Paleta de colores (extraída del logo)

| Color       | Hex       | Uso                                      |
|-------------|-----------|------------------------------------------|
| Navy oscuro | `#1B2A4A` | Fondo principal, navbar, secciones oscuras |
| Navy claro  | `#243656` | Acentos de fondo                         |
| Navy dark   | `#111D33` | Fondos muy oscuros                       |
| Dorado      | `#D4952A` | CTAs, acentos, labels                    |
| Dorado claro| `#E8B85E` | Hover states, highlights                 |
| Dorado dark | `#B07A1E` | Hover de links                           |
| Crema       | `#F5EDE0` | Fondo de secciones claras                |
| Crema claro | `#FDF9F3` | Fondo del body                           |

**Tipografías:** Cinzel (títulos) + Inter (cuerpo) — desde Google Fonts.

---

## Estructura de contenido (común a los 3 idiomas)

1. **Hero** — Logo, tagline, CTAs principales
2. **Misión** — Descripción + 4 valores (Pensamiento Estratégico, Disciplina, Resiliencia, Inclusión)
3. **Programas** — 4 tarjetas por grupo de edad:
   - 3–5 años: Iniciación Lúdica
   - 6–10 años: Fundamentos del Ajedrez
   - 11–14 años: Desarrollo Competitivo
   - 15–18 años: Alto Rendimiento
4. **Stats bar** — 5–18 años / FIDE / RD
5. **Visión / Expansión** — 6 iniciativas estratégicas (escuelas públicas, circuito nacional, plataforma digital, becas, campamentos, formación de instructores)
6. **Contacto / Apóyanos** — Info de contacto + formulario FormSubmit
7. **Footer** — Navegación secundaria + copyright

---

## Datos de contacto

| Campo        | Valor                                                    |
|--------------|----------------------------------------------------------|
| Email        | fundacion@caissaviva.com                                 |
| Teléfono     | +1 (849) 357-7625                                        |
| Ubicación    | Santo Domingo, República Dominicana                      |
| Instructor   | Freddy Alberto Gil — Instructor FIDE, Árbitro Nacional y FIDE |

---

## DNS y correo (NO MODIFICAR)

El dominio tiene registros MX/SPF/DKIM/DMARC configurados para **Microsoft 365**. No tocar estos registros al hacer cambios en GoDaddy:

- MX → `caissaviva-com.mail.protection.outlook.com`
- SPF: `v=spf1 include:spf.protection.outlook.com -all`
- DKIM: `selector1._domainkey`, `selector2._domainkey`
- DMARC: `v=DMARC1; p=reject; ...`
- Autodiscover, enterpriseenrollment, enterpriseregistration (Intune/Azure AD)

Los 4 registros A del apex (`@`) apuntan a GitHub Pages:
- `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- CNAME `www` → `pacosbell-ai.github.io`

---

## Flujo de trabajo

### Para actualizar el sitio

**Opción A — GitHub Desktop / terminal (preferida):**
1. Clone local en: `C:\Users\OmarAMartinez\OneDrive - Major Logistics SRL\Documents\06 APLICACIONES\Repositorio\GitHub\caissaviva-website`
2. Editar archivos localmente
3. `git add .` → `git commit` → `git push`
4. GitHub Pages regenera en 1-2 minutos

**Opción B — GitHub web:**
1. Ir al repo → archivo → lápiz → editar → Commit changes

### Al hacer cambios de contenido/estructura

- **Mantener paridad entre las 3 versiones de idioma.** Si cambia la estructura en `index.html`, replicar en `en/index.html` y `fr/index.html`.
- **No crear nuevos archivos de documentación (`.md`) a menos que el usuario lo pida.**
- **Al agregar secciones nuevas:** actualizar nav, footer links y los 3 idiomas.

### Activación de FormSubmit tras cambios en formulario

Si se cambia la dirección de destino del formulario, el primer envío genera un email de confirmación de FormSubmit que debe activarse una vez.

---

## Notas para Claude

- Los archivos HTML son **autocontenidos** (CSS y JS inline). No fragmentar en archivos separados sin razón estructural fuerte.
- El sitio no tiene build step. Cualquier cambio va directo a producción al hacer push.
- Al sugerir mejoras, priorizar: accesibilidad (a11y), SEO, performance (el sitio ya es ligero), y paridad de idiomas.
- **Idioma de las conversaciones:** Español por defecto (preferencia del usuario).
- **Formato de respuestas:** Markdown conciso, sin formato excesivo en respuestas cortas.
