---
title: "O papel da White Team em exercícios de cibersegurança"
subtitle: "Write-up do Encontro 1 da trilha White Team: Fundamentos e descoberta de ameaças"
---

**Trilha:** White Team · Encontro 1\
**Equipe:** Higor Ferreira (líder), Hugo, Isaque, João Vitor Carvalho\
**Criado em:** [data da publicação] · **Última atualização:** [data da última revisão]

# 1. Contexto e objetivo do tema

Em um exercício de cibersegurança, a Red Team simula o adversário e a Blue Team defende. Para que esse confronto seja seguro, justo e útil, uma terceira equipe precisa definir as regras, controlar o andamento e avaliar o resultado sem atacar nem defender: a White Team.

Esta página cobre a pauta oficial do Encontro 1 da trilha White Team da UrutauSec:

- o papel da White Team (governança, coordenação e arbitragem);
- os fundamentos (políticas, escopo, regras de engajamento e métricas);
- a descoberta de ameaças (fontes de inteligência, identificação de riscos e priorização);
- como a White Team conecta Red e Blue.

**Objetivo:** ao final, o leitor deve conseguir explicar o que a White Team faz e montar, para um laboratório isolado, um exercício-exemplo com regras, roteiro de eventos e critério de pontuação. O tratamento dos achados depois do exercício (validação, relatório pós-ação e melhoria contínua) é tema do Encontro 2 da trilha.

# 2. Conceitos principais

## 2.1 As equipes de um exercício

| Equipe | Papel |
|---|---|
| Red | Simula o adversário, só dentro do escopo acordado |
| Blue | Monitora, detecta, responde e contém |
| White | Organiza, controla o jogo e avalia os times; não ataca nem defende |
| Green | Mantém a infraestrutura do laboratório: isolamento, snapshots, telemetria |
| Purple | Não é um quarto time: é Red e Blue trabalhando juntos, abertamente, para transformar cada ataque em melhoria de detecção |

## 2.2 Governança, coordenação e arbitragem

- **Governança (antes):** a White Team decide o que pode e o que não pode, quem participa e como o exercício será avaliado.
- **Coordenação (durante):** ela controla o relógio, libera os eventos do roteiro e pode pausar o jogo.
- **Arbitragem (depois e durante):** ela julga com base em evidência e em critério conhecido por todos antes do início.

Uma analogia útil é o campeonato de futebol: o regulamento corresponde às regras de engajamento, a tabela de jogos ao roteiro de eventos (MSEL) e a súmula ao registro do avaliador.

Em engajamentos reais de red team, que costumam ser secretos para a maior parte da organização, o papel de White Team aparece nas poucas pessoas que sabem do teste (os *trusted agents*). Se a equipe de monitoramento detecta algo, são elas que dizem se é o red team ou um ataque real.

## 2.3 Dois formatos de exercício

O NIST SP 800-84 [1] descreve dois tipos de exercício:

- **Tabletop (de mesa):** só discussão; ninguém toca em teclado. Bom para treinar decisão, papéis e comunicação.
- **Funcional:** os participantes exercem seus papéis num ambiente operacional simulado. Bom para treinar detecção, contenção e recuperação.

Nos dois, a White Team prepara, controla e avalia. O exercício-exemplo desta página é funcional.

## 2.4 Ciclo de vida

A literatura sobre *cyber ranges* descreve um ciclo com fase de ensaio antes da execução [6]. Nesta página usamos cinco fases (exemplo): preparação, ensaio, execução, avaliação e repetição. A White Team é dona da preparação, do ensaio, da avaliação e da repetição, e controla a execução.

## 2.5 Políticas e autorização

A técnica de um hacker ético e a de um criminoso podem ser idênticas; o que muda é a **autorização**. No Brasil, a Lei 12.737/2012 incluiu no Código Penal o art. 154-A, que tipifica a invasão de dispositivo informático alheio [10]. Isto é orientação geral, não parecer jurídico. Por isso, todo exercício acontece em ambiente próprio e isolado, com escopo escrito.

