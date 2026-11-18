# Preguiça 3D

Pasta de produção de vídeos curtos animados em 3D (9:16) para um canal de curiosidades. Estas instruções valem pra
qualquer IA que trabalhe nesta pasta (Claude Code, Codex, Gemini CLI, Cursor, GitHub Copilot e outras).

**Fale sempre em português** (ou no idioma em que a pessoa escreve), do começo ao fim da conversa: nas notícias de cada
etapa, no relatório, na entrega do vídeo e no resumo do fim, mesmo quando a saída de um comando ou um erro vier em
inglês. Já aconteceu de a resposta do vídeo pronto vir em inglês.

## Regras

- Nunca copiar roteiro, frase ou visual de outro canal. A fórmula é livre; o texto e a identidade são do usuário
- Nunca mostrar nem enviar o conteúdo do `.env`
- O motor (`motor/`) é da Máquina e é trocado inteiro a cada versão nova: nunca mexa nele. O que é só do canal fica em
  `canal/` (as peças próprias em `canal/pecas/`, ver "Melhorar a Máquina")
- **Gastar pouco da cota da IA da pessoa** (muita gente usa IA grátis): tudo o que você lê fica na conversa e é relido a
  cada passo, até o fim. Leia a cola da etapa (regra número 5) e só o que ela manda, cada arquivo uma vez só. **Nunca
  abra o código do `motor/`** (são milhares de linhas): a ficha de uma peça, com as opções e o que ela devolve, sai com
  `npm run kit -- <nome>`; procurar uma peça, `npm run kit -- buscar <palavra>`; um cenário com os lugares e as
  posições, `npm run kit -- cenario <nome>`
- **Viralizar, redes e postagem:** pergunta sobre como viralizar, que hora postar, quantos vídeos fazer, o que marcar
  no YouTube, no Instagram ou no TikTok, música, aviso de IA, monetização, um número que caiu ou "pode fazer isso?":
  leia o arquivo do assunto em `viralizar/` (o `LEIA-PRIMEIRO.md` diz qual) antes de responder, e diga a fonte quando
  for regra da rede. Regra de rede muda: se a pessoa disser que o app dela está diferente, vale o app
- **Câmera perto e viva:** em todo `cena.js`, a câmera chega perto (o personagem ocupa pelo menos 1/3 da altura da tela;
  `aberto` só no gancho, numa revelação e no fim), anda com vontade em toda frase e nunca filma junto duas coisas longe
  uma da outra (as regras: `referencias/COMO-FAZER-O-VIDEO.md`, "As regras da câmera"). A revisão confere
- **Canal em outro idioma (Canal Gringo):** se o `canal/canal.md` tem a linha `**Idioma dos vídeos:**`, tudo o que vai
  pro vídeo e pra postar sai nesse idioma (roteiro, legenda, capa, rótulos, título, descrição, hashtags e comentário
  fixado), e a conversa com a pessoa continua em português (`comandos/extras-canal-gringo.md`)
- **Ajudar antes do suporte:** erro ou dúvida, quem resolve é você: leia a mensagem, procure no guia do comando, tente
  de novo e explique pra pessoa em palavras simples. O suporte (desconstruindouniverso@gmail.com, com o print do erro,
  o sistema do computador e o que a pessoa estava fazendo) é só pra compra, reembolso e acesso à área de membros, ou
  depois de você tentar de verdade, mais de uma vez, sem resolver

## Começo de toda conversa (regra número 1)

Na primeira resposta da conversa, seja qual for a mensagem (até um "oi"), e antes de qualquer pedido (vídeo, roteiro,
capa, texto de postar), seguir `comandos/boas-vindas.md`:
1. **Avisar** em uma frase, antes de rodar qualquer coisa, que vai dar uma olhada rápida se está tudo instalado e
   configurado
2. **Conferir:** rodar `npm run conferir` (se o comando nem existir, o Node.js não está instalado). Respondeu
   **PRONTO**: ler `canal/canal.md`, `canal/identidade.md`, `canal/aprendizados.md`, `canal/pauta.md` e as últimas ~15
   linhas de `canal/historico.md` (onde a conversa anterior parou), tudo num comando só
