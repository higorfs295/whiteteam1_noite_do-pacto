# O papel da White Team em exercícios de cibersegurança

Material da equipe **White Team 1** para o Encontro 1 da trilha White Team do grupo de estudos **UrutauSec** (EMC/UFG): como planejar, conduzir e avaliar um exercício Red × Blue.

| | |
|---|---|
| **Pauta** | Encontro 1 da trilha White Team: fundamentos e descoberta de ameaças |
| **Apresentação** | Sábado, 21/11/2026, às 9h, Sala 101, EMC/UFG |
| **Equipe** | Higor Ferreira (líder), Hugo Mituiti, Isaque e João Vitor Carvalho |
| **Paralelo com o Valorant** | João Vitor Carvalho |
| **Monitoria** | Thâmara Cordeiro, Eduardo Martins e Alyce Suza |
| **Versão** | v9 final (20/11/2026) |
| **Duração** | 1h25 com o campeonato e as perguntas |

## Comece por aqui

| Pra quê | Arquivo |
|---|---|
| Apresentar (com notas de fala) | [`01_Apresentacao/UrutauSec_WhiteTeam1_Apresentador.pptx`](01_Apresentacao/UrutauSec_WhiteTeam1_Apresentador.pptx) |
| Compartilhar depois | [`01_Apresentacao/UrutauSec_WhiteTeam1_Publico.pdf`](01_Apresentacao/UrutauSec_WhiteTeam1_Publico.pdf) |
| Ensaiar | [`03_Guia_e_Cartoes_de_Fala/`](03_Guia_e_Cartoes_de_Fala/) |
| Mestrar o campeonato | [`04_Campeonato/UrutauSec_WT1_Roteiro_do_Campeonato.pdf`](04_Campeonato/UrutauSec_WT1_Roteiro_do_Campeonato.pdf) |
| Projetar o painel do campeonato | [`04_Campeonato/Painel_do_Campeonato.html`](04_Campeonato/Painel_do_Campeonato.html) |
| Imprimir o material do campeonato | [`04_Campeonato/UrutauSec_WT1_Kit_do_Campeonato.pdf`](04_Campeonato/UrutauSec_WT1_Kit_do_Campeonato.pdf) |
| Publicar na WikiTau | [`02_WriteUp_WikiTau/WriteUp_WhiteTeam1.md`](02_WriteUp_WikiTau/WriteUp_WhiteTeam1.md) |
| Montar o exercício-exemplo | [`05_Kit_do_Exercicio/`](05_Kit_do_Exercicio/) |
| Conhecer a história | [`06_Historia_Noite_do_Pacto/Pagina_interativa/index.html`](06_Historia_Noite_do_Pacto/Pagina_interativa/index.html) |

## Estrutura

```text
.
├── 01_Apresentacao/             versão do apresentador (36 slides + 9 de apoio, com notas)
│                                e versão do público (36 slides), em .pptx e .pdf
├── 02_WriteUp_WikiTau/          texto base do write-up (.md pra colar no BookStack, .docx e .pdf)
├── 03_Guia_e_Cartoes_de_Fala/   guia da equipe e cartões de fala
├── 04_Campeonato/               painel (HTML), roteiro do mestre e kit de impressão do campeonato
├── 05_Kit_do_Exercicio/         roteiro do SENTINELA-1, matriz de ameaças e riscos, pasta de controle
├── 06_Historia_Noite_do_Pacto/  personagens e história, cartas pra imprimir, página interativa e sprites
├── 07_Para_o_Publico/           folha de uma página pra quem assistiu e o PDF do público
└── 08_Identidade_e_Creditos/    guia do visual, logos, fontes e licenças das artes e dos ícones
```

## Antes de apresentar

1. **Instale as fontes** de [`08_Identidade_e_Creditos/Fontes/`](08_Identidade_e_Creditos/Fontes/) (Titillium Web e Dosis) no computador da apresentação. No Windows é botão direito no arquivo e "Instalar"; no macOS, abrir o arquivo e "Instalar fonte". Sem elas o PowerPoint troca a fonte: o layout continua de pé, mas fica menos bonito.
2. **Projete a versão do apresentador** no modo apresentação, pra que as notas fiquem só na tela de quem fala.
3. **Abra o painel do campeonato** no navegador do mesmo notebook e deixe numa aba. Ele não precisa de internet.
4. **Leve os PDFs como plano B.** Eles já levam as fontes dentro.

