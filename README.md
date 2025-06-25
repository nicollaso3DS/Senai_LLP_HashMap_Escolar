# Senai_LLP_HashMap_Escolar

import java.util.Scanner;
import java.util.HashMap;
import java.util.ArrayList;

public class GestaoEscolar {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        HashMap<String, ArrayList<Double>> boletim = new HashMap<>();

        System.out.print("Informe a quantidade de alunos: ");
        int quantidadeAlunos = Integer.parseInt(scanner.nextLine());

        System.out.print("Informe a quantidade de notas por aluno: ");
        int quantidadeNotas = Integer.parseInt(scanner.nextLine());

        // Entrada de dados dos alunos
        for (int i = 0; i < quantidadeAlunos; i++) {
            System.out.print("\nInforme o nome do aluno #" + (i + 1) + ": ");
            String nome = scanner.nextLine();

            ArrayList<Double> notas = new ArrayList<>();
            for (int j = 0; j < quantidadeNotas; j++) {
                System.out.print("Informe a nota " + (j + 1) + " de " + nome + ": ");
                double nota = Double.parseDouble(scanner.nextLine());
                notas.add(nota);
            }

            boletim.put(nome, notas);
        }

        // Processamento e saída
        System.out.println("\n--- RESULTADOS FINAIS ---");
        for (String aluno : boletim.keySet()) {
            ArrayList<Double> notas = boletim.get(aluno);
            double soma = 0;
            for (double nota : notas) {
                soma += nota;
            }
            double media = soma / notas.size();
            String resultado = media >= 6.0 ? "Aprovado" : "Reprovado";

            System.out.printf("%s [%.2f] [%s]%n", aluno, media, resultado);
        }
    }
}