3. **Relatório:** contar em palavras simples o que está pronto, o que falta, quem resolve e quanto leva. Tudo pronto
   numa conversa de volta: uma linha só
4. **Boas-vindas:** a apresentação na primeira vez, 2 ou 3 linhas nas outras. Uma vez só por conversa
5. **PRONTO**: seguir com o pedido. **FALTA CONFIGURAR**: não começar o pedido. Se a pessoa já tinha pedido um vídeo,
   explicar em uma frase que sem a instalação e o canal configurados o vídeo sai genérico e gasta a cota da IA à toa.
   Perguntar se pode resolver e conduzir `comandos/instalar.md` (só o que o relatório marcou como falta). Terminou e o
   conferir deu PRONTO: se foi preciso fazer a entrevista do canal, o pedido vai pra uma conversa nova (regra número 3,
   com o pedido anotado na pauta e pronto pra copiar); se faltava só um conserto rápido, voltar ao pedido aqui mesmo

## Rodar os comandos sem travar (regra número 2)

Quem roda os comandos é você, a IA. **Nunca peça pra pessoa abrir o terminal, o PowerShell ou o arquivo `.env`**: ela
provavelmente nunca fez isso, e é aí que a instalação trava.
- **Instalar ou consertar a instalação:** `npm run instalar`. Ele faz tudo sozinho (peças do motor, navegador que
  desenha o vídeo e um teste com o vídeo de exemplo), fala em palavras simples e termina com `RESULTADO:` e uma linha
  `PRA IA:` com o próximo passo. Siga essa linha. Pode rodar quantas vezes precisar: o que já está pronto ele só confere
- **Chave da ElevenLabs:** `npm run chave` abre uma janelinha no navegador da pessoa, com o passo a passo e uma caixa pra
  colar a chave. A janela salva no `.env` certo, testa e diz se funcionou; a pessoa só volta e diz "salvei"
- **Não instale nada além do que o `npm run instalar` instala.** A Máquina tem motor próprio (o Three.js desenha, um
  navegador escondido fotografa cada quadro e o ffmpeg junta o vídeo). Remotion, HyperFrames, Python, outro navegador,
  editor de vídeo ou biblioteca nova não são usados e só confundem
- **Comando demorado** (instalar, render): rodar com tempo limite longo, de 15 minutos ou mais. Se parar no meio, rodar
  de novo: o `npm run instalar` continua de onde parou
- **Pedido de permissão do seu programa** (pra rodar um comando, usar a internet, abrir o navegador que desenha o vídeo
  ou a janelinha da chave): avisar a pessoa em uma frase que é a Máquina trabalhando e que pode aceitar. Com a internet
  bloqueada ou numa "sandbox", o download e o navegador não funcionam: peça a permissão (no Codex, a pessoa pode
  escolher "Acesso completo")
- **Windows:** se o `npm` der "a execução de scripts foi desabilitada neste sistema" (é o `npm.ps1` do PowerShell), use
  `npm.cmd` no lugar de `npm` (`npm.cmd run instalar`) ou rode o arquivo direto (`node motor/instalar.js`). Não mexa na
  política de execução do Windows
- **O navegador não abre** ("o Chromium falhou ao iniciar", "erro de configuração do Windows"): não conserte na mão. O
  motor tenta sozinho o Chromium da Máquina, o Microsoft Edge e o Google Chrome. Rode `npm run instalar`: ele testa,
  baixa de novo se precisar e explica o que fazer se nenhum abrir

## Uma conversa pra configurar, uma conversa nova pra cada vídeo (regra número 3)

A Máquina tem duas etapas, e cada uma fica na sua conversa:
1. **Configurar** (uma vez só, numa conversa): instalar, a entrevista do canal, a voz e o perfil no painel
   (`comandos/instalar.md`). Ela termina na passagem pra conversa nova (passo 6 de lá): nenhum vídeo começa nela
2. **Vídeos** (uma conversa nova pra cada vídeo): do tema à entrega, com os ajustes daquele vídeo

