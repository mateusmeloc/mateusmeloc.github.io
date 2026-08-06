# mateusmeloc.github.io

Site pessoal, publicado pelo GitHub Pages.

## `/listas/`

App **Listas de compras — Espaço Odontológico**, usado pela gerência da clínica
para montar a lista do mês e enviar pronta pelo WhatsApp.

`listas/index.html` é um build final e autossuficiente: React compilado, CSS,
logo e ícones já embutidos no arquivo. Não edite o conteúdo dele à mão — para
atualizar, substitua o arquivo inteiro pela versão nova.

## Por que existe um `api/saude` na raiz

O app chama `fetch("/api/saude")` em caminho absoluto, a partir da raiz do
domínio, para descobrir se a leitura de lista por foto está disponível. Num
servidor Node essa rota é dinâmica; aqui ela é um arquivo estático fixo:

```json
{"ok":true,"ia":false}
```

Com `ia: false` o app esconde o botão de leitura por foto, que é o
comportamento desejado — o recurso exigiria uma chave de API e um servidor.

**Se esse arquivo sumir**, a chamada dá 404, o app conclui que está numa
hospedagem com backend e mostra o botão mesmo assim — que então falha ao ser
usado. Mantenha o arquivo na raiz.

`.nojekyll` desliga o Jekyll, para o arquivo sem extensão ser servido como está.
