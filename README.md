# 🚀 NEON RUNNER 3D

Joc arcade 3D d'estètica neó fet amb **Three.js**, en **un únic fitxer HTML** (HTML + CSS + JavaScript). Sense instal·lacions, sense dependències locals i sense fitxers d'àudio: tot el so es genera amb la Web Audio API.

Pilotes una nau futurista que avança sola per una pista espacial suspesa al buit. Esquiva obstacles, salta barreres, recull orbes d'energia i aguanta com més temps puguis mentre la velocitat no deixa de pujar.

## ✨ Característiques

- Escena 3D amb llum ambiental, llum direccional amb ombres suaus i boira (`FogExp2`).
- Pista amb línies en moviment, vores lluminoses, pilars de neó i estels passant a gran velocitat.
- Nau detallada (xassís, morro, cabina, ales i propulsors amb flama) amb inclinació (`roll` i `pitch`).
- **Obstacles:** murs alts, blocs baixos (saltables), barreres laterals mòbils i barreres verticals que pugen i baixen.
- **Orbes d'energia** que sumen punts i recarreguen el turbo.
- **Turbo (dash)** amb invulnerabilitat breu, puntuació doble i temps de recàrrega.
- Dificultat progressiva: la velocitat i els patrons evolucionen amb el nivell.
- HUD: puntuació, rècord, nivell/velocitat, barra de turbo, pausa i silenci.
- Rècord guardat a `localStorage`.
- Àudio sintètic (orbes, salt, turbo, xoc) amb botó per silenciar.
- Controls tàctils per a mòbil i tauleta.
- Bucle amb *delta time*: mateixa velocitat a 60, 120 o 144 Hz.

## 🎮 Controls

| Acció | Teclat | Mòbil |
|---|---|---|
| Moure's a l'esquerra / dreta | `A` / `D` o `←` / `→` | Botons ◀ ▶ |
| Saltar | `Espai`, `↑` o `W` | Botó ▲ |
| Turbo | `Shift` | Botó ⚡ |
| Pausa | `P` o `Esc` | Botó ⏸ |
| Començar / reintentar | `Enter` o `Espai` | Botó en pantalla |

## 📦 Instal·lació i execució

No cal instal·lar res. Només necessites un navegador modern amb WebGL i **connexió a internet** (Three.js es carrega des de cdnjs).

### Opció 1: obrir-lo directament

1. Descarrega o clona el repositori.
2. Fes doble clic a `neon-runner-3d.html`.

### Opció 2: servidor local (opcional)

Si preferixes servir-lo per HTTP:

```bash
# Python 3
python -m http.server 8000

# o amb Node.js
npx serve .
```

Obre després `http://localhost:8000/neon-runner-3d.html`.

## 🌐 Publicar a GitHub

### 1. Crear el repositori i pujar el codi

```bash
git init
git add neon-runner-3d.html README.md
git commit -m "Primera versió de Neon Runner 3D"
git branch -M main
git remote add origin https://github.com/<el-teu-usuari>/neon-runner-3d.git
git push -u origin main
```

> Substitueix `<el-teu-usuari>` pel teu nom d'usuari de GitHub i crea abans el repositori buit a [github.com/new](https://github.com/new).

### 2. Activar GitHub Pages (per jugar des del navegador)

1. Canvia el nom del fitxer perquè GitHub Pages el serveixi com a pàgina principal:
   ```bash
   git mv neon-runner-3d.html index.html
   git commit -m "Renombra a index.html per a GitHub Pages"
   git push
   ```
2. Al repositori, ves a **Settings → Pages**.
3. A *Build and deployment*, tria **Deploy from a branch**, la branca `main` i la carpeta `/ (root)`.
4. Desa els canvis. Al cap d'uns minuts el joc estarà disponible a:
   ```
   https://<el-teu-usuari>.github.io/neon-runner-3d/
   ```

## 🗂️ Estructura

```
neon-runner-3d/
├── index.html      # El joc complet (HTML + CSS + JS)
└── README.md
```

## 🛠️ Personalització ràpida

Tot es pot ajustar editant les constants i funcions del fitxer:

| Què vols canviar | On |
|---|---|
| Posició i nombre de carrils | `LANES` |
| Durada i recàrrega del turbo | `DASH_DUR`, `DASH_CD` |
| Velocitat inicial i màxima | `update()` → `Math.min(22 + G.time * .55, 62)` |
| Temps entre nivells | `update()` → `G.time / 20` |
| Altura del salt | `jump()` → `P.vy = 12` i gravetat a `updateShip()` |
| Distància entre files d'obstacles | `update()` → `Math.max(16, 34 - G.level * 2)` |
| Patrons d'obstacles | `spawnRow()` |
| Colors i materials | `MAT`, `buildShip()` |

## 🧰 Tecnologies

- [Three.js](https://threejs.org/) r128 (CDN de cdnjs)
- Web Audio API
- `localStorage` per al rècord
- HTML5 / CSS3 / JavaScript (ES6+)

## 🌍 Compatibilitat

Chrome, Edge, Firefox i Safari recents, tant d'escriptori com de mòbil. Cal tenir WebGL activat. L'àudio s'activa després de la primera interacció (per política dels navegadors).

## 🐞 Problemes habituals

- **Pantalla en negre:** comprova la connexió a internet (Three.js es carrega des del CDN) i que WebGL estigui activat al navegador.
- **No se sent el so:** fes clic o prem una tecla dins la pàgina i comprova que el botó 🔊 no estigui silenciat.
- **El rècord no es desa:** el mode privat o el bloqueig de dades del navegador pot impedir l'ús de `localStorage`.

## 🤝 Contribuir

Les propostes són benvingudes:

1. Fes un *fork* del repositori.
2. Crea una branca: `git checkout -b feature/nova-funcionalitat`
3. Fes *commit* dels canvis: `git commit -m "Afegeix nova funcionalitat"`
4. Puja la branca: `git push origin feature/nova-funcionalitat`
5. Obre un *Pull Request*.

## 🙌 Crèdits

- **Direcció del projecte:** el teu nom aquí (canvia la constant `AUTHOR` al codi; apareix a la pantalla *Créditos* del joc).
- **Programació i disseny:** generat amb [Claude](https://claude.ai) (Anthropic).
- **Motor 3D:** [Three.js](https://threejs.org/) r128, de mrdoob i col·laboradors (llicència MIT).
- **Àudio:** sintetitzat en temps real amb la Web Audio API.

## 📄 Llicència

Distribuït sota llicència **MIT**. Afegeix un fitxer `LICENSE` al repositori (GitHub el pot generar des de *Add file → Create new file → LICENSE*).

---

Fet amb ❤️ i molt neó.
