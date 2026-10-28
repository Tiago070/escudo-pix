**INSTITUTO FEDERAL GOIANO \- CAMPUS CERES**  
**BACHARELADO EM SISTEMAS DE INFORMAÇÃO**

TIAGO CARDOSO FERREIRA  
FELIPE RAMOS SILVA REIS  
LUANNA FERNANDES DA SILVA

**ESCUDO PIX: SIMULADOR EDUCATIVO DE PREVENÇÃO A GOLPES DIGITAIS PARA O PÚBLICO IDOSO**

Documento de requisitos de software apresentado à disciplina de Programação para Dispositivos Móveis do curso de Bacharelado em Sistemas de Informação do Instituto Federal Goiano \- Campus Ceres.

Docente: Paulo César Melo

**1 INTRODUÇÃO	4**  
1.1 Contexto	4  
1.2 Objetivos	4  
1.3 Escopo do produto	4  
1.4 Definições e siglas	5  
**2 DESCRIÇÃO GERAL	6**  
2.1 Perspectiva do produto	6  
2.2 Usuários	6  
2.3 Restrições	6  
2.4 Premissas e dependências	6  
**3 REQUISITOS FUNCIONAIS	7**  
**4 REQUISITOS NÃO FUNCIONAIS	8**  
**5 REGRAS DE NEGÓCIO	9**  
**6 MODELO DE DADOS PRELIMINAR	10**  
**7 RISCOS E PENDÊNCIAS	11**  
7.1 Riscos	11  
7.2 Pendências	11  
**8 CRONOGRAMA PRELIMINAR	12**  
**REFERÊNCIAS	13**

# **1 INTRODUÇÃO**

## **1.1 Contexto**

Golpes aplicados por meios digitais, especialmente por mensagens de texto e aplicativos de conversa, atingem de forma recorrente pessoas idosas, que muitas vezes têm menor familiaridade com recursos tecnológicos e estão expostas a abordagens que exploram urgência, medo e confiança em familiares ou instituições.  
Propõe-se, assim, uma abordagem educativa em que o usuário pratica a identificação de sinais de alerta em um ambiente seguro, por meio de simulações, sem que o aplicativo precise acessar as conversas reais da pessoa. Este documento especifica os requisitos do projeto final da disciplina de Programação para Dispositivos Móveis, e adota, de forma simplificada, a estrutura de especificação descrita pela ISO/IEC/IEEE 29148 (2018).

## **1.2 Objetivos**

O objetivo geral é especificar os requisitos de um aplicativo móvel, desenvolvido em Flutter, que simula cenários de golpes digitais por mensagens para a educação de pessoas idosas. Os objetivos específicos são:

1) delimitar o escopo da versão mínima do produto;  
2) descrever as funcionalidades e as restrições de qualidade do aplicativo;  
3) estabelecer as regras de negócio que orientam a elaboração dos cenários;  
4) propor um modelo de dados preliminar para o banco SQLite;  
5) registrar os riscos, as pendências e o cronograma do projeto.

## **1.3 Escopo do produto**

O produto é um aplicativo móvel educativo que apresenta ao usuário cenários simulados de golpes aplicados por mensagens, permite que ele escolha como reagir, informa as consequências de cada escolha e explica os sinais de alerta presentes. O aplicativo também registra o histórico de desempenho em banco de dados local.  
Estão fora do escopo desta versão:

1) a leitura automática de mensagens do dispositivo;  
2) a análise de textos ou mensagens reais fornecidos pelo usuário;  
3) o uso de aprendizado de máquina;  
4) a autenticação com senha;  
5) a sincronização com serviços em nuvem;  
6) o envio de notificações;  
7) a integração real com contatos ou com o recurso de chamadas do dispositivo.

A leitura de mensagens reais foi descartada por restrições de acesso impostas pelos sistemas operacionais móveis e por questões de privacidade.

## **1.4 Definições e siglas**

Os principais termos utilizados neste documento estão definidos no Quadro 1\.

Quadro 1 \- Glossário

| Termo | Definição |
| ----- | ----- |
| Cenário | Situação simulada, composta por uma sequência de mensagens fictícias, que representa um golpe digital ou uma comunicação legítima. |
| Golpe digital | Tentativa de obter dinheiro, dados ou acesso do usuário por meios enganosos, aplicada por canais eletrônicos como SMS e aplicativos de mensagens. |
| Sinal de alerta | Característica de uma mensagem que indica possível fraude, como urgência, pedido de dinheiro ou de código de verificação, ou link suspeito. |
| Mensagem legítima | Mensagem genuína, usada em cenários de contraste para que o usuário aprenda a diferenciá-la de uma tentativa de golpe. |
| Tentativa | Execução completa ou parcial de um cenário por um usuário, com registro das escolhas feitas e do resultado. |
| Flutter | Framework de código aberto para o desenvolvimento de aplicativos móveis multiplataforma. |
| SQLite | Sistema de banco de dados relacional embarcado, que armazena os dados em um arquivo local no dispositivo. |
| MVP | Sigla de produto mínimo viável: versão do produto com as funcionalidades indispensáveis para entregar seu valor principal. |

