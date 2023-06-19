---
created: 2022-10-17
tags: livros
titulo: Programação Shell Linux
autor: Júlio Cezar Neves
---
[Livro](file:///home/sheilagomes/Dropbox/AssistirNuvem/Livros/Livro_Programação_em_Shell_Linux.pdf)`
## Impressões
* Muito bom, conteúdo excelente, bem explicado e com humor ainda (meio duvidoso às vezes, mas pontos pela tentativa).

# Destaques
## Parte I
### Capítulo 1
**Começando devagarinho**
Iniciando uma sessão Linux - 16
Encerrando uma sessão Linux - exit, logout - 17
	passwd - Alterando a senha - 17
	Comandos - 18
Obtendo ajuda - 19
	help - Ajuda - 19
		Mostra informações gerais sobre os built-ins do Shell
	man pages - Manual de Referência - 20
	apropos - Informações sobre um tópico - 22
		`apropos compiler`
	whatis - Descrição de comandos - 23
		`whatis chmod 

### Capítulo 2
**Manipulando arquivos e diretórios**
Sistema de arquivos do Unix - 24
Operações com o sistema de arquivos - 25
Caminhos de diretórios (paths) - 26
	`\` raiz, `.` diretório atual, `..` antecedente  -  26
	pwd - Informa nome do diretório corrente - 28
	cd- Navegando entre diretórios - 28
		`cd ~`  ou `cd \` (raiz)
		`cd -`  (último diretório)
	ls - Lista arquivos - 29
		*Opções:*
			`-l` lista os arquivos em formato detalhado
			`-a` lista todos os arquivos, inclusive os ocultos
			`-r` ordem alfabética reversa
			`-h` combinado com `-l` imprime tamanho mais legível (1K, 2M)
			`-R` lista também os subdiretórios encontrados
		`ls *.sh` (qq no. caracteres)
		`ls ????.sh` (no. caracteres = no. ?)
		`ls [os]*.sh` (iniciados por `o` ou `s` e seguidos pelo resto)
		`ls [!os]*.sh` (negação do anterior)
		`ls [A-Z]*.sh` (começa por maiúscula)
	cp - Cópia de arquivos e diretórios - 31
		*Opções:*
			`-i` modo interativo
			`-v` mostra o que está sendo copiado
			`-r` copia recursivamente (diretórios e subdiretórios)
		`cp -i telefones telefones.bak` (confirma se já existe cópia)
		`cp -r ~jneves julio` (copia recursivamente home pra `julio`)
	mv - Move arquivos e diretórios - 32
		`mv script.sh script.velho` (renomeia)
		`mv arq /fs2` (move `arq` pro diretório `fs2`)
	In - Estabelece ligações entre arquivos - 33
		`ln sinteticof sinteticoc` (cria link direto, mesmo arquivo)
		`ln - sf sinteticof sinteticoc` (cria link simbólico)
	mkdir - Cria um diretório - 35
		`mkdir curso`
		`mkdir ../curso` (cria pasta `curso` acima, "ao lado" do diretório atual)
		`mkdir ~jneves/curso` (cria pasta `curso` na home)
	rmdir - Remove diretório - 35
		`rmdir ~/dirtst` (remove se estiver vazio)
	rm - Deleta arquivos e diretórios - 36
		*Opções:*
			`-f` ignora arquivos inexistentes e não pede confirmação antes de remover
			`-I` sempre pede confirmação antes de remover
			`-r` remove recursivamente
		`rm arq1 arq2 arq3` (apaga os 3 arquivos)
		`rm arq[1-3]` (apaga os mesmos 3 arquivos)
		`rm -rf phpdír` (remove pastas recursivamente, sem confirmar)
	file - Indicando tipo de arquivo - 37
	grep - Pesquisa arquivos por conteúdo - 37
		*Opções:*
			`-c` somente a quantidade de linhas indicada pelo regex
			`-i` não diferencia maiúsculas e minúsculas na procura
			`-l` não mostra a linha encontrada, só o nome do arquivo
			`-v` inverte a procura, mostrando só as linhas fora do regex
			`-n` precede as linhas com número relativo dentro do arquivo
		`grep lixo dica.sh` (mostra ocorrêncas de `lixo` no arquivo `dica.sh`)
		`grep - i julio /etc/passwd` (mostra sem diferenciar maiusc/minusc)
	find - Procurando arquivo por características - 38
		*Opções:*
			`-atime ±d` arquivos acessados há mais (`+d`) ou a menos (`-d`) de `d` dias
			`-ctime ±d` arquivos cujo status mudou há mais (`+d`) ou a menos (`-d`) de `d` dias
			`-mtime ±d` arquivos cujos dados foram modificados há mais (`+d`) ou a menos (`-d`) de `d` dias
			`exec cmd {} \;` executa o comando cmd
			`-ok cmd {} \;` pede permissão antes de executar cmd
			`-printf formato` especifica formato de saída
		![[Pasted image 20221101082610.png]]
		`find . -name \*.sh` (procura na pasta atual por nome, contrabarra por causa do asterisco ou qq outro caractere especial)
		`find . -type f -size +1OOOOOOc -atime +60 -exec rm {} \;` (procura e remove arquivos com + de 1MB, último acesso há + de 60 dias)
		`find \ -name \*.sh -o -name \*.txt -print` (lista todos os arquivos `*.sh` ou `*.txt` a partir da raiz, `-o` indica OU)
		`find . -name ".b*" -printf '%t %p\n'` (saída formatada por tempo `%t`, nome do arquivo `%p` e com salto de linha `\n`)
		`find . -name ".b*" -printf '%s\t%p\n' | sort -n` (lista por ordem de tamanho, com `\t` pra dar um `tab` entre tamanho e nome)
		`find . -name ".b*" -printf '%TY-%Tm-%Td %TH:%TM:%TS %p\n' | sort` (lista os mesmos arquivos por data e hora da última alteração)`
	basename - Devolve o nome de um arquivo dado o caminho - 45
		`basename /etc/passwd` (devolve `passwd`)
	dirname  - Devolve o nome do diretório dado o caminho - 45
		`dirname /etc/passwd` (devolve o caminho absoluto `/etc`)
		`dirname telefones` (devolve o caminho relativo `.`)

### Capítulo 3
**Mais Manipulação**
	cat - Exibe o conteúdo de um arquivo - 47
		`cat texto1.txt` (mostra o conteúdo de `texto1.txt`)
		`cat > texto1.txt` (lê do teclado e manda pra `texto1.txt`)
		`cat texto1.txt texto2.txt > texto3.txt` (une vários arquivos em um novo arquivo)
		`cat -vet telefones` (mostra conteúdo e caracteres ocultos de `telefones`)
		`cat -n texto4.txt` (mostra as linhas numeradas)
	wc - Conta caracteres, palavras e/ou linhas - 49
		`wc texto.txt` (para caracteres `-c`, linhas `-l`, palavras `-w`, linha mais longa `-L`)
	sort - Classifica dados - 51
		`sort +0.1 telefones` (classifica pelo 2o. caractere do 1o. campo)
		`sort - n numeros` (pra classificar números precisa do `-n`)
	head - Mostra início dos dados - 54
		`head texto.txt` (mostra as 10 primeira linhas por padrão)
		`head -4 texto.txt` (mostra as 4 primeiras linhas)
	tail - Mostra final dos dados - 54
		`tail - n 5 /etc/smb.conf` (mostra a 5 últimas linhas)
		`tail -c5O /etc/samba` (mostra os últimos 50 bytes/caracteres)

### Capítulo 4
**Segurança de Acesso**
Posse de Arquivos - 56
chown - Trocando dono do arquivo - 57
	`chown silvina dica.sh` (muda a propriedade do arquivo pra silvina)
chgrp -Trocando o grupo do arquivo - 58
	`chgrp prod dica.sh` (muda a propriedade do arquivo pro grupo prod)
Tipos de Acesso a Arquivos - 58
	3 tipos de acesso a arquivos e diretórios: leitura (`r`), escrita (`w`) e execução (`x`), para ver usar `ls -l`
Classes de Acesso a Arquivos - 59
	`drwxrwxr-x  6 sheilagomes sheilagomes     4096 jun 23  2021  web-components` (o primeiro caractere indica o tipo, nesse caso um diretório `d`, os 3 próximos  são permissões do dono `rwx`, os próximos 3 do grupo `rwx` e os últimos de outros `w-x`, onde o hífen indica ausência)
chmod - Ajustando permissões de arquivos - 60
	`chmod u+w teste` (dando ao dono `u` permissão de escrita `w`)
	`chmod a+w teste` (dando a todos `a` permissão de escrita `w`)
	`chmod g+x, uo+r-w teste` (grupo executa, dono e outros leem mas não gravam, o `+` adiciona, o `-` remove)
	`chmod u=rwx teste` (dono lê, grava e executa)
	`chmod u=rwx,g=rx,o=r teste.txt` e `chmod 754 teste.txt` são equivalentes, o segundo usa conversão binária pra decimal representando 111, 101 e 100 

### Capítulo 5
**Comandos para Informações sobre Usuários**
who- Usuários ativos - 63
	`who am i` (info de login do próprio usuário)
	`who -m` (equivalente a `who am i`)
	`who` (todos os usuários ativos)
	`who -H` (mostra um cabeçalho)
id - Identificadores do usuário - 64
	`id` (identificadorres do usuário, login e grupos)
	`id -g` (mostra grupo atual)
	`id -G` (mostra todos os grupos)
	`id -u` (mostra só idenificador)
	`id -nu` (mostra nome do usuário)
finger - Detalha informações sobre usuários - 65
	finger não vem instalado no Ubuntu por padrão
chfn - Altera dados do finger - 66
groups - Informa grupos dos usuários - 67

### Capítulo 6
**Pra não Perder o Compromisso**
date - Mostra e acerta data/hora  - 68
	`date "+Hoje a data é : %d/%m/%Y%n e a hora é: %T"`
	`date --date '1 day ago '` (dia anterior)
	`date --date '1 day'` (dia seguinte)
	`date --date='25 Dec' +%a`  (dia da semana de uma data)
	`date --date='1 day 1 month 1 year ago'`
	`date --date='1 day 1 month 1 year'`
cal - Exibe o calendário - 70
	`cal` (mostra mês e ano atuais)
	`cal 04 2000` (mostra específicos)
	`cal 1970` (mostra ano inteiro)
	`cal 09 1752` (curiosidade: início gregoriano)

### Capítulo 7
**Becapeando**
Comandos de Backup e Compressão
	tar - Para agrupar vários arquivos em somente um
	compress - É o utilitário de compressão de arquivos padrão do Unix
	uncompress - Descomprime arquivos compactados pelo compress
	zcat - Permite visualizar o conteúdo de arquivos compactados
	com compress
	gzip - É o utilitário de compressão de arquivos padrão do Linux
	gunzip - Descomprime arquivos compactados pelo gzip
tar - Agrupa arquivos - 72
	*Opções:*
		`-c` cria um novo arquivo `.tar` e adiciona a ele os arquivosespecificados
		`-f` indica que o destino é um arquivo em disco, e não uma unidade de fita magnética;
		`-p` preserva permissões originais dos arquivos durante de-sagrupamento;
		`-r` adiciona os arquivos especificados no final do arquivo `.tar`, sem cnar um novo;
		`-t` lista o conteúdo do arquivo `.tar`
		`-u` adiciona os arquivos especificados ao arquivo `.tar` somente se eles ainda não existirem no arquivo `.tar`, ou se tiverem sido modificados desde quando foram agrupados por um comando `tar`
		`-v` mostra o nome de cada arquivo processado;
		`-x` retira os arquivos agrupados no arquivo `.tar`
	`tar -tvf /dev/nstO .` (mostra o conteúdo do arquivo)
	`tar -cf backup.tar /home/d327760/*`
compress - Para compactar dados      6 1
uncompress - Descompactando arquivos   62
zcat - Visualizando dados compactados   63
gzip - Compactado r livre       63
gunzip - Descompaclador livre    . 65

# PAREI AQUI
Capítulo 8. Controle de Execução   66
ps - Lista de processos   . 68
kill - Enviando sinal a processos .     69
Matenal com direitos aL•Iora1sSumário
XXXIII
Execução em Background  70
'obs - Lista · recessos sus ensos e em back rou nd . . 71
b - Manda recessos ara back round     71
fg - Trazendo processos para foreground    .  72
Ca ítulo 9. Executan do Tarefas A endadas .  .  73
Programando tarefas co m crontab      73
O comando at   76
O comando batch   . .  78
Parte 11
Leiame.txt    81
Ca ítulo O. O Básico do Básico .
u
. . . . . .
. .
. .  . . . . . . . . . . .
84
Visão geral do sistema operacional UNIX      84
Quem não é movido a gasolina, precisa de Snell?    .   85
Por que Shell?         . .   88
Tarefas do Sbell
88
Exame da linha de coma ndos rece bida ,   89
Resolução de redirecio namentos . : .  .     90
Substituição de vari áveis     90
Substituição de meta ca racteres .     .     90
Passa linha d e comando para o kernel .    90
Principais Shells .   91
Bourn e Shell,  ,,, ,,  ,  ,,  ,  ,, ,  ,, . . ,,  , . , 91
Bourne-Again Shell        91
Korn Shell
91
C Shell.    . 92
. Sem comentários     . . ,, ,  , ,
, , ., ,,, ,,   , ,, , 93
Capítulo 1. Recordar é Viver  . 94
Usando aspas, apóstrofos e barra invertida  94
Crase e parênteses resolvendo crise entre parentes   95
Direcionando os caracteres de redireci onamento,,   ,     ,   . , 98
Exercícios
101
Matenal com direitos aL•Iora1sXXXIV Programação Shell Linux
Ca ítulo 2. Comandos ue- não são do Planeta . 103
O ed é d+
103
O comando sed    .•• 108
A opção -n     .  11 7
A opção -i    118
A familia de comandos grep     121
A opção -c (count ou contar) .   . .  124
A opção -1    .   .  . . 1.25
A opção -v  .     126
A opção -f (file) . . .  126
A opção -o (only matching) .     128
Os comandos para cortar e cola r  .    130
Cortando cadeias de caracteres - cut      130
Colando cadeias de ca racteres - paste . .   . 133
A opção -d (delimitador)  .  . . . 134
A opção - s . . . 134
Perfumarias úteis . . 135
O tr traduz. tra nscreve ou transforma cadeias de ca racteres?  . 136
A o ão - s  .  141
A opção -d  .  .  142
A opção -c  .     143
Exprimindo o expr de forma expressa     144
Execução de operações aritméticas .  . . . 144
bc - A c a lcll I a d ora
145
O interpretador aritmético do Shell  147
O uniq é único .  . . . . 153
A o ão -d     154
Mais redirecionamento sob o Bash
155
Exercício
156
Capítulo 3. Viemos aqui para falar ou para programar?  . 157
Executando um programa (sem ser na cadeira elétrica)   157
Usando variáveis         .  158
Para criar variáveis          158
Para exibir o conteúdo das variáveis
159
Passando e receben do parâmetros   .   160
O comando que passa parâmetros . .  . . 163
Desta vez vamos.
168
Programa para procurar pessoas no arquivo de telefones   . 169
Prog rama para inserir pessoas no arquivo de telefones    170
Matenal com direitos aL•Iora1sSumário
XXXV
Programa para remover pessoas do arquivo de telefones   . . 172
Exercícios
173
Ca ítulo 4. Liberdade condicionalll  174
O bom e velho i f   .  175
Testando o test . 
. . . .
. . . . . . 178
O test de roupa nova   . .  185
Se ai uém disser ue eu disse, eu ne o   186
Não confunda and com The End     .  187
188
ar ou ou disse o cão afônico
Disfarçando de if        .          . 189
&& (andou ª lógico) .      . 189
li (QI ou ou lógico) .    .     .     . .  190
Operadores aritméticos para testar     191
. .
 .
 .  
. . .  .  192
E tome de test
O caso em que o case éasa melhor        . 195
Exercícios    .  .    .     .  201
Ca ítulo 5. De Lu a no Loo .  202
O forró do for .       203
Perguntaram ao mineiro: o que é while? while é while, uai!  . 212
O until não leva um- mas é útil.     .  .   214
Continue dançando o break    .      218
Exercício .        .  220
Ca ítulo 6. A rendendo a ler    221
Que posição você prefere? . . . .   . 221
Afinal como é que se lê?    .   . 228
Leitura dinâmica
237
Leitura sob o Bash  . .     .   239
Opção -p    .  239
Opção -t            239
Opção -n         240
Opção -s  .  . .   .        . 241
Opção -a   . . .   . 241
Outra forma de ler e gravar em arquivos   . 241
Já sei ler. Será que sei escrever?    . 243
Exercícios     . 246
Matenal com dlreilos aL•Iora1sXXXVI
Programação Shell Linux
Capítulo 7. Várias variáveis .   .  248
Exportar é o que importa   .  249
É . e pronto  .  .   255
Principais variáveis do sistema    .   . 257
Parâmetros
263
Construções com parâmetros e variáveis . . 264
Expansão de chaves {  }'  . .  .  27 4
Ganhando o jogo com mais curingas  276
Um ou co de mani ula ão de vetores .  282
Exercícios   .     290
Capítulo 8. Sacos de gatos   291
A primeira faz tchan, a segunda faz tch un, e tchan, tchan, tchan   291
wait a minute Mr. Postman  . .  296
Para evitar trapalhadas use o trap .    297
Funções  . .   301
Substituição de processos    309
Mergulhando fundo no nautilus . . 317
Instalando scripts do gerenciador de arquivos  .   317
Escrevendo scripts do gerenciador de arquivos .  318
Ex em lo.s de se ri ts . .  320
script também é um comando .    326
Fatiando o ões      .  328
Em busca do erro perdido  . . 331
Mandando no terminal.    333
Macetes, macetes & macetes    . 338
Exe~ ici os
A êndice 1. awk: Comando ou Lin
340
em?  . 341
O Be- a-bá do awk   .   342
Uso do awk
, ,
343
Campos      .  343
Listando . . .  344
Forma ndo padrões .    . 346
Expressões relacionais   . 346
Expressões regula res   348
Matenal com dlreilos aL•Iora1sSumário
XXXVII
Padrões BEGIN e END  ,  ,  ,,,,,,  . ,  ,,,,, , . . 351
O uso de variáveis . 352
Faz de conta      .    , . . 355
Operadores       .     356
Funções matemáticas       .   . 357
Prá cadeia . ,  ,  ,. ,, . , , . , , , ,,, ,  , , ., ,, . , , . , , ., ,,   , , , . 357
Instruções de controle de fluxo . . 361
O comando if  362
O comandowhile  .  .  .     .   363
for midável.  .  . .  . . . 364
break e outros bric-a-bracs     365
Valores de vetores        . . 365
print e printf parece mas não é   .  .   . . 368
A saída com prínt .  .  368
Formatando a saída com printf        369
Como redirecionar a saída com rintf?  370
O awk no contexto do Shell . ,  , ,  ,  ,  ,  ,  3 72
Recebendo parâmetros  373
Em cooperação com o Shel/ . . . . . 373
A êndice 2. Ex ressões re u lares  377
Um pouco de teoria  .        378
Conceitos básicos .    . .    . .  . . . . 378
História . .          . 379
Então vamos meter as mãos na massa . 380
Âncoras . 381
Representantes     .    . 383
Quantificadores      . 384
Fingindo ser lista .   .   . 390
Outros Z9
Expressões Regula res (no BrOffice.org)     408
Onde usar Expressões Regulares no BrOffice.org .   409
Diferenças na lógica de uso    4 10
Diferenças de sintaxe     .   .  412
A ênd ice 3. CGI em Shell Scri t   420
Configuração   .       . .   . 420
Algumas considerações importantes    . 422
Diversão .    .    . 422
IniCiando
422
Método GET .    . 426
Matenal com direitos aL•Iora1sXXXVIII Programação Shell Linux
Método POST    .   427
U load     .  429
CheckBox
431
Radio Buttons . .        432
Contador de acesso genérico          433
SSI - Server Side lncludes  .   . 434
Contador     .  434
Segurança        .  436
Introdução e Configuração   . .  .  436
LAN
44
Livro de assinaturas     .  445
A êndice 4 . Dia lo  450
Por que este doéumento existe  .    .      450
Objetivo e Escopo Deste Documento    . 451
. . . .
. .
. 452
Últimas Palavras Antes de Inici ar.
Introdu ão .  . .   452
O ue é o Dialo .    452
Breve Históri co do Di'alog .      453
Seu Primeiro Comando com o Dialog . .  453
Listagem dos 15 Tipos de Caixas .    454
Exemplos dos Tipos de Caixa . .    455
Como o Dialog Funciona   .   460
Parâmetros Obrigatórios da Linha de Comando     461
Como reconh ecer respostas SIM ou NÃO .  . 462
Como Obter o Texto Que o Usuário Digitou    . 464
Como Obter o Item Único Escolhido de um Menu ou Radiolist   . 466
Como Obter os Itens Múlti plos Escolhidos de um Checklist   4 70
E se o Usuário Apertar o Botão CANCELAR?  .  472
E se o Usuário Apertar a Tecla ESC?    473
E se o Usuário Aperta r o botão HELP?      473
Como Trata r Todos os Botões e Teclas de Uma Vez?    4 7 4
Mergu lhando de Cabeça no Dialog . .    .    474
Exemplo de Menu Amarrado (em Loop) .  474
Exemplo de Telas Encadeadas (Navegação Sem Volta)  . 476
Exemplo de Telas com Navegação Completa (Ida e Volta)  477
Exemplo de Pedido de Confirmaçã o (Uma Caixa Sobre Outra)   480
Exemplo de Posicionamento de Caixas (Não Centralizado)  481
Exemplo de Vá ri as Caixas na Mesma Tela (Multicaixas!)   482
Exemplo de Menu com Itens Dinâmicos (Defi nidos em Execução)   484
Exemplo de Cópia de Arquivos com Barra de Progresso (Gauge)  486
Configurando as Cores das Caixas  . . 489
Matenal com direitos aL•Iora1sSumário
XXXIX
Lista das Opções de Linha de Comando     492
Opções para definir os textos da caixa  .  492
Opções para fazer ajustes no texto da caixa     492
Opções para fazer ajustes na ca ixa . . 493
Opçõ es relativas aos dados informados pelo usuário    . . 494
Outras 49
Opções que devem ser usadas sozinhas na linha de comando . 495
Os Clones: Xdialog, Kdialog, gdialog .     .  . 495
Whiptail  . .    . .  496
Xdialog  .  496
.    .    497
 . 498
Zenity
39
Udpm
09
pythondialog .  .  .       499
Onde Obter Mais Informações     499
A
Usandó o wget com proxy    .   506
Arquivos de configuração       .  507
Brincando pela rede com o netcat .    51 3
Coisas do bem .         514
Coisas do mal    .  517
Resumo .  .  .     . 519
Apêndice 6. Significado das Opções mais Freq uentes no Shell.  520
A êndice 7. Resolução dos Pro ramas     522··
•
lndice Remissivo