Por quê: a memória de uma conversa tem limite, e tudo o que está nela é relido a cada passo (é isso que gasta a cota da
IA). Quando enche, a IA resume a conversa e esquece detalhes do método, e o vídeo sai bem pior (no teste com IA grátis,
a conversa foi resumida duas vezes antes do vídeo ficar pronto). Na gravação do curso, a mesma tarefa feita no fim de
uma conversa cheia gastou umas 4 vezes mais que numa conversa nova. Nada se perde: o que importa está em `canal/` e em
`videos/<tema>/`, e a conversa nova lê tudo do zero.
- **Pedido de vídeo na conversa que fez a entrevista do canal**, ou **um segundo vídeo numa conversa que já fez um vídeo
  inteiro:** explicar em uma frase por que fica melhor numa conversa nova, anotar o tema em `canal/pauta.md` e passar a
  mensagem de passagem (modelo no passo 6 de `comandos/instalar.md`). Se a pessoa preferir seguir aqui mesmo, seguir
- **Depois do vídeo entregue**, só ajuste daquele vídeo segue na mesma conversa (uma cena, a capa, o texto de postar).
  Outra tarefa grande (estudar ou comparar virais, mexer no canal, consertar algo da Máquina) vai pra uma conversa nova,
  do mesmo jeito: uma frase do porquê e a mensagem pronta pra colar lá, com o pedido dela. Se ela preferir seguir aqui,
  seguir
- **Numa conversa que acabou de começar, nunca pedir conversa nova:** é nela que o vídeo é feito
- Conserto rápido (trocar a voz, instalar de novo, mudar uma cor, escrever o texto de postar) não pede conversa nova
- **Como abrir uma conversa nova**, pra dizer à pessoa no programa dela:

| Programa | Conversa nova |
|---|---|
| Claude Code no VS Code | o botão de conversa nova, no alto do painel do Claude |
| Claude Code no terminal | digitar `/clear` |
| Codex | o botão **+** no alto do painel do Codex (no terminal: `/new`) |
| Cursor, GitHub Copilot | o botão **+** (nova conversa) no alto do chat |
| Gemini CLI | digitar `/quit` e abrir de novo (`gemini`) |
| Outro, ou na dúvida | o botão "Nova conversa" do programa, ou fechar e abrir o programa de novo |

## O painel sempre à mão (regra número 4)

O painel (`npm run painel`) é uma página no navegador da pessoa: os vídeos, as cenas, o texto de postar, o canal. Ela
pode não saber abrir uma página sozinha, então **quem abre é você**, e **toda resposta sua termina com o link do painel**.
- **Os comandos abrem sozinhos:** o `npm run instalar` (no fim, em "Comece aqui"), o `--revisar` (nas cenas), o vídeo
  completo (no vídeo pronto) e o `npm run canal` (em "Meu canal"). Quando um comando mostrar a linha `PAINEL:`, mande
  o link dela pra pessoa, clicável, e siga a linha `PRA IA:` logo abaixo
- **Começo da conversa:** o `npm run conferir` mostra `PAINEL: ligado` (com o link) ou `PAINEL: desligado`. Desligado:
  rode `npm run painel`, que abre na tela dela. No Claude Code, o painel já liga sozinho quando a conversa começa
- **Fim de toda resposta que entrega alguma coisa** (o relatório do começo, o roteiro, as cenas, o vídeo, o texto de
  postar, uma mudança no canal): o link do painel, clicável, e uma frase do que ela vê lá. Sem o link à mão,
  `npm run painel -- --link` liga o painel sem abrir aba nova e mostra o link
- **"Não abriu", "cadê o painel?", "não achei":** rode `npm run painel` de novo, mande o link clicável e diga que também
  dá pra abrir com **dois cliques no arquivo `ABRIR-PAINEL`**, na pasta da Máquina (`ABRIR-PAINEL.command` no Mac,
  `ABRIR-PAINEL.bat` no Windows)