Fonte: Elaborado pelos autores (2026).

# **2 DESCRIÇÃO GERAL**

## **2.1 Perspectiva do produto**

O produto é um aplicativo móvel autônomo, desenvolvido em Flutter, que funciona sem conexão com a internet e armazena todos os dados em banco SQLite no próprio dispositivo. Não há, nesta versão, servidor, conta de usuário nem comunicação com sistemas externos.

## **2.2 Usuários**

O público-alvo são pessoas idosas, assim entendidas aquelas com 60 anos ou mais, conforme o Estatuto da Pessoa Idosa (BRASIL, 2003), que utilizam smartphones e aplicativos de mensagens. Considera-se, como hipótese a ser validada em testes com usuários, que esse público pode apresentar familiaridade variável com tecnologia e eventuais limitações visuais e motoras, o que orienta os requisitos de acessibilidade e simplicidade deste documento. Não há perfil de administrador: todos os usuários dispõem das mesmas funcionalidades.

## **2.3 Restrições**

1) o aplicativo deve ser desenvolvido em Flutter;  
2) o armazenamento de dados deve utilizar SQLite;  
3) a plataforma Android é o alvo obrigatório;  
4) a entrega final ocorre na primeira semana de dezembro de 2026, com apresentações semanais de andamento ao professor;  
5) a equipe é composta por três integrantes;  
6) o funcionamento deve ser integralmente offline.

## **2.4 Premissas e dependências**

1) o professor ainda não definiu a exigência de API ou de autenticação, e este documento assume que não serão necessárias;  
2) os cenários serão elaborados pela equipe com base em fontes públicas sobre golpes digitais;  
3) haverá acesso a pessoas idosas para a validação do protótipo.

# **3 REQUISITOS FUNCIONAIS**

Os requisitos funcionais estão apresentados no Quadro 2\. A prioridade segue três níveis: essencial, indispensável para a versão mínima do produto; desejável, a ser implementado se o prazo permitir; e opcional, previsto apenas em caso de folga no cronograma. A redação procura atender às recomendações da ISO/IEC/IEEE 29148 (2018) para requisitos bem formados, como serem necessários, não ambíguos e verificáveis.

Quadro 2 \- Requisitos funcionais

| ID | Requisito | Prioridade |
| ----- | ----- | ----- |
| RF01 | O sistema deve permitir a criação de um perfil local simples, com nome ou apelido, sem exigência de senha. | Essencial |
| RF02 | O sistema deve listar os cenários agrupados por tipo de golpe: falso parente, falsa central bancária, benefício ou INSS falso, e cobrança ou boleto falso. | Essencial |
| RF03 | O sistema deve exibir cada cenário como uma conversa simulada, em etapas, em interface semelhante à de um aplicativo de mensagens. | Essencial |
| RF04 | A cada etapa, o sistema deve apresentar de duas a quatro opções de ação, como ignorar, bloquear, responder, ligar para o familiar, clicar no link ou informar dados. | Essencial |
| RF05 | Após cada escolha, o sistema deve mostrar a consequência da ação e uma explicação em linguagem simples. | Essencial |
| RF06 | Ao final do cenário, o sistema deve exibir um resumo com os sinais de alerta presentes na conversa e a orientação sobre o que fazer em uma situação real. | Essencial |
| RF07 | O sistema deve registrar cada tentativa (cenário, escolhas, resultado e data) em banco de dados local. | Essencial |
| RF08 | O sistema deve exibir o histórico e a evolução do usuário, com cenários concluídos e desempenho por tipo de golpe. | Essencial |
| RF09 | O sistema deve incluir cenários com mensagens legítimas, para que o usuário aprenda a distingui-las de golpes. | Essencial |
| RF10 | O usuário deve poder refazer qualquer cenário. | Desejável |
| RF11 | O sistema deve oferecer uma seção de consulta rápida por tipo de golpe, com sinais comuns e orientações de ação. | Desejável |
| RF12 | O usuário deve poder ajustar o tamanho da fonte. | Desejável |
| RF13 | O sistema deve permitir a revisão dos erros, reapresentando os cenários em que o usuário teve desempenho inadequado. | Opcional |
| RF14 | O sistema deve aumentar a dificuldade progressivamente, com golpes mais sofisticados conforme o desempenho do usuário. | Opcional |