Na WikiTau há uma regra adicional: exemplos e write-ups usam só dados fictícios ou anonimizados.

## 2.6 Escopo e regras de engajamento

**Escopo** é a lista do que está dentro do jogo (endereços, sistemas, janelas de tempo). **Regras de engajamento** (RoE) dizem o que cada time pode fazer. Guias de mercado sobre RoE para red team detalham esses componentes [8, 9].

Princípio adotado no exercício-exemplo (exemplo): **o que não está escrito como permitido está proibido**, e toda violação vira penalidade na nota.

## 2.7 Palavras de controle

| Palavra | Quem declara | Efeito |
|---|---|---|
| STARTEX | Diretor | Início oficial; o relógio começa em T+0 |
| PAUSA | Diretor ou árbitro | Todos param; nada é pontuado |
| RETOMA | Diretor | O jogo volta de onde parou |
| MUNDO REAL | Qualquer pessoa | Problema real (saúde, segurança, vazamento suspeito): encerra o jogo |
| ENDEX | Diretor | Fim do exercício |

StartEx aparece no material de treinamento do HSEEP [22], e um modelo de *C/E Handbook* (Montana, EUA) prevê o aviso de "real-world emergency" para emergências de verdade [23], que é o papel do nosso MUNDO REAL. ENDEX é o par de STARTEX, mas não foi conferido em fonte primária nesta pesquisa. PAUSA e RETOMA são definições da equipe (exemplo).

## 2.8 Métricas

A nota de cada Blue Team deve sair de registros, não de impressões. Fórmula proposta pela equipe (exemplo) (não é norma):

**S = 100 × (0,40·D + 0,40·R + 0,20·I) − P**

| Letra | Pergunta | Como se mede |
|---|---|---|
| D | O serviço ficou no ar? | checagens OK ÷ checagens feitas |
| R | A defesa foi boa? | pontos na rubrica ÷ pontos possíveis |
| I | Comunicou no prazo? | respostas no prazo ÷ eventos com prazo |
| P | Quebrou regra? | pontos descontados, validados pelo árbitro |

Os pesos são escolha da White Team; por isso são publicados antes do jogo e congelados no STARTEX. A ideia de definir antes da execução o que se espera da defesa e avaliar a partir de registros aparece em trabalho sobre avaliação automatizada de Blue Teams em *cyber ranges* [7].

## 2.9 Documentos da White Team

A metodologia HSEEP [5] organiza a documentação de um exercício. Os documentos usados no exemplo:

| Documento | Para que serve | Quando |
|---|---|---|
| Plano do exercício (ExPlan) | Objetivos, escopo, papéis, logística | Preparação |
| Regras de engajamento (RoE) | Permitido, proibido, como parar | Preparação |
| MSEL (*Master Scenario Events List*) | Lista cronológica de eventos e *injects* | Preparação: execução |
| Rubrica (EEG) | Critérios e níveis que o avaliador usa | Preparação: avaliação |
| Relatório pós-ação (AAR/IP) | Lições e plano de melhoria | Depois: tema do Encontro 2 |

Um *inject* é uma mensagem ou evento que a White Team insere no exercício em um horário definido para provocar uma decisão ou ação dos times.

## 2.10 Descoberta de ameaças

Antes de escrever o roteiro, a White Team pesquisa ameaças. Quatro fontes:

- **MITRE ATT&CK** [3]: catálogo público de táticas e técnicas observadas em ataques reais, com matriz Enterprise e matriz ICS (automação industrial).
- **CISA KEV** [4]: catálogo de vulnerabilidades com exploração confirmada. A própria CISA recomenda usá-lo como entrada da priorização no gerenciamento de vulnerabilidades.
- **Alertas e inteligência de ameaças (CTI):** o contexto do momento.
- **Histórico interno:** o que já aconteceu na organização (no exemplo, histórico fictício).