O checklist completo (acessibilidade, legenda ao vivo, quadro, tempo e passagens de bastão) está no guia da equipe.

## O campeonato

A parte prática é o **Campeonato da Noite do Pacto**, feito pra quem nunca estudou segurança. A sala se divide em quatro grupos, um por personagem: Corvina e Doc no Red, Lírio e Dona Ivone no Blue. Em cada round:

1. Hugo ou Isaque lê a cena;
2. o grupo da vez conversa um minuto e levanta a placa **A** ou **B**;
3. o painel rola um dado de 20 lados pra cada lado e soma **+3** pra jogada boa. Maior vence; empate é da defesa.

Ninguém faz conta. Depois de cada round, o mestre explica em uma frase por que a jogada boa era boa. São quatro rounds no mapa (sites A e B), um bilhete secreto de acordo entre a Corvina e o Lírio e o veredito da Corte de Prata. Um pendrive faz o papel da spike: ele é só objeto de cena, ninguém pluga em nada.

Quem conduz:
- **Higor:** mestre;
- **João:** painel, cronômetro e narração do Vava;
- **Hugo e Isaque:** cartões, cenas e o bilhete (o Isaque é o mensageiro);
- **Prof. Galvão:** Ysolde;
- **monitores:** Bené.

**Painel do Campeonato:** abrir `04_Campeonato/Painel_do_Campeonato.html` num navegador (Chrome, Edge ou Firefox). É um arquivo só, sem internet e sem instalar nada. O placar fica guardado no navegador se a página for recarregada; o botão "Zerar o campeonato" limpa tudo.

## Página interativa

Abra `06_Historia_Noite_do_Pacto/Pagina_interativa/index.html` no navegador; a pasta `img/` precisa ficar ao lado do arquivo. Com internet, a página carrega as fontes do Google Fonts. Sem internet ela funciona do mesmo jeito, com as fontes padrão do navegador.

## Regras do material

- Empresa, ameaças, notas e personagens são **fictícios**. Pesos, escalas e prazos marcados como exemplo são escolhas da equipe, não norma.
- Hacking ético só em ambiente próprio e isolado, ou com autorização por escrito e escopo definido.
- Antes de publicar na WikiTau, cada pessoa revisa a sua parte com as próprias palavras e mantém o rodapé que as diretrizes da WikiTau pedem quando houve apoio de IA.
- Wazuh, Datadog Watchdog e os kits de exercício citados são exemplos de categoria, não recomendação de produto.
- O pendrive do campeonato é objeto de cena: não deve ser plugado em nenhum computador.
- Os arquivos deste repositório são versões finais. Os scripts que geraram slides, planilhas e documentos não fazem parte dele.

## Licenças e créditos