- Nunca diga "abre o painel" ou "olhe no painel" sem ter rodado o comando você mesmo, e nunca peça pra pessoa abrir o
  terminal pra isso
- **Os menus:** Comece aqui (o que falta, o backup no GitHub, os pacotes de modelos 3D), Meu canal (as perguntas do canal
  e, no fim, Os roteiros, o método que ela pode mudar), Vídeos (cada vídeo, as cenas com Gostei ou Mudar e o "Mandar pra
  IA"), Modelos 3D, Potencializar a máquina (os extras), Estudar virais, Conquistas, Sobre e Ajuda. **O que a pessoa
  salva em Meu canal muda os arquivos do canal**: leia de novo antes de cada vídeo e não desfaça sem perguntar. O que cada
  menu faz, os comandos de cada um e quando abrir: `comandos/painel.md`

## A cola de cada etapa (regra número 5)

A Máquina sabe muita coisa (o método, 141 dicas de viralizar, as regras da câmera, o cardápio de cenas, o kit), e
ninguém lembra de tudo. Por isso, **cada etapa de um vídeo começa rodando a cola dela**, lida até a última página. A
cola tira de cada guia, na hora, só o que vale naquela etapa, com o que o canal mudou no painel (`canal/metodo.md`) já
no lugar e o que a pessoa ensinou (`canal/aprendizados.md`) junto. Siga a cola, não a memória nem o que você leu em
outra conversa: o canal muda, e as revisões cobram o que está nela.

| Etapa | Rode |
|---|---|
| Escolher o tema (a pessoa não deu um) | `npm run guia -- tema` |
| Escrever o roteiro | `npm run guia -- roteiro <tema>` |
| A ficha de cena | `npm run guia -- ficha <tema>`; no fim, `npm run roteiro -- <tema>` até APROVADO |
| O `roteiro.json`, o `cena.js` e a capa | `npm run guia -- cena <tema>` (já traz a ficha das peças da sua tabela) |
| O texto de postar | `npm run guia -- postar <tema>` |

- **Leia todas as páginas.** A cola sai em páginas, pra caber no que você lê de uma vez; a linha `PRA IA:` do fim de
  cada página diz o comando da próxima (`npm run guia -- roteiro <tema> 2`), e a da última diz o próximo passo
- **`npm run roteiro -- <tema>` é a revisão do roteiro e da ficha de cena**, antes de qualquer código: o gancho, o
  tamanho, o fechamento, a tabela dos objetos e, em cada frase, as 10 linhas por extenso, o personagem com duas ações,
  a câmera diferente da anterior e o "mostra". Só mostre o roteiro pra pessoa com `RESULTADO: APROVADO`. O `--revisar`
  das cenas roda ela de novo, e o vídeo completo não sai com o `roteiro.md` pra corrigir
- **Uma peça que a cola não trouxe:** `npm run kit -- <nome>` (a ficha) ou `npm run kit -- buscar <palavra>`, nunca o
  código do `motor/`
- Pedido de mudança no meio de uma etapa (outro gancho, outra cena): não precisa rodar a cola de novo, mas rode a
  revisão daquela etapa depois de mudar

## Dar notícia, pra pessoa não achar que travou (regra número 6)

Fazer um vídeo leva de 30 minutos a 1 hora, e a maior parte é você lendo, pensando e escrevendo, sem nada mudar na tela
da pessoa. Na gravação do curso da Máquina, quem assistia achou várias vezes que tinha travado. Por isso:
- **Antes de cada etapa**, uma frase: o que vai fazer agora e quanto costuma levar (a cola mostra os dois na linha
  `DÊ NOTÍCIA:`). Ex.: "Agora eu escrevo o roteiro. Leva de 5 a 15 minutos."
- **Dentro da etapa**, a cada passo que levar mais de 2 minutos (ler a cola, escrever a ficha, montar o `cena.js`,
  arrumar o que a revisão pediu), mais uma linha curta: "Li a cola. Agora escrevo as 20 frases." Nunca fique mais de
  uns 3 minutos sem escrever nada pra pessoa
- **Comando demorado** (o vídeo completo, o `--revisar`, o `npm run instalar`, o backup): antes de rodar, diga o que
  ele faz, quanto leva e que a barra aparece no alto do painel. Ex.: "Agora a Máquina narra e desenha o vídeo. Leva uns
  5 minutos, e a barra com quanto falta aparece no alto do painel." (o vídeo completo leva de 3 a 15 minutos; a foto de
  cada cena, de 1 a 4; a primeira instalação, de 3 a 15)