**Identificação e priorização.** O NIST SP 800-30 Rev. 1 [2] descreve a determinação de risco a partir da probabilidade e do impacto. No exemplo, cada ameaça recebe nota de 1 a 5 em probabilidade (P) e impacto (I), e a pontuação é P × I. A escala e os limiares (15 crítico, 10 alto, 5 moderado) são escolhas da equipe (exemplo).

**O filtro da White Team.** Priorizar não é o mesmo que escolher. Uma ameaça com nota alta só entra no exercício se passar por três perguntas:

1. É segura de simular no laboratório isolado?
2. Respeita as regras de engajamento (sem pessoas reais, sem dados reais)?
3. Serve a pelo menos um objetivo do exercício?

## 2.11 O profissional White Team e onde ele aparece

Fora do grupo de estudos, esse papel existe de verdade. No TIBER-EU, o framework europeu de red team para o setor financeiro, a equipe dentro da empresa testada que planeja e gerencia o teste se chamava oficialmente White Team [12]. Na versão de 2025, alinhada com a regulação DORA, o nome passou a ser *control team*, e o guia diz que ela responde pelo planejamento, gestão do projeto, gestão de risco e comunicação entre os envolvidos [12].

No dia a dia, quem faz esse papel:

- **antes**: define objetivos e escopo com quem autoriza o teste, escolhe o cenário a partir de ameaças reais e escreve regras, roteiro e gabarito;
- **durante**: controla o relógio e os eventos, responde dúvidas, diz se um alerta é o teste ou um ataque real e pausa se houver risco;
- **depois**: junta as evidências, calcula a nota e entrega o relatório com o plano de melhoria.

O perfil mistura noção técnica de ataque e defesa com gestão de projeto, risco e comunicação. No Brasil, um exemplo de grande porte é o Guardião Cibernético, exercício coordenado pelo Comando de Defesa Cibernética do Exército [13].

## 2.12 Como a White Team conecta Red e Blue

A White Team entrega ao Red o roteiro e as regras, e ao Blue os eventos e as regras. Recebe o log de ações do Red e os relatórios do Blue, e devolve nota e lições para os dois. Os encontros anteriores das trilhas Red e Blue (reconhecimento, segurança web, resposta a incidentes e táticas do adversário) são o material que a White usa para montar o cenário. Para escrever o gabarito do Blue, isto é, o que se espera da defesa, ajuda partir das recomendações de resposta a incidentes do NIST SP 800-61 Rev. 3 [14].

# 3. Passo a passo: montar o exercício-exemplo SENTINELA-1

Tudo abaixo usa uma **organização fictícia** (uma companhia de saneamento com rede de TI e uma parte de automação) e um **laboratório isolado**. Os números são didáticos (exemplo). As planilhas citadas estão no kit que acompanha esta página.

**Passo 1. Defina os objetivos.** O1 detecção · O2 contenção e recuperação · O3 comunicação · O4 decisão.

**Passo 2. Liste e pontue as ameaças.**

| ID | Ameaça | P | I | P × I | Entra? | Motivo |
|---|---|---|---|---|---|---|
| A1 | Credencial fraca ou vazada | 4 | 4 | 16 | Sim | Simulável com contas de teste |
| A2 | Ransomware na rede de TI | 3 | 5 | 15 | Não nesta edição | Simular criptografia real é arriscado; cabe num tabletop |
| A7 | Phishing contra o administrativo | 4 | 3 | 12 | Não | Engenharia social contra pessoas reais viola as RoE |
| A3 | Comando não autorizado ao CLP | 2 | 5 | 10 | Sim | Testa detecção em automação simulada |
| A5 | Varredura e descoberta de serviços | 5 | 2 | 10 | Sim | Primeiro passo do adversário |
| A6 | Negação de serviço no portal web | 3 | 3 | 9 | Sim | Mede disponibilidade (D) |
| A4 | Manipulação da tela da IHM | 2 | 4 | 8 | Sim | Testa se o Blue confere o processo, não só a tela |
| A8 | Vazamento de dados de clientes | 2 | 4 | 8 | Não nesta edição | Exigiria base fictícia grande e regras extras |