| Item | Autoria | Licença |
|---|---|---|
| Cidade (Parallax Industrial) e casa de bombas (Bulkhead Walls) | Luis Zuno ([ansimuz.com](https://ansimuz.com)) | CC0 |
| Fundo da Corte da Maré (Underwater Fantasy) | Luis Zuno ([ansimuz.com](https://ansimuz.com)) | CC BY 3.0 |
| Fadas e Dona Ivone (Oracles 1.1, cores alteradas) | Svetlana Kushnariova (Cabbit), Nila122, olonu, leangoro e Jordan Irwin (AntumDeluge) | CC BY-SA 3.0 |
| Doc e Bené (sprites) | Equipe White Team 1 | CC BY-SA 3.0 |
| Molduras das cartas (Fantasy Card, Dark Cosmic) | cethiel ([OpenGameArt](https://opengameart.org/users/cethiel)) | **a confirmar** (ver abaixo) |
| Ícones (Font Awesome Free 6, recoloridos) | Fonticons, Inc. ([fontawesome.com](https://fontawesome.com)) | CC BY 4.0 |
| Fontes Titillium Web e Dosis | Accademia di Belle Arti di Urbino; The Dosis Project Authors | SIL Open Font License 1.1 |
| Visual inspirado nos modelos Donalbain e Mowbray | [SlidesCarnival](https://www.slidescarnival.com) | Creative Commons Attribution |
| Logo e coruja | UrutauSec | uso restrito a material do grupo |
| Arte dos agentes do Valorant (só nos slides 7 e 8) | Riot Games | política "Legal Jibber Jabber" da Riot, uso sem fins comerciais |

**Aviso da Riot Games:** este projeto foi criado sob a política "Legal Jibber Jabber" da Riot Games, usando recursos da Riot Games; a Riot Games não endossa nem patrocina este projeto. O material de jogo (painel e kit) usa só os nomes dos agentes, sem imagens, porque a política não permite usar a propriedade intelectual da Riot em jogos e aplicativos.

Os textos de licença estão em [`08_Identidade_e_Creditos/Licencas_das_artes/`](08_Identidade_e_Creditos/Licencas_das_artes/) e [`08_Identidade_e_Creditos/Fontes/`](08_Identidade_e_Creditos/Fontes/). O mosaico de pixels e as cunhas diagonais foram desenhados por script nas cores do grupo; nenhuma arte dos modelos foi copiada.

**Pendências antes de deixar o repositório público:**

- **Licença do conteúdo da equipe:** ainda não foi definida. Escolham uma e criem o arquivo `LICENSE`.
- **Molduras das cartas:** a página do autor pede crédito opcional, mas a licença não está registrada neste repositório. Confirmem no OpenGameArt ou troquem as molduras.
- **Arte dos agentes:** releiam a política da Riot antes de publicar a apresentação fora do grupo.

## Histórico de versões

**v9 (20/11/2026): campeonato pra iniciante**
- O paralelo com o Valorant passou pro João, que é de quem são as referências do jogo: ele apresenta os slides 7 a 9 e narra o Vava no campeonato.
- Cartões de fala com as falas do campeonato de cada pessoa: cartões de personagem e cenas (Hugo e Isaque), porquê de cada round (Higor), painel e narração (João).
- Painel cabe numa tela só, sem rolar, de 1024 × 768 pra cima, e mostra a linha "No Vava" de cada round.
- Campeonato simplificado: cada grupo escolhe A ou B com uma placa, o painel rola os dados e soma +3 pra jogada boa. Sem atributo, sem conta, sem escriba.
- Painel do Campeonato (HTML, sem internet), kit de impressão refeito (placas, cola do jogador, cenas pra ler, gabarito do mestre) e roteiro do mestre reescrito.
- O acordo escondido virou um bilhete de papel levado por um mensageiro. O WhatsApp e a Twitch saíram do material.
- Mundo e jogo mais visuais: slide das quatro leis do mundo, três slides do Vava com a arte dos agentes e slide de regulamento, admin e árbitro.
- Duração passou pra 1h25. Pastas renumeradas: o campeonato ganhou a pasta 04.

**v8 (20/11/2026): campeonato e Valorant**
- Paralelos com o Valorant em toda a apresentação e o primeiro Campeonato da Noite do Pacto. A atividade antiga ficou como plano B no apoio.
- Novas funções: o João apresenta os blocos 01 e 02; o Higor, o anti-manual, as ferramentas, as ameaças e o campeonato; Hugo e Isaque leem as aberturas, os cartões e as cenas.

**v7 (20/11/2026): visual novo**
- Slides claros, com mosaico de pixels na borda, cunhas diagonais nas aberturas de bloco, cena da noite em formato de citação e marca-texto nas frases-chave.
- Fontes Titillium Web e Dosis incluídas no pacote.

**v6 (20/11/2026): conteúdo**
- Versão do público de 34 pra 26 slides. Slide do jeito certo depois do anti-manual: registrar, provar e treinar.
- Personagens mais diversos, não repúdio no kit do SENTINELA-1, horário de 9h em todo o material, links clicáveis e texto alternativo nas imagens.
