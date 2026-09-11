# Radar de Decisores — ReachLeads

Página de captura da ReachLeads. A pessoa informa o site da empresa, o segmento que quer
alcançar e os cargos que procura. Em cerca de 40 segundos ela recebe um relatório com:

1. quantos decisores verificados existem no ICP dela
2. a quebra por cargo, porte de empresa e região
3. 12 empresas do perfil, com o nome visível e o contato protegido
4. o primeiro e-mail inteiro, escrito para uma dessas empresas
5. o resto bloqueado, com duas saídas: assinar ou agendar uma demonstração

**Ver funcionando:** abra `index.html` com `?demo=1` no fim do endereço. O formulário já
vem preenchido, e dá para percorrer o fluxo inteiro.

---

## O que é real e o que é demonstração

| | |
|---|---|
| Layout, textos, fluxo e relatório | **Definitivos.** É isso que vai ao ar |
| Números, empresas e o e-mail gerado | **Simulados.** Todas as empresas são fictícias |
| Envio do formulário | **Não envia nada.** A página não tem servidor, chave nem chamada de rede |

O rodapé da própria página avisa o visitante que os dados são de demonstração.

---

## Como colocar no seu GitHub

A página é um único arquivo, `index.html`, sem dependência além das fontes do Google.

1. Clique em **Use this template → Create a new repository**. Você fica com uma cópia na sua conta.
2. Na sua cópia, troque o conteúdo do arquivo `CNAME` pelo seu domínio — por exemplo,
   `radar.reachleads.com.br`. Se não for usar domínio próprio, **apague** o `CNAME`.
3. Em **Settings → Pages**, escolha a branch `main` e a pasta `/ (root)`.
4. No seu provedor de DNS, crie um registro `CNAME` apontando o subdomínio para
   `<seu-usuario>.github.io`. Depois marque **Enforce HTTPS** no Pages.

Para atualizar a página, é só substituir o `index.html` e dar push na `main`.

---

## O que falta para ela capturar lead de verdade

Hoje ela demonstra. Para virar captura, faltam três peças:

1. **Envio do lead.** Ligar o formulário a um webhook ou ao CRM, com `fetch` usando
   `keepalive: true`, para o lead não se perder quando a página redireciona.
2. **Rastreamento.** GTM no topo do `<head>` e o evento `lead_gerado` disparado no envio
   bem-sucedido do formulário — nunca no clique do botão. É esse evento que se marca como
   conversão, não a visita à página de obrigado.
3. **Dados reais.** Trocar os números e as empresas simuladas por uma consulta ao catálogo
   da plataforma.

**Nomes de empresa nesta página são sempre inventados.** Nunca usar o catálogo real, um
lead que apareceu numa demonstração ou um cliente, porque a página é pública.
