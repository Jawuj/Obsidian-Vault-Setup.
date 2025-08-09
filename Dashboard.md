---
banner: "![[09 - Media/10 - Images/Banners/Le Neophyte - Gustave Doré - 1877-1880.jpg]]"
banner-x: 51
banner-y: 25
banner-height: 250
banner-display: cover
banner-fade: -25
content-start: 236
banner-radius: 0
cssclasses:
  - centerh2
  - homepage
---
---
> [!multi-column]
>
> > [!blank-container|wide-3] Contributions
> > ```contributionGraph
> > graphType: default
> > dateRangeValue: 365
> > dateRangeType: LATEST_DAYS
> > startOfWeek: 0
> > showCellRuleIndicators: true
> > titleStyle:
> >   textAlign: center
> >   fontSize: 14px
> >   fontWeight: normal
> > dataSource:
> >   type: PAGE
> >   value: ""
> >   dateField:
> >     type: FILE_CTIME
> >   countField:
> >     type: DEFAULT
> > fillTheScreen: false
> > enableMainContainerShadow: false
> > mainContainerStyle:
> >   boxShadow: rgba(100, 80, 50, 0.1) 0px 1px 4px
> >   backgroundColor: "transparent"
> > cellStyleRules:
> >   - id: SEPIA_empty
> >     color: "#000000"
> >     min: 0
> >     max: 0
> >   - id: SEPIA_a
> >     color: "#8B6E4E"
> >     min: 1
> >     max: 2
> >   - id: SEPIA_b
> >     color: "#A18261"
> >     min: 2
> >     max: 3
> >   - id: SEPIA_c
> >     color: "#C2A67D"
> >     min: 3
> >     max: 5
> >   - id: SEPIA_d
> >     color: "#E3CBA2"
> >     min: 5
> >     max: 8
> >   - id: SEPIA_e
> >     color: "#F5E9D3"
> >     min: 8
> >     max: 25
> >   - id: BOLD_25
> >     color: "#FFB347"
> >     min: 25
> >     max: 50
> >   - id: BOLD_50
> >     color: "#FF7F50" 
> >     min: 50
> >     max: 100
> >   - id: BOLD_100
> >     color: "#FF4F81"
> >     min: 100
> >     max: 200
> >   - id: BOLD_200
> >     color: "#FF2E63"
> >     min: 200
> >     max: 9999
> > ```

```tabs
tab: Current Projects/Quick Access.
 - [[Poemario - Espacio]]
 - [[Heatmap Graphics.]]
 - [[Albums]]
 - [[¿Ppaml]]
 - [[University]]

tab: Highest Priority Tasks
 ```tasks
not done
priority is high


tab: Recent Files.
 ```dataview
	list
	from ""
	sort file.mtime desc
	limit 5

tab: Stats.


```dataviewjs
let poems = dv.pages("#Poem").array();
let ideas = dv.pages("#Escritura/Idea").array();

let lastPoem = poems.sort((a,b) => b.file.ctime - a.file.ctime)[0];
let totalPoems = poems.length;
let totalIdeas = ideas.length;

let writingDays = new Set(poems.map(p => p.file.ctime.toFormat("yyyy-MM-dd")));
let lastPoemText = lastPoem ? `[[${lastPoem.file.name}]]` : "N/A";

let exclude = ["poem", "#poem", "notfinished", "#notfinished", "poem/notfinished", "#poem/notfinished", "finished", "#finished"];
let tagCounts = {};