Fonte: Elaborado pelos autores (2026).

A opção “ligar para o familiar”, prevista no RF04, é apenas uma alternativa dentro da simulação, sem integração real com contatos ou com chamadas do dispositivo. O RF09 evita que o usuário passe a desconfiar de toda mensagem recebida.

# **4 REQUISITOS NÃO FUNCIONAIS**

Os requisitos não funcionais estão apresentados no Quadro 3 e concentram-se na adequação do aplicativo ao público idoso, na privacidade e na facilidade de manutenção do conteúdo.

Quadro 3 \- Requisitos não funcionais

| ID | Categoria | Requisito |
| ----- | ----- | ----- |
| RNF01 | Acessibilidade visual | O texto do corpo deve ter fonte mínima de 18 sp e razão de contraste mínima de 4,5:1 em relação ao fundo, conforme o critério de nível AA da WCAG 2.1 (WORLD WIDE WEB CONSORTIUM, 2018). Nenhuma informação deve ser transmitida somente por cor. |
| RNF02 | Interação por toque | Os botões devem ter área mínima de 48 dp, com espaçamento que evite toques acidentais. |
| RNF03 | Simplicidade | Cada tela deve ter uma ação principal, e a navegação deve ter no máximo dois níveis. |
| RNF04 | Linguagem | Os textos devem ser escritos sem jargão técnico, e termos como phishing, quando necessários, devem vir acompanhados de explicação. |
| RNF05 | Disponibilidade | Todo o conteúdo e o banco SQLite devem funcionar sem conexão com a internet. |
| RNF06 | Privacidade | Os dados devem ficar armazenados apenas no dispositivo, sem coleta nem transmissão de dados pessoais reais, em consonância com os princípios da finalidade e da necessidade previstos na LGPD (BRASIL, 2018). |
| RNF07 | Segurança do conteúdo | Links e telefones presentes nos cenários não devem ser clicáveis nem discáveis, e toda tela de simulação deve indicar claramente que se trata de um treino. |
| RNF08 | Manutenibilidade | Os cenários devem ser armazenados como dados no SQLite, com carga inicial, de modo que seja possível adicionar conteúdo sem alterar o código. |
| RNF09 | Portabilidade | O aplicativo deve funcionar em Android; o suporte a iOS é desejável, desde que não comprometa o prazo. |
| RNF10 | Desempenho | A abertura do aplicativo e a troca de telas devem ocorrer sem travamentos perceptíveis em aparelhos de entrada. |

Fonte: Elaborado pelos autores (2026).

# **5 REGRAS DE NEGÓCIO**

As regras de negócio que orientam a elaboração e a avaliação dos cenários estão no Quadro 4\.

Quadro 4 \- Regras de negócio

| ID | Regra |
| ----- | ----- |
| RN01 | Todo cenário de golpe deve conter ao menos um sinal de alerta identificável, e todo cenário legítimo deve apresentar a explicação de por que é confiável. |
| RN02 | Cada etapa deve ter ao menos uma opção adequada, e a explicação deve ser apresentada para todas as opções, não somente para a correta. |
| RN03 | O aplicativo não deve afirmar que uma mensagem real é segura ou fraudulenta, pois trata exclusivamente de cenários simulados. |
| RN04 | O resultado de um cenário deve ser classificado como adequado, parcialmente adequado ou inadequado, conforme as escolhas do usuário, com critérios definidos antes da redação dos cenários. |
| RN05 | Todos os nomes, números de telefone, links, valores e instituições presentes nos cenários devem ser fictícios. |
| RN06 | As orientações ao usuário devem priorizar a confirmação da informação por um canal oficial ou por contato direto com a pessoa envolvida. |

Fonte: Elaborado pelos autores (2026).

# **6 MODELO DE DADOS PRELIMINAR**

O Quadro 5 apresenta as entidades previstas para o banco SQLite e seus principais atributos. O modelo é preliminar e poderá ser refinado na etapa de projeto.

Quadro 5 \- Entidades do banco de dados

| Entidade | Atributos | Descrição |
| ----- | ----- | ----- |
| usuario | id, nome, tamanho\_fonte | Perfil local do usuário. |
| tipo\_golpe | id, nome, descricao, orientacoes | Categoria de golpe, com orientações de ação. |
| cenario | id, tipo\_golpe\_id, titulo, eh\_legitimo, dificuldade | Situação simulada. |
| mensagem | id, cenario\_id, ordem, remetente, texto | Mensagens de cada cenário, em sequência. |
| opcao | id, mensagem\_id, texto, adequada, consequencia, explicacao | Ações possíveis em cada etapa. |
| sinal\_alerta | id, descricao | Catálogo de sinais de alerta. |
| cenario\_sinal | cenario\_id, sinal\_id | Associação entre cenários e sinais de alerta. |
| tentativa | id, usuario\_id, cenario\_id, data, resultado | Execução de um cenário por um usuário. |
| escolha | id, tentativa\_id, opcao\_id | Opção escolhida em cada etapa da tentativa. |