**Passo 3. Mapeie cada ameaça escolhida para uma técnica do ATT&CK** [3]. A5 vira T1046 Network Service Discovery e T0846 Remote System Discovery (ICS); A1 vira T1078 Valid Accounts; A3 vira T1692.001 Unauthorized Message: Command Message (ICS); A4 vira T0832 Manipulation of View (ICS); A6 vira T1499 Endpoint Denial of Service.

> Atenção ao versionamento: o antigo ID T0855 (*Unauthorized Command Message*) hoje redireciona, no site do ATT&CK, para T1692.001. Confira os IDs na data de publicação.

**Passo 4. Escreva o MSEL.** Cada ameaça vira um evento com horário, ação esperada do Blue (o gabarito) e critério da rubrica. Trecho:

| T+ (min) | Evento | Gabarito | Testa |
|---|---|---|---|
| 10 | Red: descoberta de serviços no segmento de TI (A5) | Detectar e registrar | O1 |
| 18 | Red: acesso com conta de teste de senha fraca (A1) | Detectar, bloquear e registrar | O1/O2 |
| 25 | Coordenação pede relatório de situação em 10 min | Enviar relatório | O3 |
| 40 | Red: comando não autorizado ao CLP simulado (A3) | Ver alteração, origem e horário; restaurar | O1/O2 |
| 48 | Dilema: isolar a automação por 10 min? | Decisão escrita e justificada | O4 |
| 75 | Red: negação de serviço no portal web (A6) | Conter e manter o serviço no ar | O2 |

O MSEL completo tem 15 eventos em 2 horas.

**Passo 5. Escreva a rubrica e as regras.** Sete critérios com níveis de 0 a 3 (detecção, relatório de incidente, contenção, recuperação, relatório de situação, decisão no dilema, comunicação externa) e a tabela de permitido e proibido para cada time.

**Passo 6. Ensaie.** Rode todos os eventos sem plateia; peça que dois avaliadores pontuem o mesmo relatório de teste. Se discordarem em mais de um nível, o descritor da rubrica está ambíguo.

**Passo 7. Execute e pontue.** Exemplo com o Blue A (exemplo): D = 22/24 = 0,917; R = 17/21 = 0,810; I = 4/5 = 0,800; P = 0.

S = 100 × (0,40 × 22/24 + 0,40 × 17/21 + 0,20 × 4/5) − 0 ≈ **85,05** (85,0 com uma casa decimal, como mostra a planilha)

Se a conta for feita com os valores já arredondados (0,917; 0,810; 0,800), dá 85,08. A diferença é só arredondamento.

Para reproduzir: abra a Pasta de Controle, aba Pontuação, e substitua os valores em azul.

## 3.1 O que não fazer (anti-manual)

Pra entender por que cada pilar do Manual Operacional White Team (ROE-WT-2026, material da monitoria) existe, ajuda virar cada um do avesso. Nenhuma dessas decisões é crime, só péssima ideia.

| Pilar | A pior decisão possível | Por que dá errado |
|---|---|---|
| Imparcialidade | Dar dica só pro time que trouxe café | A nota passa a medir amizade, não defesa, e ninguém confia no resultado |
| Segurança e escopo | Desligar a parada de emergência pra não atrapalhar o ritmo | Se algo sair do controle, não tem como parar |
| Auditabilidade | Registrar tudo de cabeça | Nenhuma nota pode ser defendida; o relatório vira opinião |
| Suporte e estabilidade | Restaurar o snapshot no meio do ataque, sem avisar | Apaga as evidências e o trabalho dos dois times |

