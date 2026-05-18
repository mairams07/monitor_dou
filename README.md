# Monitor DOU — Contratação ENCCEJA

Monitora diariamente o Diário Oficial da União em busca da publicação oficial
da empresa contratada para execução do ENCCEJA (INEP/MEC).

## Como configurar

### 1. Criar o repositório no GitHub

Crie um repositório (público ou privado) e suba este conteúdo.

### 2. Configurar os Secrets do GitHub

Vá em **Settings → Secrets and variables → Actions → New repository secret**
e adicione os três secrets abaixo:

| Secret | Valor |
|---|---|
| `GMAIL_USERNAME` | Seu endereço Gmail (ex: `seuemail@gmail.com`) |
| `GMAIL_APP_PASSWORD` | Senha de App do Gmail (veja instruções abaixo) |
| `NOTIFY_EMAIL` | E-mail que receberá os alertas |

#### Como gerar a Senha de App do Gmail

1. Acesse [myaccount.google.com/security](https://myaccount.google.com/security)
2. Certifique-se de ter **verificação em 2 etapas** ativada
3. Pesquise "Senhas de app" → Criar → nomeie como "Monitor DOU"
4. Copie a senha gerada (16 caracteres) e use como `GMAIL_APP_PASSWORD`

### 3. Ativar o workflow

Após subir os arquivos, vá em **Actions** no GitHub e confirme a ativação
dos workflows (se solicitado).

### 4. Testar manualmente

Em **Actions → Monitor DOU - Contratação ENCCEJA → Run workflow**,
clique em **Run workflow** para disparar uma verificação imediata.

## O que é monitorado

- **Horário:** Todo dia às 9h (horário de Brasília)
- **Fonte 1:** Página de busca do DOU filtrada por INEP/MEC + "encceja"
- **Fonte 2:** RSS do DOU — Seção 3 (contratos e editais)
- **Fonte 3:** RSS do DOU — Seção 1 (atos normativos)
- **Fonte 4:** RSS do DOU — Edição Extra

**Palavras-chave de contratação buscadas:**
`contrat`, `licitaç`, `homologaç`, `adjudicaç`, `pregão`,
`dispensa`, `empresa`, `executor`, `fornecedor`

## Alerta

O e-mail só é enviado quando há publicação **com "encceja" E alguma
palavra-chave de contratação** ao mesmo tempo. Sem novidades = sem e-mail.
