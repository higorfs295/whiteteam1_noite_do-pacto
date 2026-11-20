# O papel da White Team em exercícios de cibersegurança

Material da equipe **White Team 1** para o Encontro 1 da trilha White Team do grupo de estudos **UrutauSec** (EMC/UFG): como planejar, conduzir e avaliar um exercício Red × Blue.

| | |
|---|---|
| **Pauta** | Encontro 1 da trilha White Team: fundamentos e descoberta de ameaças |
| **Apresentação** | Sábado, 21/11/2026, às 9h, Sala 101, EMC/UFG, com transmissão na Twitch |
| **Equipe** | Higor Ferreira (líder), Hugo, Isaque e João Vitor Carvalho |
| **Monitoria** | Thâmara Cordeiro, Eduardo Martins e Alyce Suza |
| **Versão** | v7 (20/11/2026) |

## Comece por aqui

| Pra quê | Arquivo |
|---|---|
| Apresentar (com notas de fala) | [`01_Apresentacao/UrutauSec_WhiteTeam1_Apresentador.pptx`](01_Apresentacao/UrutauSec_WhiteTeam1_Apresentador.pptx) |
| Compartilhar depois | [`01_Apresentacao/UrutauSec_WhiteTeam1_Publico.pdf`](01_Apresentacao/UrutauSec_WhiteTeam1_Publico.pdf) |
| Ensaiar | [`03_Guia_e_Cartoes_de_Fala/`](03_Guia_e_Cartoes_de_Fala/) |
| Publicar na WikiTau | [`02_WriteUp_WikiTau/WriteUp_WhiteTeam1.md`](02_WriteUp_WikiTau/WriteUp_WhiteTeam1.md) |
| Montar o exercício-exemplo | [`04_Kit_do_Exercicio/`](04_Kit_do_Exercicio/) |
| Conhecer a história | [`05_Historia_Noite_do_Pacto/Pagina_interativa/index.html`](05_Historia_Noite_do_Pacto/Pagina_interativa/index.html) |

## Estrutura

```text
.
├── 01_Apresentacao/             versão do apresentador (26 slides + 8 de apoio, com notas)
│   │                            e versão do público (26 slides), em .pptx e .pdf
│   └── Visual_anterior_escuro/  mesma apresentação no visual escuro da v6
├── 02_WriteUp_WikiTau/          texto base do write-up (.md pra colar no BookStack, .docx e .pdf)
├── 03_Guia_e_Cartoes_de_Fala/   guia da equipe e um cartão de fala por pessoa
├── 04_Kit_do_Exercicio/         roteiro do SENTINELA-1, matriz de ameaças e riscos, pasta de controle
├── 05_Historia_Noite_do_Pacto/  personagens e história, cartas pra imprimir, página interativa e sprites
├── 06_Para_o_Publico/           folha de uma página pra quem assistiu e o PDF do público
└── 07_Identidade_e_Creditos/    guia do visual, logos, fontes e licenças das artes
```

## Antes de apresentar

1. **Instale as fontes** de [`07_Identidade_e_Creditos/Fontes/`](07_Identidade_e_Creditos/Fontes/) (Titillium Web e Dosis) no computador da apresentação. No Windows é botão direito no arquivo e "Instalar"; no macOS, abrir o arquivo e "Instalar fonte". Sem elas o PowerPoint troca a fonte: o layout continua de pé, mas fica menos bonito.
2. **Projete a versão do apresentador** no modo apresentação, pra que as notas fiquem só na tela de quem fala.
3. **Leve os PDFs como plano B.** Eles já levam as fontes dentro.

O checklist completo (acessibilidade, legenda ao vivo, quadro, tempo e passagens de bastão) está no guia da equipe.

## Página interativa

Abra `05_Historia_Noite_do_Pacto/Pagina_interativa/index.html` no navegador; a pasta `img/` precisa ficar ao lado do arquivo. Com internet, a página carrega as fontes do Google Fonts. Sem internet ela funciona do mesmo jeito, com as fontes padrão do navegador.

