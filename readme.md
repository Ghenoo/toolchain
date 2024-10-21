## Organizando versões entre diversos projetos com a Toolchain em GoLang

 A partir da versão "Go 1.21" junto com algumas adições ao pacote slices, surgiu essa nova palavra no go.mod, a palavra toolchain. A toolchain permite que você especifique a versão exata do GO para seu projeto, sem precisar instalar gerenciadores de versão.

- O comando GO pode usar sua cadeia de ferramentas Go empacotada, bem como outras versões que ele encontra no PATH local ou baixa conforme necessário.

```bash
  module example.com/toolchain-demo
  
  go 1.21
  toolchain go1.20.5
 ```

 **Exemplo:** 
    - Vamos supor que você tem 3 projetos no seu pc, o 1° em GO 1.21, 2° em GO 1.22 e o 3° em GO 1.23 mas seu PC está em GO 1.18, se você for buildar e rodar o projeto 1.21, você vai precisar baixar o GO 1.21, apagar a versão antiga no seu path e mudar o ponteiro do seu ENV para apontar para a nova versão do GO, quando você for rodar o 2° projeto, irá precisar fazer tudo denovo, tendo a versão mais atualizada **1.23** todos abaixo dela vão funcionar e assim por diante, mas o problema é o verso, quando você está na 1.23 e precisa executar um projeto na 1.16, você necessita baixar a versão antiga para rodar.


 ** Solução:**  
    Com a Toolchain você escreve com a versão do GO que está na sua máquina mas a versão GO que estiver definida no projeto na Toolchain é a que vai ser buildada, ele vai baixar e rodar o projeto naquela versão.

- Leia mais sobre a documentação da [Toolchain](https://go.dev/doc/toolchain)
