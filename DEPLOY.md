# Jackie Network CRM — deploy (≈15 min, uma vez)

Arquitetura: **GitHub Pages (front) → Apps Script (API) → Google Sheet (banco)**. Tudo teu, grátis, live.

## Passo 1 — Banco (Google Sheet) + API (Apps Script)
1. Cria um **Google Sheet novo** (Drive teu) → nomeia `Jackie Network CRM DB`.
2. Nele: **Extensions → Apps Script**.
3. Apaga o `Code.gs` de exemplo, cola **todo o `Code.gs`** deste pacote.
4. No topo do arquivo, muda `var APP_PASSWORD = 'CHANGE_ME_now';` pra tua senha real.
5. Menu de funções (topo) → seleciona **`setup`** → **Run**. Autoriza (é teu Google).
   - Cria as abas `People` (com os 125 nomes da Jackie) e `Events`.
6. **Deploy → New deployment** → engrenagem → **Web app**:
   - *Execute as*: **Me**
   - *Who has access*: **Anyone**
   - Deploy → autoriza → **copia a URL `…/exec`**.

> Sempre que editar o `Code.gs`: **Deploy → Manage deployments → ✏️ → Version: New version → Deploy** (a URL continua a mesma).

## Passo 2 — Front (GitHub Pages)
1. Abre `index.html`, acha a linha:
   `var API_URL = "PASTE_YOUR_APPS_SCRIPT_EXEC_URL_HERE";`
   e cola a URL `…/exec` do passo 1.
2. Novo repo no **chan-kkim** (ex: `jackie-crm`) → sobe o `index.html`.
3. **Settings → Pages → Branch: main / root → Save.**
4. Abre `https://chan-kkim.github.io/jackie-crm/` → digita a senha → tá vivo.

## Passo 3 — Compartilhar
- Manda a URL + senha pra Jackie e Ahmed. Zero login/conta nova.
- (Opcional) registra no teu **admin index**.

## Como usam (o que a Jackie pediu)
- **Reach out**: muda o **Status** direto na tabela ou arrastando o card no Kanban (owner Chan/Ahmed/Jackie).
- **Add no breakfast/lunch** (do celular): botão **＋ Adicionar** → salva na hora.
- **"guy from the Ireland lunch"**: aba **Events** → cria o evento, lista as pessoas, marca follow-ups.
- **Follow-up**: campo *Follow-up date* + status *Follow-up needed* + filtro por esse status.

## Notas
- Backup: é um Google Sheet normal — histórico de versões do Google + dá pra exportar quando quiser.
- Limite: sem limite prático (Sheet aguenta dezenas de milhares de linhas).
- Segurança: endpoint público protegido por senha; roda em HTTPS. Troca a senha em `APP_PASSWORD` + redeploy quando quiser.