Fonte: Elaborado pelos autores (2026).

# **7 RISCOS E PENDÊNCIAS**

## **7.1 Riscos**

Os principais riscos identificados e as respectivas ações de mitigação estão no Quadro 6\.

Quadro 6 \- Riscos e mitigação

| Risco | Mitigação |
| ----- | ----- |
| Cenários insuficientes ou pouco realistas, comprometendo o valor educativo. | Definir responsáveis pela redação, basear os textos em cartilhas e materiais públicos sobre golpes e fazer revisão cruzada entre os integrantes. |
| Crescimento do escopo, como a inclusão de análise de mensagens ou aprendizado de máquina. | Manter os itens fora de escopo e aceitar mudanças somente com acordo do grupo e avaliação do prazo. |
| Ausência de validação com o público real. | Testar o protótipo com ao menos três pessoas idosas antes da entrega final e registrar as observações. |
| Efeito educativo não comprovado. | Limitar o objetivo ao desempenho em cenários simulados, sem prometer redução de golpes reais. |
| Definição tardia de exigência de API ou autenticação. | Consultar o professor imediatamente e manter o acesso a dados em camada separada da interface. |
| Interface inadequada em tamanho de fonte, contraste ou área de toque. | Prototipar as telas cedo e testá-las com o público-alvo. |
| Tom infantilizado, que afaste o público adulto. | Evitar elementos excessivos de gamificação e adotar linguagem respeitosa e objetiva. |

Fonte: Elaborado pelos autores (2026).

## **7.2 Pendências**

Ficam pendentes de definição:

1) a confirmação, com o professor, da exigência de API ou de autenticação;  
2) os responsáveis pela redação e pela revisão dos cenários, e as fontes de consulta;  
3) os critérios de classificação do resultado de um cenário (RN04);  
4) a identificação de ao menos três pessoas idosas para o teste do protótipo;  
5) o nome do aplicativo.

# **8 CRONOGRAMA PRELIMINAR**

O Quadro 7 apresenta uma proposta de distribuição das atividades em seis semanas, com uma entrega demonstrável em cada apresentação semanal. O cronograma está sujeito a ajustes conforme as orientações recebidas do professor.

Quadro 7 \- Cronograma preliminar

| Semana | Atividades | Entrega na apresentação |
| ----- | ----- | ----- |
| 1 | Fechamento dos requisitos, definição dos casos de uso, divisão de tarefas e consulta ao professor sobre API e autenticação. | Documento de requisitos. |
| 2 | Protótipo de telas, modelagem do banco, estrutura inicial do projeto Flutter e redação dos primeiros cenários. | Protótipo e modelo de dados. |
| 3 | Implementação do simulador (fluxo do cenário, opções e feedback) com os primeiros cenários. | Simulador funcional parcial. |
| 4 | Registro de tentativas, histórico e evolução; redação dos demais cenários, incluindo os legítimos. | Histórico e conteúdo completo. |
| 5 | Ajustes de acessibilidade, consulta rápida, ajuste de fonte e testes com pessoas idosas. | Versão para testes. |
| 6 | Correções, documentação final e preparação da apresentação. | Versão final. |

Fonte: Elaborado pelos autores (2026).

# **REFERÊNCIAS**

BRASIL. **Lei nº 10.741, de 1º de outubro de 2003**. Dispõe sobre o Estatuto da Pessoa Idosa e dá outras providências. Brasília, DF: Presidência da República, \[2003\]. Disponível em: https\://www\.planalto.gov.br/ccivil\_03/leis/2003/l10.741.htm. Acesso em: 21 out. 2026\.

BRASIL. **Lei nº 13.709, de 14 de agosto de 2018**. Lei Geral de Proteção de Dados Pessoais (LGPD). Brasília, DF: Presidência da República, \[2018\]. Disponível em: https\://www\.planalto.gov.br/ccivil\_03/\_ato2015-2018/2018/lei/l13709.htm. Acesso em: 21 out. 2026\.

ISO/IEC/IEEE. **ISO/IEC/IEEE 29148:2018**: systems and software engineering: life cycle processes: requirements engineering. Geneva: ISO, 2018\.

WORLD WIDE WEB CONSORTIUM. **Web content accessibility guidelines (WCAG) 2.1**. \[S. l.\]: W3C, 5 jun. 2018\. Disponível em: https\://www\.w3.org/TR/WCAG21/. Acesso em: 21 out. 2026\.
