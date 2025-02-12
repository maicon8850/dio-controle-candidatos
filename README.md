# 📌 Processo Seletivo - Sistema de Gestão de Candidatos

## 📋 Sobre o Projeto
Este projeto foi desenvolvido para **estudos** em **Java**, aplicando conceitos fundamentais de:
- 🔹 **Controle de fluxo** (`if-else`, `switch-case`)
- 🔹 **Estruturas de repetição** (`for`, `while`, `do-while`)
- 🔹 **Manipulação de arrays**
- 🔹 **Geração de valores aleatórios** (`Random`)
- 🔹 **Simulação de um processo seletivo realista**

O sistema **seleciona automaticamente candidatos** com base no **salário pretendido** e realiza **até 3 tentativas de contato** com os aprovados.

---

## ⚙️ Como funciona o sistema?
O projeto segue um fluxo lógico baseado no **processo seletivo de uma empresa**:

### 1️⃣ **Listagem dos candidatos**
- O sistema possui uma lista de **10 candidatos** interessados na vaga.

### 2️⃣ **Seleção de candidatos com base no salário pretendido**
- Cada candidato solicita um **salário aleatório** entre **R$ 1.800 e R$ 2.600**.
- Se o salário pretendido for **menor ou igual ao salário base (R$ 2.000)**, ele é **selecionado**.
- Apenas **5 candidatos são aprovados** no processo seletivo.

### 3️⃣ **Tentativa de contato com os candidatos selecionados**
- O sistema tenta ligar para cada candidato **até 3 vezes**.
- Se o candidato atender, exibe:  
  ✅ **"CONSEGUIMOS CONTATO COM [CANDIDATO] APÓS [TENTATIVA] TENTATIVA(S)"**
- Se não atender após 3 tentativas, exibe:  
  ❌ **"NÃO CONSEGUIMOS CONTATO COM O [CANDIDATO]"**

---

## 📌 Exemplo de Saída no Console
```bash
Processo seletivo
O candidato FELIPE solicitou este valor de salário: 2239.17
O candidato JULIA solicitou este valor de salário: 1824.07
O candidato JULIA foi selecionado para a vaga.
O candidato PAULO solicitou este valor de salário: 2189.13
O candidato AUGUSTO solicitou este valor de salário: 1976.71
O candidato AUGUSTO foi selecionado para a vaga.

📞 Tentando contato com os candidatos selecionados:
📞 Tentativa 1 com JULIA sem sucesso...
✅ CONSEGUIMOS CONTATO COM JULIA APÓS 2 TENTATIVA(S)
📞 Tentativa 1 com AUGUSTO sem sucesso...
📞 Tentativa 2 com AUGUSTO sem sucesso...
📞 Tentativa 3 com AUGUSTO sem sucesso...
❌ NÃO CONSEGUIMOS CONTATO COM O AUGUSTO
```

---

## 📂 Estrutura do Projeto
```
📦 controle-candidatos
 ┣ 📂 src
 ┃ ┗ 📂 main
 ┃ ┃ ┗ 📂 java
 ┃ ┃ ┃ ┗ 📂 org.example
 ┃ ┃ ┃ ┃ ┗ 📜 ProcessoSeletivo.java
 ┣ 📜 README.md
 ┣ 📜 pom.xml 
```

---

## 📜 Código-Fonte
Aqui está o código principal do projeto:
```java
package org.example;

import java.util.Random;

public class ProcessoSeletivo {
    public static void main(String[] args) {
        System.out.println("Processo seletivo");
        selecaoCandidatos();
    }

    static void selecaoCandidatos() {
        String[] candidatos = {"FELIPE", "MARCIA", "JULIA", "PAULO", "AUGUSTO", "MONICA", "FABRICIO", "MIRELA", "DANIELA", "MAICON"};
        String[] selecionados = new String[5];
        int candidatosSelecionados = 0;
        int candidatoAtual = 0;
        double salarioBase = 2000.0;

        while (candidatosSelecionados < 5 && candidatoAtual < candidatos.length) {
            String candidato = candidatos[candidatoAtual];
            double salarioPretendido = valorPretendido();
            System.out.println("O candidato " + candidato + " solicitou este valor de salário: " + salarioPretendido);

            if (salarioBase >= salarioPretendido) {
                System.out.println("O candidato " + candidato + " foi selecionado para a vaga.");
                selecionados[candidatosSelecionados] = candidato;
                candidatosSelecionados++;
            }
            candidatoAtual++;
        }

        System.out.println("\n📞 Tentando contato com os candidatos selecionados:");
        for (int i = 0; i < candidatosSelecionados; i++) {
            tentarContato(selecionados[i]);
        }
    }

    static double valorPretendido() {
        Random random = new Random();
        return 1800 + random.nextDouble() * 800;
    }

    static void tentarContato(String candidato) {
        Random random = new Random();
        int tentativas = 0;
        boolean atendeu = false;

        while (tentativas < 3 && !atendeu) {
            tentativas++;
            atendeu = random.nextBoolean();

            if (atendeu) {
                System.out.println("✅ CONSEGUIMOS CONTATO COM " + candidato + " APÓS " + tentativas + " TENTATIVA(S)");
            } else {
                System.out.println("📞 Tentativa " + tentativas + " com " + candidato + " sem sucesso...");
            }
        }

        if (!atendeu) {
            System.out.println("❌ NÃO CONSEGUIMOS CONTATO COM O " + candidato);
        }
    }
}
```

---

## 📌 O que foi aprendido com este projeto?
✅ **Uso de loops (`for`, `while`)** para iterar sobre candidatos.  
✅ **Uso de `if-else`** para tomar decisões no processo seletivo.  
✅ **Manipulação de arrays** para armazenar candidatos selecionados.  
✅ **Uso da classe `Random`** para gerar valores aleatórios.  
✅ **Simulação de um fluxo realista de seleção de candidatos.**  

---

## 🚀 Conclusão
Este projeto foi criado **para estudos**, explorando **lógica de programação e estruturas de controle de fluxo em Java**. Ele simula um **processo seletivo automatizado**, desde a **seleção de candidatos** até a **tentativa de contato**.

📌 **Aprendi muito desenvolvendo este projeto e continuo evoluindo!** 🚀

