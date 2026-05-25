# smartmarket-pdv-java
import java.util.ArrayList;
import java.util.Scanner;

class Produto {
    String nome;
    double preco;
    int quantidade;

    Produto(String nome, double preco, int quantidade) {
        this.nome = nome;
        this.preco = preco;
        this.quantidade = quantidade;
    }

    double calcularTotal() {
        return preco * quantidade;
    }
}

public class SmartMarketPDV {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        ArrayList<Produto> carrinho = new ArrayList<>();

        System.out.println("======================================");
        System.out.println("      SMART MARKET PDV SYSTEM");
        System.out.println("======================================");

        String continuar;

        do {

            System.out.print("\nNome do produto: ");
            String nome = scanner.nextLine();

            System.out.print("Preço do produto: R$ ");
            double preco = scanner.nextDouble();

            System.out.print("Quantidade: ");
            int quantidade = scanner.nextInt();
            scanner.nextLine();

            Produto produto = new Produto(nome, preco, quantidade);
            carrinho.add(produto);

            System.out.print("\nDeseja adicionar outro produto? (s/n): ");
            continuar = scanner.nextLine();

        } while (continuar.equalsIgnoreCase("s"));

        double subtotal = 0;

        System.out.println("\n======================================");
        System.out.println("              RECIBO");
        System.out.println("======================================");

        for (Produto produto : carrinho) {

            double totalProduto = produto.calcularTotal();

            System.out.println("Produto: " + produto.nome);
            System.out.println("Preço: R$ " + produto.preco);
            System.out.println("Quantidade: " + produto.quantidade);
            System.out.println("Total: R$ " + totalProduto);
            System.out.println("--------------------------------------");

            subtotal += totalProduto;
        }

        double desconto = 0;

        if (subtotal >= 200) {
            desconto = subtotal * 0.10;
        }

        double totalFinal = subtotal - desconto;

        System.out.println("Subtotal: R$ " + subtotal);
        System.out.println("Desconto: R$ " + desconto);
        System.out.println("TOTAL FINAL: R$ " + totalFinal);

        System.out.println("======================================");
        System.out.println(" Obrigado por utilizar o SmartMarket!");
        System.out.println("======================================");

        scanner.close();
    }
}
