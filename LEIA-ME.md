# Livro de Contas — como publicar e instalar

A app é só um conjunto de ficheiros estáticos. Não tem servidor nem base de dados: os teus movimentos ficam cifrados (AES-256, chave derivada da tua password com PBKDF2-SHA256, 600 000 iterações) no armazenamento do próprio dispositivo. O site publicado contém apenas a app vazia.

## 1. Publicar no GitHub Pages (grátis, uma vez)

1. Cria uma conta em https://github.com (grátis).
2. Carrega em **New repository**.
   - Nome: algo difícil de adivinhar, por exemplo `cx-7f3k9q`. Esse nome faz parte do endereço.
   - Visibilidade: **Public** (o GitHub Pages grátis exige repositório público; só o código fica visível, nunca os teus dados).
   - Cria o repositório.
3. Na página do repositório, carrega em **uploading an existing file**.
4. Descompacta o zip e arrasta para lá **o conteúdo** da pasta `contas` (o `index.html`, `sw.js`, `manifest.webmanifest`, e as pastas `icons` e `vendor`). Carrega em **Commit changes**.
5. Vai a **Settings → Pages**. Em *Build and deployment*, escolhe **Deploy from a branch**, branch **main**, pasta **/ (root)**, e carrega em **Save**.
6. Ao fim de 1–2 minutos, a página mostra o endereço: `https://O-TEU-USERNAME.github.io/cx-7f3k9q/`.

## 2. Instalar no iPhone

1. Abre o endereço no **Safari** (tem de ser o Safari).
2. Toca em **Partilhar** → **Adicionar ao ecrã principal** → **Adicionar**.
3. Abre a app pelo ícone novo e **cria a conta lá dentro**.

Importante: a app instalada e o Safari guardam dados em sítios separados. Usa sempre a app pelo ícone; se criares conta no Safari, essa conta não aparece na app.

## 3. Instalar no Mac

1. Abre o endereço no **Safari** (macOS Sonoma ou mais recente).
2. Menu **Ficheiro → Adicionar à Dock**.
3. Abre a app pela Dock e cria a conta.

Na app da Dock, clicar nas caixas de importação não abre a janela para escolher ficheiros (limitação do Safari nestas apps). Arrasta o ficheiro do Finder para a caixa, ou copia-o no Finder (⌘C) e cola-o na app (⌘V).

## 4. Uso mensal

- **Crédito Agrícola:** importa na caixa "CA" o PDF do extrato mensal (Extracto Integrado) que recebes do banco. A app confere os movimentos com o saldo inicial e final do extrato; se não baterem certo, não importa nada. CSV ou Excel do CA Online continuam a funcionar.
- **Coverflex:** pede o CSV ao assistente da Coverflex com o texto da secção "Como exportar os extratos" (escolhe lá o mês; por omissão é o mês anterior) e importa-o na caixa "CF". Pede um mês completo de cada vez, como o extrato do CA. O ficheiro não traz o valor de cada movimento, só o saldo depois dele, por isso a app calcula o valor pela diferença de saldos: importa os meses por ordem, porque o primeiro movimento de um mês só tem valor se o mês anterior já estiver importado.
- Importar o mesmo período duas vezes não duplica movimentos.
- **Movimentos à mão:** na tabela de movimentos, **Adicionar movimento** (por exemplo, despesas pagas em dinheiro).
- **Comentários:** o ✎ de cada linha escreve ou edita um comentário, que aparece por baixo da descrição. A pesquisa também procura nos comentários, e voltar a importar um ficheiro não os apaga.
- **Categorias:** na secção **Categorias** (em baixo) podes criar categorias novas e mudar o nome de qualquer uma; as regras e as categorias escolhidas à mão acompanham o nome novo. Só as categorias que criaste podem ser apagadas.
- **Apagar:** o ✕ de cada linha apaga esse movimento. **Importações** (em baixo) lista cada importação com um botão para a apagar. **Apagar estes movimentos** apaga tudo o que a tabela está a mostrar com os filtros atuais; com "Todos os meses" e sem filtros, apaga todos os movimentos e mantém a conta e as regras.

## 5. Passar dados entre o Mac e o iPhone

1. No Mac: secção **Cópia de segurança** → **Exportar cópia**. Sai um ficheiro `.json` cifrado com a tua password.
2. Envia-o para o iPhone por AirDrop ou iCloud Drive.
3. No iPhone: **Restaurar cópia…**, escolhe o ficheiro e escreve a password. Os movimentos juntam-se sem duplicar.

Guarda também uma cópia de vez em quando no iCloud Drive: se apagares a app ou o histórico do Safari, os dados desse dispositivo desaparecem.

## Segurança

- A password não é guardada em lado nenhum. Se a esqueceres, os dados não podem ser recuperados (só restaurando uma cópia cuja password te lembres).
- Depois de 5 tentativas erradas, a app obriga a esperar antes de tentar de novo.
- Bloqueia sozinha após 10 minutos sem uso ou 5 minutos em segundo plano.
- A página tem `noindex`, por isso não aparece no Google.

## Atualizar a app no futuro

Substitui os ficheiros no repositório e, em `sw.js`, muda `contas-v1` para `contas-v2` (e assim sucessivamente). Na próxima abertura com internet, a app atualiza-se. Os teus dados não são afetados.