## 3.2 O jeito certo: registrar, provar e treinar

O avesso do "o log sou eu" é um registro em que ninguém consegue negar depois o que fez. O glossário do NIST chama isso de não repúdio: garantia de que nenhuma das partes pode negar depois ter processado a informação, ou a capacidade de determinar se uma pessoa realizou uma ação [15]. Na prática, a White Team consegue isso com três cuidados.

| Palavra | O que é | Exemplos e cuidados |
|---|---|---|
| Observar | Monitoramento e observabilidade: ver o ambiente enquanto o exercício acontece | Plataformas abertas, como o Wazuh [16], ou comerciais com detecção automática de anomalia, como o Datadog Watchdog [17]. No SENTINELA-1, a checagem de disponibilidade a cada 5 min cumpre esse papel |
| Provar | Não repúdio no registro do exercício | Logs centralizados fora do alcance dos times; relógio sincronizado (NTP); registro com hash ou assinatura; armazenamento que só aceita acréscimo; log do Red com o ID de cada evento do roteiro. No kit, a aba Integridade dos Logs da Pasta de Controle guarda o *hash* de cada arquivo |
| Treinar | Não começar do zero | Kits em repositório público: *ir-tabletop-library* [11] (tabletops de resposta a incidente), *Atomic Red Team* [18] (testes ligados ao ATT&CK), *MITRE Caldera* [19] (emulação de adversário; usar só em laboratório isolado), *BOTS v3* da Splunk [20] (base de dados e CTF de defesa) e os pacotes de tabletop da CISA [21] |

Os nomes de ferramenta acima são exemplos de categoria, não recomendação de produto. Antes de usar qualquer uma, conferir a licença e a documentação da versão atual.

# 4. Ferramentas e referências

**Kit da equipe (fictício e didático):** Matriz de Ameaças e Riscos (.xlsx), Pasta de Controle com MSEL, rubrica, registro e pontuação (.xlsx), Roteiro do Exercício SENTINELA-1 com RoE e anexos.

**Material sugerido pelo monitor Eduardo Martins:** NIST SP 800-84 [1] e o repositório *ir-tabletop-library* [11], com cenários fictícios de tabletop, guia do facilitador, cartões de *inject* e modelo de relatório pós-ação (licença MIT).

## Referências

