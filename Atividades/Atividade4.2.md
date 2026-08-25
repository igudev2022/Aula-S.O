# Sistemas Operacionais Desenvolvidos a Partir de Outros Sistemas

## 1. Introdução

Existem diversos sistemas operacionais que foram desenvolvidos utilizando como base outro sistema operacional, seja por meio do uso de um kernel, de componentes de arquitetura ou de uma estrutura já existente. Essa prática permite aproveitar recursos já desenvolvidos e, ao mesmo tempo, criar novas funcionalidades e características específicas.

Neste trabalho foram pesquisados cinco exemplos de sistemas operacionais que utilizam como base outro sistema ou componentes de outro sistema operacional: **Android, ChromeOS, Ubuntu, macOS e iOS**.

---

## 2. Sistemas Operacionais Pesquisados

### 2.1 Android

O Android utiliza o **kernel Linux** como base. Entretanto, não é simplesmente uma distribuição Linux tradicional. O Android possui componentes próprios, como o Android Runtime (ART), bibliotecas específicas, estrutura de aplicativos e uma interface voltada principalmente para dispositivos móveis.

Segundo a documentação oficial do Android, seu kernel é baseado em versões LTS (Long Term Support) do Linux e recebe modificações específicas para atender às necessidades do Android.

### 2.2 ChromeOS

O ChromeOS também utiliza o **kernel Linux**. Seu desenvolvimento é voltado principalmente para Chromebooks e possui como característica uma forte integração com serviços e aplicações baseadas na nuvem.

O sistema possui mecanismos específicos de segurança, inicialização verificada e atualizações projetadas para manter o sistema estável. O ChromeOS também permite executar aplicações Linux por meio de um ambiente próprio.

### 2.3 Ubuntu

O Ubuntu é uma distribuição baseada no **kernel Linux**. Ele utiliza o kernel Linux juntamente com diversos outros componentes de software livre para formar um sistema operacional completo.

Apesar de utilizar o mesmo kernel de outras distribuições Linux, o Ubuntu possui sua própria organização de pacotes, ferramentas, configurações e ambientes de uso, sendo utilizado em computadores pessoais, servidores e outros dispositivos.

### 2.4 macOS

O macOS possui uma arquitetura diferente dos sistemas Linux citados anteriormente. Seu núcleo, chamado **XNU**, combina o kernel Mach com componentes derivados do BSD e o framework IOKit.

A própria Apple descreve o XNU como um kernel híbrido que combina o Mach, desenvolvido na Carnegie Mellon University, com componentes do FreeBSD e o IOKit.

Portanto, o macOS não deve ser considerado simplesmente uma versão do FreeBSD. Ele possui uma arquitetura própria, mas aproveita componentes e conceitos provenientes da família BSD.

### 2.5 iOS

O iOS também utiliza o **XNU** como parte de sua base. O XNU faz parte do sistema Darwin, utilizado tanto pelo macOS quanto pelo iOS.

Apesar de compartilhar essa base com o macOS, o iOS foi desenvolvido especificamente para dispositivos móveis, possuindo diferentes recursos, restrições de segurança, gerenciamento de aplicativos e interface voltada para telas sensíveis ao toque.

---

## 3. Tabela Comparativa

| Sistema Operacional | Sistema/Base Utilizada | Kernel ou componente principal | Principais diferenças em relação à base                                                                                                                 |
| ------------------- | ---------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Android**         | Linux                  | Kernel Linux                   | Possui Android Runtime, bibliotecas próprias, gerenciamento de aplicativos e interface voltada para smartphones e tablets.                              |
| **ChromeOS**        | Linux                  | Kernel Linux                   | É otimizado para Chromebooks, possui foco em segurança, inicialização verificada, atualizações automáticas e integração com serviços em nuvem.          |
| **Ubuntu**          | Linux                  | Kernel Linux                   | Possui ferramentas, gerenciador de pacotes, configurações e ambientes próprios, sendo uma distribuição Linux completa.                                  |
| **macOS**           | Mach + BSD / Darwin    | XNU                            | Combina Mach e componentes BSD com tecnologias próprias da Apple, como IOKit, além de possuir interface e ferramentas específicas.                      |
| **iOS**             | Darwin / XNU           | XNU                            | Utiliza a mesma base de kernel do macOS, mas é adaptado para dispositivos móveis, com foco em segurança, aplicativos móveis e telas sensíveis ao toque. |

---

## 4. Comparação Geral

Os sistemas pesquisados demonstram que utilizar uma base existente não significa necessariamente criar uma cópia do sistema original.

O **Android, ChromeOS e Ubuntu** possuem o Linux como elemento fundamental, mas cada um foi desenvolvido com objetivos diferentes. O Android é direcionado principalmente para dispositivos móveis, o ChromeOS para computadores Chromebook e o Ubuntu para diferentes tipos de computadores e servidores.

Já o **macOS e o iOS** possuem uma relação diferente. Ambos utilizam o XNU, que combina elementos do Mach e do BSD. Porém, cada sistema foi desenvolvido para um tipo de dispositivo e possui características próprias.

Assim, a utilização de um kernel ou de componentes de outro sistema permite aproveitar tecnologias já consolidadas, enquanto os desenvolvedores podem modificar e adicionar recursos para atender às necessidades específicas de cada sistema operacional.

---

## 5. Conclusão

A pesquisa mostrou que muitos sistemas operacionais modernos são construídos utilizando tecnologias desenvolvidas anteriormente. O uso de um kernel ou de componentes existentes permite reduzir o esforço necessário para desenvolver um sistema completo desde o início.

O Linux é um dos principais exemplos, servindo como base para sistemas como Android, ChromeOS e Ubuntu. Da mesma forma, a arquitetura XNU, composta por elementos do Mach e do BSD, serve como uma importante base para os sistemas operacionais da Apple, como macOS e iOS.

Portanto, sistemas operacionais diferentes podem compartilhar uma mesma base tecnológica e, ainda assim, apresentar características, interfaces, funcionalidades e objetivos completamente diferentes.

## 6. Referências

* Android Open Source Project. **Kernel overview**. Documentação oficial do Android.
* Apple Open Source. **XNU – What is XNU?**. Código-fonte e documentação do kernel XNU.
* Apple Developer. **BSD Overview**. Documentação sobre os componentes BSD utilizados no macOS.
* Google for Developers. **Linux on ChromeOS**. Documentação oficial sobre Linux e ChromeOS.
* Ubuntu. **Ubuntu Core as an immutable Linux Desktop base**. Documentação e informações sobre sistemas baseados em Linux.