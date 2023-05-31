import java.util.ArrayList;
import java.util.Scanner;

class Informacao {
    private String nome;
    private String email;

    public Informacao(String nome, String email) {
        this.nome = nome;
        this.email = email;
    }

    public String getNome() {
        return nome;
    }

    public String getEmail() {
        return email;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}

public class CadastroSoftware {
    private ArrayList<Informacao> informacoes;
    private Scanner scanner;

    public CadastroSoftware() {
        informacoes = new ArrayList<>();
        scanner = new Scanner(System.in);
    }

    public void cadastrarInformacao() {
        System.out.println("Cadastro de Informação");
        System.out.print("Nome: ");
        String nome = scanner.nextLine();
        System.out.print("Email: ");
        String email = scanner.nextLine();

        Informacao informacao = new Informacao(nome, email);
        informacoes.add(informacao);
        System.out.println("Informação cadastrada com sucesso!");
    }

    public void listarInformacoes() {
        System.out.println("Lista de Informações");
        for (Informacao informacao : informacoes) {
            System.out.println("Nome: " + informacao.getNome());
            System.out.println("Email: " + informacao.getEmail());
            System.out.println("-----------------------");
        }
    }

    public void editarInformacao() {
        System.out.println("Edição de Informação");
        System.out.print("Digite o nome da informação que deseja editar: ");
        String nomeBusca = scanner.nextLine();

        for (Informacao informacao : informacoes) {
            if (informacao.getNome().equals(nomeBusca)) {
                System.out.print("Novo nome: ");
                String novoNome = scanner.nextLine();
                System.out.print("Novo email: ");
                String novoEmail = scanner.nextLine();

                informacao.setNome(novoNome);
                informacao.setEmail(novoEmail);
                System.out.println("Informação editada com sucesso!");
                return;
            }
        }

        System.out.println("Informação não encontrada!");
    }

    public void excluirInformacao() {
        System.out.println("Exclusão de Informação");
        System.out.print("Digite o nome da informação que deseja excluir: ");
        String nomeBusca = scanner.nextLine();

        for (Informacao informacao : informacoes) {
            if (informacao.getNome().equals(nomeBusca)) {
                informacoes.remove(informacao);
                System.out.println("Informação excluída com sucesso!");
                return;
            }
        }

        System.out.println("Informação não encontrada!");
    }

    public static void main(String[] args) {
        CadastroSoftware cadastro = new CadastroSoftware();
        Scanner scanner = new Scanner(System.in);
        int opcao = 0;

        while (opcao != 5) {
            System.out.println("----- Cadastro de Informações -----");
            System.out.println("1. Cadastrar Informação");
            System.out.println("2. Listar Informações");
            System.out.println("3. Editar Informação");
            System.out.println("4. Excluir Informação");
            System.out.println("5. Sair");
            System.out.print("Escolha uma opção: ");
            opcao = scanner.nextInt();
            scanner.nextLine();

            switch (opcao) {
                case 1:
                    cadastro.cadastrarInformacao();
                    break;
                case 2:
                    cadastro.listarInformacoes();
                    break;
                case 3:
                    cadastro.editarInformacao();
                    break;
                case 4:
                    cadastro.excluirInformacao();
                    break;
                case 5:
                    System.out.println("Encerrando o programa...");
                    break;
                default:
                    System.out.println("Opção inválida!");
            }

            System.out.println();
        }

        scanner.close();
    }
