# Jogo-Zombue-Dice
Código do funcionamento do jogo
import java.util.Random;
import java.util.Scanner;

public class JogoZumbi {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        //parte 1 - apresentação
        Boolean ciclo1  = true;
        System.out.println("Bem vindo ao Zombie Dice!!!!!!!!");
        System.out.println("Depois de ler as regras, digite a quantidades de jogadores");
        int jogadores;
        jogadores = sc.nextInt();
        if (jogadores < 2) {
            System.out.println("Numero de jogadores invalido, leia novamente as regras");
            System.exit(1);
        }
        System.out.println("Agora vamos ver quem vai começar, teve algum vencedor a ultima partida ?");
        String vencedor;
        vencedor = sc.next();
        if (vencedor.matches("sim")) {
            System.out.println("Então o vencedor deve começar");
        } else {
            System.out.println("Então a pessoa que falar cérebroooooo!!!! da maneira mais zumbi começa");
        }
        System.out.println("Boa partida e boa sorte com os cerebroooossss!!!");

        // parte 2 - jogo em andamento
        int quantdados = 0;
        // ciclo1 é o jogo em andamento
        while (ciclo1) {
            int cerebros = 0;
            int espingarda = 0;
            Boolean ciclo2 = true;
            // ciclo2 são os turnos
            while (ciclo2) {
                Random random = new Random();
                char vermelhoChar = 'a';
                char verdeChar = 'a';
                char amareloChar = 'a';
                // o dado do jogo
                char[] letrasdodado = new char[3];
                int stop = 1;
                while (stop <= 3) {
                    String setOfCharacters = "abbbbbbccc"; // seleção da cor do dado/dificuldade
                    int randomInt = random.nextInt(setOfCharacters.length());
                    char randomChar = setOfCharacters.charAt(randomInt);
                    if (stop == 1) {
                        letrasdodado[0] = randomChar;
                    }
                    if (stop == 2) {
                        letrasdodado[1] = randomChar;
                    }
                    if (stop == 3) {
                        letrasdodado[2] = randomChar;
                    }
                    stop = +1;
                }
                //Sortei do dado
                for (int i = 0; i < letrasdodado.length; i++) {
                    if (i == 'a') {
                        String dadover = "eeeppc";
                        int vermelhoInt = random.nextInt(dadover.length());
                        vermelhoChar = dadover.charAt(vermelhoInt);
                        System.out.println("Você tirou os dados:" + "VERMELHO" + vermelhoChar);

                    }
                    if (i == 'b') {
                        String dadoverde = "cccppe";
                        int verdeInt = random.nextInt(dadoverde.length());
                        verdeChar = dadoverde.charAt(verdeInt);
                        System.out.println("Você tirou os dados:" + "VERDE" + verdeChar);

                    } else {
                        String dadoama = "eeppcc";
                        int amareloInt = random.nextInt(dadoama.length());
                        amareloChar = dadoama.charAt(amareloInt);
                        System.out.println("Você tirou os dados:" + "AMARELO" + amareloChar);
                    }
                }
                //Condição1
                if (vermelhoChar == 'e' && verdeChar == 'e' && amareloChar == 'e') {
                    System.out.println("3 espirgardas, o turnou acabou.");
                    ciclo2 = false;

                }
                //Soma dos pontos
                if (vermelhoChar == 'c') {
                    cerebros = +1;
                }
                if (verdeChar == 'c') {
                    cerebros = +1;
                }
                if (amareloChar == 'c') {
                    cerebros = +1;
                }
                //Soma das espingardas
                if (vermelhoChar == 'e') {
                    espingarda = +1;
                }
                if (verdeChar == 'e') {
                    espingarda = +1;
                }
                if (amareloChar == 'e') {
                    espingarda = +1;
                }
                //Condição2
                if (espingarda <= 3){
                    System.out.println("3 espirgardas, o turnou acabou.");
                    System.out.println("A sua pontuação foi de:" + cerebros);
                    cerebros = 0;
                    ciclo2 = false;
                }
                //Controle da quantidade de dados no jogo
                String aux1;
                boolean stop1 = true;
                boolean stop4 = true;
                int dados2;
                int dados = 10;
                int soma3 = 0;
                while (stop1) {
                    if (vermelhoChar == 'p') {
                        soma3 = +1;
                    }
                    if (verdeChar == 'p') {
                        soma3 = +1;
                    }
                    if (amareloChar == 'p') {
                        soma3 = +1;
                    }


                    while (stop4) {
                        if (soma3 == 1) {
                            dados2 = dados - 2;
                        } else if (soma3 == 2) {
                            dados2 = dados - 1;
                        } else {
                            dados2 = dados - 3;
                        }
                        if (dados == 0) {
                            System.out.println("Dados insuficientes para continuar");
                            System.out.println("Sua pontuação foi de:" + cerebros);
                            System.out.println("Digite P para o próximo jogador");
                            dados = 10;
                            ciclo2 = false;
                        }
                    }
                }
                System.out.println("oi");
                //Final do jogo2
                if (cerebros == 13){
                    System.out.println("Meus parabens, você venceu o jogo!!!!1");
                    System.out.println("Até a próxima e obrigafo por jogar");
                    ciclo1 = false;
                }


                System.out.println("Agora você pode parar por aqui ou continuar");
                System.out.println("Se deseja continaar digite SIM");
                System.out.println("Caso deseje parar digite NAO");
                String b;
                b = sc.next();
                if (b.matches("sim")) {
                    System.out.println("Muito bem, vamos lá então:");
                    ciclo2 = false;
                }
                String c;
                c = sc.next();
                if (c.matches("nao")) {
                    System.out.println("Que pena que decidiu parar, muito obrigo pela participação e até a proxima zumbi!!!!");
                    System.out.println("Você adquiriu" + cerebros + " de pontos, muito bemm!!!");
                    ciclo1 = false;
                }
            }
        }
    }
}