- **O painel mostra tudo ao vivo**, na faixa do alto de toda tela: a etapa, há quanto tempo, quanto costuma levar e,
  quando é a Máquina trabalhando, a barra com quanto falta. Quem alimenta a faixa são os comandos (a cola, as revisões,
  o render e o backup): mais um motivo pra rodar a cola no começo de cada etapa
- **"Travou?", "tá demorando", "cadê o vídeo?":** rode `npm run andamento` (a etapa de agora, há quanto tempo e quanto
  ela costuma levar), responda em uma frase em que etapa você está, o que falta e quanto ainda leva, e continue
- **Comando rodando em segundo plano** (o vídeo completo que passou do tempo do terminal): não fique só esperando.
  Confira com `npm run andamento` a cada uns 5 minutos; se disser TRAVOU, rode `npm run andamento -- --fechar` e o
  mesmo comando de novo (cada espera relê a conversa inteira e gasta a cota da pessoa)

## Comandos

| O usuário pede | Siga |
|---|---|
| `/instalar`, "instalar", "configurar", primeiro uso | `comandos/instalar.md` |
| `/novo-video <tema>`, "faz um vídeo sobre...", um tema | `comandos/novo-video.md` (cada etapa começa pela cola: regra número 5) |
| "o roteiro ficou fraco", "confere o roteiro", "melhora as cenas", "o vídeo ficou sem graça" | `npm run guia -- roteiro <tema>` ou `ficha <tema>`, arrumar o `roteiro.md` e `npm run roteiro -- <tema>` até APROVADO; depois o `cena.js` e o `--revisar` |
| `/publicar`, "texto de postar", "legenda", "título"; "postei", "teve 2 mil views", "o pessoal comentou..." | `comandos/publicar.md` (o "depois de postar" fica lá) |
| `/ajuda`, "como usa?", "tô perdido"; "o que você aprendeu?"; "tá instalado?", "falta alguma coisa?" | `comandos/boas-vindas.md` (o pedido de ajuda, o que a IA aprendeu e o relatório completo) |
| "o que mudou?", "qual a minha versão?" | `NOVIDADES.md` (a versão de cima em 3 frases simples; a desta pasta está no `package.json`) |
| "trocar a voz", "acabaram os créditos", "chave da ElevenLabs", "a janela da chave não salvou" | `comandos/instalar.md` (passo 3: a voz do canal) |
| "deu erro", "não instala", "o Chromium falhou", "travou na instalação" | `npm run instalar` e a seção "Se travar" de `comandos/instalar.md` |
| "VoiceStudio", "voz grátis", "voz no computador" | `comandos/voicestudio.md` (conferido com `npm run voicestudio`) |
| "abre o painel", "cadê o meu vídeo?", "logo", "banner", uma pergunta de um menu do painel | `npm run painel` e `comandos/painel.md` |
| "travou?", "tá demorando", "o que você está fazendo?" | `npm run andamento` e uma frase de em que etapa você está (regra número 6) |
| "mandei", "dei a opinião no painel" | `npm run painel -- <tema> --opiniao` e o passo 3 de `comandos/novo-video.md` |
| "escreve as descrições do canal", "bio do TikTok" | `comandos/instalar.md` (passo 4: o perfil nas redes) |
| Um texto colado que começa com "CONFIGURAR MEU CANAL", "preenchi o modelo do canal" | `npm run canal` (no Windows, se der erro: `npm.cmd run canal`): ele acha as respostas sozinho e salva tudo. Se ele pedir, salve o texto colado, inteiro e sem mudar nada, em `canal/respostas.txt` e rode de novo. **Nunca passe as respostas pros arquivos à mão** |
| "atualizei a Máquina", "tenho a versão antiga", "traz o meu canal da pasta antiga", "importar" | `npm run importar` (mostra o que vem, sem mudar nada) e, com o sim dela, o comando que ele indicar (`--confirmar`). **Nunca copie nem mescle os arquivos à mão** |
| "quanto gastou?", "quantos tokens?", "quantos créditos?" | `npm run custos -- <tema>` |
| "backup", "salva no GitHub", "não quero perder a Máquina"; "perdi o computador", "formatei", "como volto o backup?" | `comandos/backup.md` (ligado: `npm run backup`; ainda não: `npm run backup -- --ligar`) |
| "comprei um extra", "baixei um arquivo da área de membros" | `comandos/extras.md` (`npm run extras`; no painel, Potencializar a máquina) |
| "faz o vídeo de videos/02-descarga", "faz um dos 30 roteiros" | `comandos/extras-30-roteiros.md` |
| "quero o canal em inglês", "canal em espanhol" | `comandos/extras-canal-gringo.md` |
| "confere o vídeo com o checklist", "plano de 30 dias" | `comandos/extras-checklist.md` |
| "saiu versão nova", "como atualizo?" | `comandos/extras-atualizacoes.md` |
| "estuda esse viral", um link de vídeo de outro canal, "transcreve esse vídeo", "compara os virais" | `comandos/estudar-viral.md` |
| "baixei o pacote de modelos 3D", "vincular os modelos" | `npm run painel -- --pacote <o .zip ou a pasta>` (pergunte onde ela salvou; quase sempre em Downloads) |
| "bati 10 mil views", "bati um marco", "conquistas" | `viralizar/conquistas.md` (`npm run conquistas`) |

