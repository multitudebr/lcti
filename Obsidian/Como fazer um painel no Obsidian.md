
#obsidian
[fonte](https://youtu.be/AatZl1Z_n-g)
1) Ativar CSS Snippets e entrar na pasta dele (Settings > Appearance > CSS Snippets).
2) Baixar e colocar esse [arquivo](https://github.com/TfTHacker/DashboardPlusPlus/blob/master/.obsidian/snippets/dashboard.css) na pasta.
3) Em Settings > Appearance > CSS Snippets, recarregar (usando um botão similar a 🔄) e ativar o snippet copiado.
4) Criar uma página e colocar um cabeçalho yaml com `cssclass: dashboard` dentro dela.
5) Pra ver o funcionamento, copiar o conteúdo [desse arquivo](https://github.com/TfTHacker/DashboardPlusPlus/blob/master/Dashboard%2B%2B.md) na página criada e apertar no botão superior direito pra ativar o modo de leitura ou usar o atalho Ctrl + E. 
6) Pra ver melhor o conteúdo, desativar Settings > Editor > Display > Readable line length. Pra ter o mesmo efeito sem desativar essa opção, baixar [este arquivo](https://github.com/TfTHacker/DashboardPlusPlus/blob/master/.obsidian/snippets/dashboard-ReadLineLength.css), colocar na pasta do CSS snippets e ativar.
7) Pra fazer aparecer uma imagem no início do painel é preciso baixar e ativar o plugin Banners, além de baixar e referenciar uma imagem no cabeçalho yaml.
8) É possível adicionar código HTML como esse, que adiciona um título sobre a imagem: `<div class="title" style="color:Teal">HOME</div>`
9) Outra possibilidade é fazer o painel ser a página inicial do vault usando o plugin Homepage. Depois de baixar e ativar, abrir as opções e colocar o nome da página na opção Homepage, definir a opção Homepage view como Reading e ativar a opção Refresh dataview.
10) Pra não aparecer bloco de metadados no início, desativar Show frontmatter em Settings > Editor > Show frontmatter.
11) O conteúdo do painel pode ter cabeçalhos de níveis 1 a 6 e listas com sublistas. 
12) Na seção Vault, é preciso habilitar as opções Enable Javascript Queries e Enable Inline Javascript Queries em Settings > Dataview > General Settings. Pra ver o código do dataviewjs basta usar Ctrl + E de novo.

Exemplos de snippets do dataviewjs:
```
Esta opção mostra os últimos 4 itens acessados: 
$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)

Esta mostra os itens marcados com a tag favorite: $=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(4).file.link)

Esta mostra a quantidade total de páginas e de uma pasta específica: $=dv.pages().length` e `$=dv.pages('"Family/Recipes"').length
```

![[Dashboard++ — a simple organization and navigation method for Obsidian Vaults by TfTHacker Obsidian Observer Medium.pdf]]