for (let p of poems) {
  if (!p.tags) continue;
  for (let tag of p.tags) {
    let cleanTag = tag.toLowerCase().replace(/^#/, "");
    if (exclude.includes(cleanTag)) continue;
    tagCounts[tag] = (tagCounts[tag] || 0) + 1;
  }
}

let sortedTags = Object.entries(tagCounts).sort((a,b) => b[1]-a[1]);
let topTag = sortedTags[0] ? `${sortedTags[0][0]} (${sortedTags[0][1]})` : "None";

dv.paragraph(`
- 📜 **Poems written:** ${totalPoems}
- 💡 **Ideas captured:** ${totalIdeas}
- 📅 **Writing days:** ${writingDays.size}
- 🕓 **Last poem:** ${lastPoemText}
- 🏷️ **Most used theme:** ${topTag}
`);

```
---
## Create Quick Notes.


> [!multi-column]
> > [!blank]
> > 
> > ```meta-bind-button
> > id: new-album
> > label: 🎵 Add Album
> > style: primary
> > class: sepia-glow
> > action:
> >   type: createNote
> >   folderPath: "01 - Database/Albums"
> >   fileName: "New Album"
> >   openNote: true
> > ```
>
> > [!blank]
> > 
> > ```meta-bind-button
> > id: new-book
> > label: 📚 Add Book
> > style: primary
> > class: sepia-glow
> > action:
> >   type: createNote
> >   folderPath: "01 - Database/Books"
> >   fileName: "New Book"
> >   openNote: true
> > ```
>
> > [!blank]
> > 
> > ```meta-bind-button
> > id: new-poem
> > label: ✒️ Add Poem
> > style: primary
> > class: sepia-glow
> > action:
> >   type: createNote
> >   folderPath: "03 - Escritura/Poemas"
> >   fileName: "New Poem"
> >   openNote: true
> > ```
> 

---
> [!multi-column]
> 
> > [!gradient_3_1] Tasks.
> >
> > [![[TasksIcon.png]]](Tasks.md)
> >
> > Todo lo que tengo que hacer en mi día, universidad, relaciones, trabajos... Todo.
> 
> > [!gradient_3_1] University.
> >
> > [![[UniversityIcon.png]]](University.md)
> >
> > Terreno fértil para el pensamiento estructurado, la exploración personal y la construcción de conocimiento con propósito.
> 
> > [!gradient_3_1] Writing.
> >
> > [![[WritingIcon.png]]](Writing.md)
> >
> > La escritura como medio de expresión y transformación, herramienta para pensar, sentir y recordar.
>
> > [!gradient_3_1] Poetry.
> >
> > [![[PoetryIcon.png]]](Poetry.md)
> >
> > Expresar situaciones, emociones y vivencias mediante palabras decoradas, suavizadas o perforantes.
>
> > [!gradient_3_1] Daily.
> >
> > [![[DailyIcon.png]]](Daily.md)
> >
> > Mi día a día escrito en notas independientes, reflejan lo que viví y cómo funciona mi cerebro.
>
> > [!gradient_4_1] Dreams.
> >
> > [![[DreamIcon.png]]](Dreams.md)
> >
> > Simplemente sueños que tuve y escribí con un ojo cerrado. Lamentablemente algunos los olvido antes...
>
> > [!gradient_5_1] Me.
> >
> > [![[MeIcon.png]]](Me..md)
> >
> > Yo, descrito en una nota más. Supongo que soy un poco egocéntrico como para tener una nota especialmente sobre mí.
>
> > [!gradient_6_1] Albums.
> >
> > [![[AlbumIcon.png]]](Albums.md)
> >
> > Colección organizada de canciones o piezas musicales publicadas juntas, usualmente con un concepto, estilo o narrativa en común.
>
> > [!gradient_7_1] Books.
> >
> > [![[BookIcon.png]]](Books%20In%20Note.md)
> >
> > Obras escritas que recopilan ideas, historias o conocimientos, con un propósito literario, informativo o artístico.
>
> > [!gradient_8_1] ----------.
> >
> > [![[HeartIcon.png]]](Test.md)
> >
> > -----------------------------------------------------------------------.
>
> > [!gradient_9_1] Zettel.
> >
> > [![[ZettelkastenIcon.png]]](z-20250713-Zettelkasten.md)
> >
> > Sistema para capturar, conectar y desarrollar ideas individuales. Significa Caja de notas.
>
> > [!gradient_10_1] Zettelkasten.
> >
> > [![[ZettelkastenIcon.png]]](z-20250713-Zettelkasten.md)
> >
> > Sistema para capturar, conectar y desarrollar ideas individuales. Significa Caja de notas.
>
> > [!gradient_11_1] Zettelkasten.
> >
> > [![[ZettelkastenIcon.png]]](z-20250713-Zettelkasten.md)
> >
> > Sistema para capturar, conectar y desarrollar ideas individuales. Significa Caja de notas.
>
> > [!gradient_12_1] Zettelkasten.
> >
> > [![[ZettelkastenIcon.png]]](z-20250713-Zettelkasten.md)
> >
> > Sistema para capturar, conectar y desarrollar ideas individuales. Significa Caja de notas.



---
```dataviewjs
// Calculate days since first note
const files = dv.pages()
const oldestFile = files.sort(f => f.file.ctime)[0]
const daysSinceStart = Math.floor((Date.now() - oldestFile.file.ctime) / (1000 * 60 * 60 * 24))

// Count total notes
const totalNotes = files.length

// Count unique tags
const allTags = files.flatMap(p => p.file.tags).distinct()
const totalTags = allTags.length

// CSS común + adaptativo por media query
const statsStyles = `
  <style>
    .sepia-stats {
      border: 1px solid #d4bfa5;
      border-radius: 14px;
      padding: 20px;
      text-align: center;
      font-family: var(--font-text);
      box-shadow: 0 3px 6px rgba(140, 120, 100, 0.1);
      transition: background 0.3s ease, color 0.3s ease;
    }
    .sepia-stats h2 {
      font-weight: bold;
      margin-bottom: 12px;
    }
    .sepia-stats p {
      font-size: 18px;
      margin: 10px 0;
    }
    @media (prefers-color-scheme: light) {
      .sepia-stats {
        background-color: #f8f0e6;
        color: #5c4a35;
      }
      .sepia-stats h2 {
        color: #7d5a3a;
      }
    }
    @media (prefers-color-scheme: dark) {
      .sepia-stats {
        background-color: #2e261f;
        color: #eee2d7;
        border-color: #5b4b3f;
        box-shadow: 0 3px 6px rgba(20, 15, 10, 0.2);
      }
      .sepia-stats h2 {
        color: #e0c4a4;
      }
    }
  </style>
`;

dv.paragraph(`
${statsStyles}
<div class="sepia-stats">
  <h2>📊 Obsidian Stats</h2>
  <p>🗓️ Has usado Obsidian por <strong>${daysSinceStart}</strong> días</p>
  <p>📝 Tienes <strong>${totalNotes}</strong> notas</p>
  <p>🏷️ Estás usando <strong>${totalTags}</strong> etiquetas únicas</p>
</div>
`);

```
---




