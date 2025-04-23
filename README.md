# Checkpoint-3

S - Single Responsibility Principle (SRP)
Uma classe deve ter apenas um motivo para mudar.

Violação: 
A classe GerenciadorBiblioteca faz tudo:
- Cadastra livros
- Cadastra usuários
- Faz empréstimos
- Calcula multas
- Evnia e-mails e SMS

Por que isso é ruim:
Se você quiser mudar a forma de notificação, vai ter que alterar essa classe. Se quiser mudar o cálculo de multas, também vai mexer nela. Isso quebra o isolamento e dificulta a manutenção.

O - Open/Closed Principle (OCP)
Software deve estar aberto para extensão e fechado para modificação.

Violação:
- Para adicionar um novo tipo de notificação (como WhatsApp), é necessário modificiar o método RealizarEmprestimo e adicionar o código do novo canal ali.

Por que isso é ruim:
- Cada vez que surge uma necessidade nova, você muda código existente, o que pode quebrar funcionalidade que já funcionam.

L - Liskov Substitution Principle (LSP)
Subtipos devem poder ser usados no lugar de seus tipos base sem causar erros.

Situação neutra:
O código original não define heranças ou subclasses, então não viola LSP diretamente. Mas, ao introduzir interfaces e polimorfismo na refatoração, você cria base para aplicar o LSP corretamente.

I - Interface Segregation Principle (ISP)
Os clientes não devem ser forçados a depender de interfaces que não usam.

Violação implícita:
- O código não tem interfaces. Se criássemos uma interface INotificador, um SMS simples teria que implementar assunto e mensagem, mesmo que não use "assunto".

Por que isso é ruim:
- Componentes acabam dependendo de métodos que não fazem sentido para eles.

D - Dependency Inversion Principle (DIP)
Dependa de abstrações, não de implementações concretas.

Violação:
- A classe GerenciadorBiblioteca cria e usa diretamente os métodos de notificação (EnviarEmail, EnviarSMS), que são implementações concretas.

Por que isso é ruim:
- Isso torna o sistema difícil de testar e difícil de estender. Com abstrações (interfaces), é facil trocar a implementação sem tocar na lógica principal.

Clean Code (Boas Práticas)
Além de SOLID, há outras boas práticas quebradas:

Métodos longos com múltiplas responsabilidades

Nomes como l, u, e em vez de nomes descritivos (livro, usuario, emprestimo)

Repetição de código (envio de mensagens)

Falta de encapsulamento (listas manipuladas diretamente)

Erros codificados como return -1, o que é pouco expressivo
