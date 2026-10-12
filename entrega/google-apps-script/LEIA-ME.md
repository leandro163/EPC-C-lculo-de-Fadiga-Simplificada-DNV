# EPC — Cargas e Relatório · versão de teste

O arquivo `Codigo.gs` contém o aplicativo completo para o Google Apps Script.
Não precisa de outros arquivos nem de Google Sites. Esta edição começa vazia,
sem os dados reais do exemplo do cliente. Implementa somente cargas e relatório.

## Corrigir a implantação existente

1. Abra `Codigo.gs` neste repositório e use **Copy raw file** (copiar o arquivo).
   Se esse botão não aparecer, clique em **Raw**, selecione todo o texto e copie.
   Não copie o código compacto da mensagem anterior: aquela cópia ficou incompleta.
2. Abra seu projeto no editor https://script.google.com.
3. Substitua **todo** o conteúdo do arquivo `Código.gs` pelo conteúdo copiado.
   Não acrescente ao fim do código antigo. Salve.
4. Abra **Implantar → Gerenciar implantações**. Selecione a implantação que
   forneceu seu endereço `/exec` e clique no lápis para editar.
5. Em **Versão**, selecione **Nova versão** e clique em **Implantar**.
6. Reabra o mesmo endereço `/exec`. A URL permanece a mesma quando você atualiza
   essa implantação. Apenas salvar o código no editor não atualiza esse endereço.

O erro “Não foi possível descompactar o arquivo gzip” ocorre com uma cópia
incompleta ou danificada do conteúdo compactado. Este arquivo completo foi
descompactado e comparado ao HTML gerado em uma verificação local. O funcionamento
dentro da conta Google ainda depende da conferência abaixo.

## Conferência rápida

1. Crie um conjunto chamado `TESTE - EXCLUIR`.
2. Cole as duas colunas abaixo nos campos de cargas, com formato decimal vírgula:

```text
Primary	Secondary
100,0	80,0
120,0	60,0
```

3. Calcule: o máximo deve ser **120**, o mínimo **60** e o range **60 kN**.
4. Abra o relatório: ele deve manter o nome `TESTE - EXCLUIR` e esses valores.
5. Baixe o CSV. Salve também um JSON, reabra-o e confira os resultados.
6. Apague o conjunto de teste antes de iniciar um trabalho real.

Os extremos são globais entre Primary e Secondary, e range = máximo − mínimo,
como na planilha de origem. Este pacote não altera a metodologia de cálculo.

## Liberar para a equipe

1. Em **Implantar → Gerenciar implantações → Editar**, mantenha a execução
   como o proprietário do aplicativo.
2. Em **Quem tem acesso**, escolha a opção restrita aos usuários da organização
   EPC. O nome exato depende da conta e das políticas do Google Workspace.
3. Confirme a implantação. Envie à equipe o endereço do aplicativo terminado
   em `/exec`; não é necessário compartilhar a edição do projeto Apps Script.
4. Peça a um colega, usando a própria conta EPC, que abra o endereço e faça
   a conferência rápida acima antes de adotar a versão no trabalho.

Se a opção de acesso da organização não estiver disponível, o administrador
do Google Workspace precisa conferir a política do domínio.

Cada usuário trabalha com os dados do próprio navegador. Esta versão não
sincroniza projetos nem grava no Google Drive. Para trocar ou guardar um projeto,
use **Salvar JSON**. O CSV é a saída de tabela para o relatório.

## Atualizações futuras

Substitua o código, salve e edite **a mesma implantação**, escolhendo **Nova versão**.
Assim, a equipe continua usando o mesmo link.

## Integridade do pacote

- `Codigo.gs`: 18.168 bytes, 151 linhas, 138 trechos de conteúdo compactado.
- SHA-256 do HTML após descompactar:
  `ff9cbe21b9135f358f8373128d3eb9790a6e8aab78340069f4e47da47626d020`.
- O próprio código confere esse hash antes de servir o aplicativo.
- Verificação local: descompactação e igualdade exata com o HTML gerado.
- Validação no Google: pendente até reabrir a implantação corrigida.