## Regras do material

- Empresa, ameaças, notas e personagens são **fictícios**. Pesos, escalas e prazos marcados como exemplo são escolhas da equipe, não norma.
- Hacking ético só em ambiente próprio e isolado, ou com autorização por escrito e escopo definido.
- Antes de publicar na WikiTau, cada pessoa revisa a sua parte com as próprias palavras e mantém o rodapé que as diretrizes da WikiTau pedem quando houve apoio de IA.
- Wazuh, Datadog Watchdog e os kits de exercício citados são exemplos de categoria, não recomendação de produto.
- Os arquivos deste repositório são versões finais. Os scripts que geraram slides, planilhas e documentos não fazem parte dele.

## Licenças e créditos

| Item | Autoria | Licença |
|---|---|---|
| Cidade (Parallax Industrial) e casa de bombas (Bulkhead Walls) | Luis Zuno ([ansimuz.com](https://ansimuz.com)) | CC0 |
| Fundo da Corte da Maré (Underwater Fantasy) | Luis Zuno ([ansimuz.com](https://ansimuz.com)) | CC BY 3.0 |
| Fadas e Dona Ivone (Oracles 1.1, cores alteradas) | Svetlana Kushnariova (Cabbit), Nila122, olonu, leangoro e Jordan Irwin (AntumDeluge) | CC BY-SA 3.0 |
| Doc e Bené (sprites) | Equipe White Team 1 | CC BY-SA 3.0 |
| Molduras das cartas (Fantasy Card, Dark Cosmic) | cethiel ([OpenGameArt](https://opengameart.org/users/cethiel)) | **a confirmar** (ver abaixo) |
| Fontes Titillium Web e Dosis | Accademia di Belle Arti di Urbino; The Dosis Project Authors | SIL Open Font License 1.1 |
| Visual inspirado nos modelos Donalbain e Mowbray | [SlidesCarnival](https://www.slidescarnival.com) | Creative Commons Attribution |
| Logo e coruja | UrutauSec | uso restrito a material do grupo |

Os textos de licença estão em [`07_Identidade_e_Creditos/Licencas_das_artes/`](07_Identidade_e_Creditos/Licencas_das_artes/) e [`07_Identidade_e_Creditos/Fontes/`](07_Identidade_e_Creditos/Fontes/). O mosaico de pixels e as cunhas diagonais foram desenhados por script nas cores do grupo; nenhuma arte dos modelos foi copiada.

**Pendências antes de deixar o repositório público:**

- **Licença do conteúdo da equipe:** ainda não foi definida. Escolham uma e criem o arquivo `LICENSE`.
- **Molduras das cartas:** a página do autor pede crédito opcional, mas a licença não está registrada neste repositório. Confirmem no OpenGameArt ou troquem as molduras.

## Histórico de versões

**v7 (20/11/2026): visual novo**
- Slides claros, com mosaico de pixels na borda, cunhas diagonais nas aberturas de bloco, cena da noite em formato de citação e marca-texto nas frases-chave.
- Conteúdo, ordem e notas iguais aos da v6, então guia, cartões de fala e mapa de tempo continuam valendo.
- Fontes Titillium Web e Dosis incluídas no pacote.

**v6 (20/11/2026): conteúdo**
- Versão do público de 34 pra 26 slides. Equipes, futebol e tabletop x funcional viraram slides de apoio.
- Slide novo depois do anti-manual: registrar, provar e treinar (monitoramento, não repúdio e kits de exercício).
- Personagens mais diversos: Dona Ivone é uma mulher negra, o Doc é pardo e o Bené virou Bené Takeda, neto de imigrantes japoneses.
- Não repúdio no kit: seção 7.1 do roteiro do SENTINELA-1 e aba Integridade dos Logs na pasta de controle.
- Horário de 9h em todo o material, links clicáveis nas fontes, texto alternativo nas imagens e revisão de referências, contas e atribuições.