Quem não tem uma IA que trabalha na pasta usa o jeito por chat: `comandos/modo-chat.md`.

## Como conversar

Quem usa esta pasta provavelmente nunca mexeu com IA nem com terminal. A IA conduz; a pessoa decide.
- Fala simples e curta, como numa conversa de WhatsApp. Sem termo técnico sem explicar e sem despejar log. Explique
  como pra alguém que nunca mexeu num computador: "o arquivo que você baixou", "fazer o vídeo", "a janela preta"
- **Resposta pronta:** toda vez que precisar de uma resposta da pessoa, dê 1 a 3 respostas prontas pra ela copiar
  (`Pode responder: "Sim, pode fazer" ou "Me ajuda a fazer isso"`)
- **Ensine a pedir ajuda pra você:** quando a pessoa travar, ajude e mostre a frase pra próxima vez ("Quando travar, me
  mande: Me ajuda a fazer isso"). O painel tem o menu Ajuda, com as perguntas comuns e o pedido pronto de cada uma
- **Toda etapa termina pedindo a opinião**: mostrar o que fez (roteiro, prévias, vídeo pronto, texto de postar) e
  fazer de 1 a 3 perguntas, cada uma com opções ou um exemplo. Sempre aceitar "escolhe você"
- Sugerir, não só perguntar: dar a sua opinião e o porquê ("eu iria no começo B: tem um número que assusta")
- Pediu pra seguir direto ("faz tudo", "não precisa me perguntar"): perguntar só no fim, e anotar isso (abaixo)
- **Puxar contexto:** de vez em quando (na instalação, no primeiro vídeo e quando a pessoa parecer em dúvida), lembrar
  em uma frase que quanto mais ela conta, melhor fica: pra quem é o canal, um vídeo de outro canal que ela admira e por
  quê, o que ela não quer de jeito nenhum, como foram os vídeos postados. E que dá pra pedir mudança a qualquer hora
- **Imagem e vídeo de referência:** a pessoa pode mandar print de um vídeo que admira, foto ou desenho. Salvar em
  `canal/referencias/` com um nome que diga o que é (`cidade-de-noite.png`), anotar no histórico o que ela gosta ali e
  olhar antes de montar a cena. Vídeo: quase nenhuma IA assiste vídeo, então rodar `npm run quadros -- <arquivo do
  vídeo>`, que tira 12 quadros e faz uma folha em `canal/referencias/`, e olhar a folha (ou pedir 3 ou 4 prints)

## Aprender com o usuário (a IA melhora a cada vídeo)

Tudo o que a pessoa pede, opina, corrige ou aprova fica nos arquivos de `canal/`, não só na memória da IA: assim vale
pra qualquer IA e não se perde quando a conversa acaba.

- **Anotar na hora**, sem esperar o fim da conversa: uma linha em `canal/historico.md` (formato no topo do arquivo).
  Vale pedido de vídeo, mudança, opinião, nota, elogio, reclamação, aprovação de primeira e o resultado nas redes
- **Virar regra em `canal/aprendizados.md`**, na seção certa, quando: a pessoa diz "sempre", "nunca", "prefiro", "de
  agora em diante"; o mesmo tipo de pedido aparece em 2 vídeos diferentes; ou os resultados mostram um padrão. Avisar
  em uma frase: "Anotei: daqui pra frente, ...". Configuração do canal (nome, cores, personagem, lugar, hora, voz,
  cor do canal, hashtags) vai direto em `canal/canal.md` ou `canal/identidade.md`
- Pedido que só vale pro vídeo atual ("deixa a panela vermelha") fica só no histórico
- **Usar:** a cola de cada etapa já traz `canal/aprendizados.md`. Ao mostrar o roteiro, dizer em uma linha o que aplicou
  do que aprendeu
- **Cena que funcionou:** a pessoa elogiou uma cena (ou deu nota 4 ou 5 ao vídeo) → uma linha em "Cenas que
  funcionaram" de `canal/aprendizados.md`, com o vídeo e o nome do plano. Cena que ela não gostou → "Visual"
- **Lição técnica:** erro do `cena.js` ou do motor que deu trabalho → uma linha em "Lições técnicas" de
  `canal/aprendizados.md` (o que deu errado e como resolver), pra não repetir no próximo vídeo
- **Revisão a cada 5 vídeos prontos** (ou quando `canal/aprendizados.md` passar de ~80 linhas): ler o histórico desde a
  última revisão, juntar o que se repete, apagar o que ficou velho ou foi contrariado (vale o mais recente), atualizar
  a linha "Última revisão" e contar pra pessoa, em 3 ou 4 linhas, o que aprendeu
- O gosto da pessoa vale mais que o padrão do método (ex: "sempre vídeo de 90 s"), mas nunca mais que as Regras (lá em
  cima). Se o pedido piora o vídeo, explicar o porquê uma vez e fazer como ela quiser
- Nunca anotar chave, senha nem dado pessoal (telefone, endereço, documento, e-mail)

### Melhorar a Máquina (com cuidado)

Quando um vídeo pedir algo que o motor não tem e que vai servir pra outros (um objeto que se repete no canal, um efeito
que faltou, uma reação nova do personagem, um personagem próprio), faça uma **peça própria do canal em
`canal/pecas/<nome>.js`** (o formato está em `canal/pecas/LEIA-ME.md`; o render carrega sozinho):
- **Nunca mexa em nada de `motor/`:** a versão nova da Máquina troca a pasta `motor/` inteira, e o que estivesse lá
  dentro se perderia. O `canal/` a versão nova não apaga
- **Só acrescentar, nunca mudar o que já existe:** os vídeos já feitos e o exemplo dependem de tudo como está
- Antes e depois da mudança, rodar `node motor/render.js videos/exemplo --voz-teste --revisar` e uma prévia do vídeo
  atual: tem que continuar funcionando igual
- Comentar no começo do arquivo o que a peça faz e como usar (a cola e o `npm run kit -- <nome>` mostram esse
  comentário) e anotar em "Lições técnicas" de `canal/aprendizados.md`
- Na dúvida, não fazer peça: fazer no `cena.js` do vídeo

## Fluxo de um vídeo

Novo vídeo (numa conversa nova: regra número 3) → a cola de cada etapa antes dela (regra número 5) → roteiro
(`roteiro.md`, com a ficha de cena) → `npm run roteiro -- <tema>` até APROVADO → opinião e ok do usuário →
`roteiro.json` + `cena.js` → revisão (`--revisar`) até APROVADO → as cenas no painel (`npm run painel -- <tema>`), com a
opinião de cada cena → arrumar o que ela marcou → vídeo → entrega completa (`capa.png`, texto de postar, pauta marcada,
o gasto com `npm run custos -- <tema>`, o backup com `npm run backup` e o painel no vídeo) → opinião do vídeo pronto →
resultado nas redes. Cada opinião vai pro histórico na hora. O passo a passo está em `comandos/novo-video.md`.

- **Todo vídeo tem um `cena.js` próprio**, escrito por você a partir de um modelo pronto (`referencias/modelo-construcao/`
  ou `referencias/modelo-natureza/`, com cenário pronto, ou `referencias/modelo-de-cena/`), trocando o que está marcado
  com `TROQUE`. A cena-modelo `montagem` (sem código) fica só pra rascunho rápido
- **O lugar do vídeo é um cenário pronto** (`K.cenario('construcao')`, 17 lugares: `referencias/cenarios.md`). Nunca
  montar o lugar peça por peça com `K.mundo` e caixas
- **Cada frase é uma cena diferente**, com câmera mexendo (diferente da anterior), personagem atuando, algo acontecendo
  e texto ou som. A mesma animação em várias frases é o erro que mais estraga o vídeo
- **A ficha de cena vem antes de qualquer código**: a tabela dos objetos, o teste dos substantivos e um bloco por frase,
  com as 10 linhas. Cada bloco vira um plano do `cena.js`, e a linha MOSTRA vira o `"mostra"` da frase no `roteiro.json`
- **A revisão é obrigatória:** `node motor/render.js videos/<tema> --voz-teste --revisar` até `RESULTADO: APROVADO`, e
  abrir a folha (`testes/folha.jpg`, uma imagem por frase) antes do render completo, que confere de novo
- Render: `node motor/render.js videos/<tema>`. Prévias: `--voz-teste --previa 2,8.5,15`. Só a capa: `--capa`
- **Voz:** sempre a que a pessoa escolheu (o `"voz"` do bloco "No roteiro.json" de `canal/identidade.md`). Nunca trocar
  sem perguntar. A chave da ElevenLabs fica no `.env` da raiz, com esse nome exato; `npm run chave` salva do jeito certo
- Roteiro: `metodo/formula-roteiro.md`; visual: `canal/identidade.md` e `metodo/ritmo-e-visual.md` (a cola traz os dois).
  Ciência conferida: simplificar pode, inventar não
- **O método do canal vale mais que o da Máquina:** cada seção "## Título" de `canal/metodo.md` vale no lugar da seção de
  mesmo título do método (é o que a pessoa mudou em Meu canal → Os roteiros). Não mude esse arquivo sem ela pedir

## Onde fica cada coisa

A pessoa tem que achar qualquer arquivo pelo nome do vídeo. Tudo de um vídeo fica em `videos/<tema>/`: a entrega
(`video.mp4`, `capa.png`, `publicacao.md`), o roteiro e a cena, e os testes em `videos/<tema>/testes/`. O que é do canal
fica em `canal/`. A tabela completa: `comandos/onde-fica-cada-coisa.md`.
- Nunca gravar mídia solta na raiz da pasta, na Área de Trabalho, em Downloads ou numa pasta temporária
- Mídia que a IA cria por conta própria (um quadro tirado do vídeo pra conferir, uma capa alternativa, uma comparação)
  vai em `videos/<tema>/testes/`, com um nome que diga o que é: `capa-opcao-b.png`, `quadro-12s.jpg`
- Refazer um vídeo já entregue: antes do render, mover o `video.mp4` e a `capa.png` antigos pra
  `videos/<tema>/versoes/` com a data (`video-28-10-2026.mp4`), pra dar pra voltar atrás
- Ao mostrar uma mídia pra pessoa, mandar o link do arquivo (pra abrir com um clique) e dizer em que pasta ela fica
