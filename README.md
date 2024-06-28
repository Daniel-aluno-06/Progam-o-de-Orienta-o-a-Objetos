# Progamacao-de-Orientacao-a-Objetos
Projeto - Java
package Empregado;

public class empregados {
    private String nome;
    private int idade;
    private String posicao;

    public empregados(String nome, int idade, String posicao) {
        this.nome = nome;
        this.idade = idade;
        this.posicao = posicao;
    }

    public String getNome() {
        return nome;
    }

    public int getIdade() {
        return idade;
    }

    public String getPosicao() {
        return posicao;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + ", Idade: " + idade + ", Posição: " + posicao;
    }
}

package Empregado;
import java.util.ArrayList;
import java.util.List;

public class GerenciamentoEmpregados {
    private List<empregados> empregados;

    public GerenciamentoEmpregados() {
        empregados = new ArrayList<>();
    }

    public void adicionarEmpregado(empregados empregado) {
        empregados.add(empregado);
    }

    public List<empregados> listarEmpregados() {
        return empregados;
    }
}

package Empregado;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        GerenciamentoEmpregados gerenciamento = new GerenciamentoEmpregados();
        Scanner scanner = new Scanner(System.in);
        boolean continuar = true;

        while (continuar) {
            System.out.println("Digite o nome do empregado:");
            String nome = scanner.nextLine();

            System.out.println("Digite a idade do empregado:");
            int idade = scanner.nextInt();
            scanner.nextLine();  // Consumir o newline

            System.out.println("Digite a posição do empregado:");
            String posicao = scanner.nextLine();

            empregados empregado = new empregados(nome, idade, posicao);
            gerenciamento.adicionarEmpregado(empregado);

            System.out.println("Deseja adicionar outro empregado? (s/n):");
            String resposta = scanner.nextLine();
            if (!resposta.equalsIgnoreCase("s")) {
                continuar = false;
            }
        }

        System.out.println("Lista de Empregados:");
        for (empregados emp : gerenciamento.listarEmpregados()) {
            System.out.println(emp);
        }

        scanner.close();
    }
}