1. GRANCE, T. et al. *Guide to Test, Training, and Exercise Programs for IT Plans and Capabilities*. NIST SP 800-84, 2006. <https://csrc.nist.gov/pubs/sp/800/84/final>
2. NIST. *Guide for Conducting Risk Assessments*. NIST SP 800-30 Rev. 1, 2012. DOI 10.6028/NIST.SP.800-30r1. <https://csrc.nist.gov/pubs/sp/800/30/r1/final>
3. MITRE. *ATT&CK*. Técnicas citadas: <https://attack.mitre.org/techniques/T1046>, <https://attack.mitre.org/techniques/T1078>, <https://attack.mitre.org/techniques/T1499>, <https://attack.mitre.org/techniques/T0846>, <https://attack.mitre.org/techniques/T0832>, <https://attack.mitre.org/techniques/T1692/001/>. Acesso em 13/11/2026.
4. CISA. *Known Exploited Vulnerabilities Catalog*. <https://www.cisa.gov/known-exploited-vulnerabilities-catalog>
5. FEMA. *Homeland Security Exercise and Evaluation Program (HSEEP)*, 2020: consultado via guia de exercícios do estado de Indiana: <https://in.gov/dhs/files/idhs-exercise-guide.pdf>
6. YAMIN, M. M. et al. Cyber ranges and security testbeds: scenarios, functions, tools and architecture. *Computers & Security*, v. 88, 2020. DOI 10.1016/j.cose.2019.101636
7. *Scalable and automated evaluation of Blue Team cyber posture in cyber ranges*. arXiv:2312.17221, 2023. <https://arxiv.org/abs/2312.17221>
8. COBALT. *Red Team Rules of Engagement (RoE): A Comprehensive Checklist & Guide*. <https://www.cobalt.io/learning-center/red-team-rules-of-engagement-comprehensive-checklist>
9. SECURE.COM. *Red Team Rules of Engagement*. <https://www.secure.com/blog/soc/red-team-rules-of-engagement>
10. BRASIL. Lei nº 12.737, de 30 de novembro de 2012. <https://www.planalto.gov.br/ccivil_03/_ato2011-2014/2012/lei/l12737.htm>
11. MAWAZO, R. *ir-tabletop-library*. GitHub, 2026, licença MIT. <https://github.com/SecurityNomad/ir-tabletop-library>
12. EUROPEAN CENTRAL BANK. *TIBER-EU Framework* e *TIBER-EU Control Team Guidance*, 2025. <https://www.ecb.europa.eu/paym/cyber-resilience/tiber-eu/>
13. FGV PROJETOS; COMANDO DE DEFESA CIBERNÉTICA. *Manual de Orientação sobre Exercícios de Cibersegurança*. <https://projetos.fgv.br/sites/default/files/2025-03/manual-de-orientacao-sobre-exercicios-de-ciberseguranca_0.pdf>
14. NIST. *Incident Response Recommendations and Considerations for Cybersecurity Risk Management*. SP 800-61 Rev. 3, 2025. DOI 10.6028/NIST.SP.800-61r3. <https://csrc.nist.gov/pubs/sp/800/61/r3/final>
15. NIST. *Glossary: non-repudiation* (definição da CNSSI 4009). <https://csrc.nist.gov/glossary/term/non_repudiation>. Acesso em 20/11/2026.
16. WAZUH. *Wazuh: open source XDR and SIEM*. <https://github.com/wazuh/wazuh>. Acesso em 20/11/2026.
17. DATADOG. *Watchdog*. <https://www.datadoghq.com/product/watchdog/>. Acesso em 20/11/2026.
18. RED CANARY. *Atomic Red Team*. <https://github.com/redcanaryco/atomic-red-team>. Acesso em 20/11/2026.
19. MITRE. *Caldera*. <https://caldera.mitre.org> e <https://github.com/mitre/caldera>. Acesso em 20/11/2026.
20. SPLUNK. *BOTS v3: sample security dataset and CTF platform*. <https://github.com/splunk/botsv3>. Acesso em 20/11/2026.
21. CISA. *CISA Tabletop Exercise Packages (CTEP)*. <https://www.cisa.gov/cisa-tabletop-exercises-packages>. Acesso em 20/11/2026.
22. FEMA. *HSEEP Participant Guide, Training Module 4: Exercise Conduct* (curso L0146, versão 13.1), cópia publicada pela Nevada Division of Emergency Management. <https://dem.nv.gov/uploadedFiles/demnvgov/content/raining/HSEEP%20GUIDE%20-%20Module%204.pdf>. Trecho conferido via busca em 20/11/2026.
23. MONTANA DISASTER AND EMERGENCY SERVICES. *Controller/Evaluator (C/E) Handbook* (modelo). <https://des.mt.gov/preparedness/Training_Exercise/CE-Handbook-Template.docx>. Trecho conferido via busca em 20/11/2026.

# 5. Autores (equipe)

- **Higor Ferreira** (líder): descoberta de ameaças, priorização e exercício-exemplo
- **Hugo**: papel da White Team
- **João Vitor Carvalho**: fundamentos (formatos, autorização, escopo, regras e métricas)
- **Isaque**: anti-manual da White Team e o jeito certo (registrar, provar e treinar)

Monitores da trilha White Team: Thâmara Cordeiro, Eduardo Martins e Alyce Suza.

---

*conteúdo autoral e revisado por apoio de ia Claude*
