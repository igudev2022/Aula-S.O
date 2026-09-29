# Manual de Instalação e Utilização de uma Máquina Virtual com Linux

**Disciplina:** Sistemas Operacionais
**Aluno:** Igor Antonio Campos Correa
**Tema:** Instalação do Oracle VirtualBox e Linux em Máquina Virtual

---

## 1. Introdução

Este manual apresenta o processo de instalação do **Oracle VirtualBox**, criação de uma máquina virtual e instalação de um sistema operacional Linux.

O objetivo da atividade é aprender na prática como funciona a virtualização de um sistema operacional, utilizando uma máquina virtual sem precisar instalar o Linux diretamente no computador.

Para este trabalho foi utilizado o **Linux Xubuntu**, por ser uma distribuição baseada em Ubuntu e que possui uma interface relativamente leve.

---

## 2. Objetivo

Os objetivos deste trabalho são:

* Instalar o Oracle VirtualBox;
* Criar uma máquina virtual;
* Configurar memória e armazenamento;
* Instalar uma distribuição Linux;
* Testar o funcionamento do sistema virtualizado;
* Explorar algumas funcionalidades do Linux;
* Documentar todo o processo.

---

# 3. Materiais necessários

Para realizar a atividade foram necessários:

* Computador;
* Conexão com a internet;
* Oracle VirtualBox;
* Imagem ISO do Xubuntu;
* Espaço disponível no disco;
* Memória RAM suficiente para executar a máquina virtual.

---

# 4. Instalação do Oracle VirtualBox

O primeiro passo foi realizar o download do Oracle VirtualBox.

O VirtualBox é um software de virtualização que permite criar e executar máquinas virtuais dentro do computador.

### Passo 1 – Download

Acessei o site oficial do VirtualBox e realizei o download do instalador correspondente ao sistema operacional utilizado no computador.

**Site:** https://www.virtualbox.org/

> **Imagem 1 – Página de download do VirtualBox**

![Página de download do VirtualBox](https://www.virtualbox.org/images/VirtualBox.png)

---

### Passo 2 – Instalação

Depois de baixar o instalador, executei o arquivo e iniciei a instalação.

Durante o processo, mantive as opções padrão recomendadas pelo instalador.

As principais etapas foram:

1. Abrir o instalador;
2. Aceitar os termos de licença;
3. Escolher o local de instalação;
4. Confirmar a instalação;
5. Aguardar o término;
6. Abrir o VirtualBox.

> **Imagem 2 – Tela de instalação do VirtualBox**

![Instalação do VirtualBox](https://www.virtualbox.org/manual/images/installation-windows.png)

---

# 5. Download do Linux

Depois de instalar o VirtualBox, foi necessário obter a imagem ISO do sistema operacional Linux.

Neste trabalho foi utilizado o **Xubuntu**.

O Xubuntu é uma distribuição Linux baseada no Ubuntu que utiliza o ambiente gráfico XFCE, conhecido por ser mais leve.

O download da ISO pode ser realizado pelo site oficial:

https://xubuntu.org/download/

> **Imagem 3 – Download do Xubuntu**

![Xubuntu](https://xubuntu.org/wp-content/uploads/2022/10/xubuntu-logo.png)

---

# 6. Criação da máquina virtual

Com o VirtualBox instalado e a ISO do Linux disponível, foi criada uma nova máquina virtual.

### Passo 1 – Criar uma nova máquina

Na tela principal do VirtualBox, cliquei em:

**Novo**

Em seguida, foi necessário informar:

* Nome da máquina virtual;
* Tipo do sistema operacional;
* Versão do sistema operacional;
* Local onde a máquina seria armazenada.

Foi utilizado um nome semelhante a:

**Xubuntu - Linux**

---

### Passo 2 – Memória RAM

Na configuração de memória, foi definida uma quantidade de RAM para a máquina virtual.

Para o teste, foi utilizada uma quantidade que não comprometesse o funcionamento do computador principal.

**Exemplo utilizado:**

* RAM: 2048 MB

A quantidade pode ser alterada de acordo com a capacidade do computador.

> **Imagem 4 – Configuração da memória RAM**

![Memória RAM](https://www.virtualbox.org/manual/images/create-vm-memory.png)

---

### Passo 3 – Disco rígido virtual

Depois foi criado um disco rígido virtual para armazenar os arquivos do Linux.

Foi selecionada a opção:

**Criar um disco rígido virtual agora**

Depois foi escolhido o formato padrão do VirtualBox.

Para o tamanho do disco, foi utilizado aproximadamente:

**20 GB**

---

# 7. Configuração da ISO

Depois de criar a máquina virtual, foi necessário configurar a imagem ISO do Xubuntu.

Para isso, entrei nas configurações da máquina virtual e acessei:

**Armazenamento → Unidade Óptica**

Depois selecionei o arquivo ISO do Xubuntu que havia sido baixado anteriormente.

Após selecionar a ISO, a máquina virtual estava preparada para iniciar a instalação.

---

# 8. Inicialização da máquina virtual

Com todas as configurações realizadas, iniciei a máquina virtual clicando em:

**Iniciar**

A máquina virtual iniciou utilizando a ISO do Xubuntu.

Foi exibida a tela inicial do sistema operacional.

> **Imagem 5 – Inicialização do Xubuntu**

![Xubuntu inicialização](https://xubuntu.org/wp-content/uploads/2024/02/xubuntu-desktop.png)

---

# 9. Instalação do Xubuntu

Na tela inicial do Xubuntu, foi selecionada a opção para instalar o sistema.

Durante a instalação foram realizadas algumas configurações.

### Idioma

Foi selecionado o idioma desejado para o sistema.

### Teclado

Foi configurado o layout do teclado utilizado no computador.

### Tipo de instalação

Foi selecionada a opção para instalar o Xubuntu no disco virtual criado anteriormente.

Como a instalação está sendo realizada dentro de uma máquina virtual, o disco utilizado é o disco virtual e não o disco principal do computador.

---

## 10. Criação do usuário

Durante a instalação foi solicitado o cadastro de um usuário.

Foram definidos:

* Nome do usuário;
* Nome do computador;
* Nome de usuário;
* Senha.

Depois disso, a instalação continuou automaticamente.

---

# 11. Finalização da instalação

Após alguns minutos, a instalação do Xubuntu foi concluída.

O sistema solicitou a reinicialização da máquina virtual.

Depois da reinicialização, o Linux foi iniciado normalmente.

A máquina virtual passou a apresentar a área de trabalho do Xubuntu.

> **Imagem 6 – Área de trabalho do Xubuntu**

![Área de trabalho do Xubuntu](https://xubuntu.org/wp-content/uploads/2024/02/xubuntu-desktop.png)

---

# 12. Testes realizados

Depois da instalação, foram realizados alguns testes para verificar se o sistema estava funcionando corretamente.

## 12.1 Teste da área de trabalho

Foi possível acessar normalmente a área de trabalho do Xubuntu.

Também foi possível abrir o menu de aplicativos e navegar pelas configurações.

---

## 12.2 Teste do terminal

O terminal foi aberto para verificar o funcionamento dos comandos do Linux.

Foi utilizado o comando:

```bash
ls
```

Esse comando mostra os arquivos e diretórios existentes no local atual.

Também foi utilizado:

```bash
pwd
```

O comando mostra o diretório atual.

Outro comando testado foi:

```bash
uname -a
```

Esse comando apresenta informações sobre o sistema operacional e o kernel.

---

## 12.3 Teste de conexão com a internet

Também foi realizado um teste de conexão utilizando o navegador.

Foi acessado um site para verificar se a máquina virtual possuía acesso à internet.

O teste foi realizado com sucesso.

---

## 12.4 Teste dos aplicativos

Foram explorados alguns aplicativos disponíveis no sistema, como:

* Navegador;
* Terminal;
* Gerenciador de arquivos;
* Configurações do sistema;
* Editor de texto.

Os aplicativos abriram normalmente dentro da máquina virtual.

---

# 13. Exploração das funcionalidades

Após a instalação, algumas funcionalidades do Xubuntu foram exploradas.

Entre elas:

### Gerenciador de arquivos

Permite criar, excluir, copiar e organizar arquivos e pastas.

### Terminal

Permite executar comandos diretamente no sistema.

### Configurações

Permite modificar configurações como:

* Tela;
* Teclado;
* Mouse;
* Rede;
* Aparência;
* Usuários.

### Gerenciador de aplicativos

Permite pesquisar e instalar programas disponíveis para Linux.

---

# 14. Observações sobre a máquina virtual

Durante os testes foi possível perceber que a máquina virtual funciona como um computador separado dentro do computador principal.

O sistema operacional virtualizado possui:

* Área de trabalho própria;
* Arquivos próprios;
* Aplicativos próprios;
* Memória RAM configurada;
* Disco virtual;
* Configurações de rede.

Uma vantagem da virtualização é poder testar outro sistema operacional sem precisar alterar diretamente o sistema instalado no computador principal.

---

# 15. Problemas encontrados

Durante o processo, alguns pontos podem exigir atenção.

A máquina virtual pode apresentar desempenho inferior ao computador físico, principalmente quando é configurada com pouca memória RAM ou poucos recursos.

Também é importante verificar se o computador possui espaço suficiente no armazenamento para criar o disco virtual.

Outro ponto importante é configurar corretamente a imagem ISO para que a máquina virtual consiga iniciar o instalador do Linux.

---

# 16. Resultado final

Ao final da atividade, foi possível criar uma máquina virtual utilizando o Oracle VirtualBox e instalar o sistema operacional Xubuntu.

Também foram realizados testes utilizando o terminal, navegador, gerenciador de arquivos e outras ferramentas disponíveis no sistema.

A máquina virtual funcionou corretamente e permitiu explorar o Linux sem precisar instalá-lo diretamente no computador principal.

---

# 17. Conclusão

A atividade permitiu compreender melhor o funcionamento da virtualização e das máquinas virtuais.

Com o Oracle VirtualBox foi possível criar um ambiente separado para instalar e testar o Xubuntu.

Também foi possível conhecer alguns comandos básicos do Linux e utilizar seus principais aplicativos.

A experiência mostrou que as máquinas virtuais podem ser utilizadas para estudar sistemas operacionais, testar programas e aprender novos ambientes sem modificar diretamente o sistema operacional principal do computador.

---

# 18. Referências

* Oracle VirtualBox: https://www.virtualbox.org/
* Manual do VirtualBox: https://www.virtualbox.org/manual/
* Xubuntu: https://xubuntu.org/
* Ubuntu: https://ubuntu.com/

---

**Aluno:** Igor Antonio Campos Correa
**Disciplina:** Sistemas Operacionais
**Atividade:** Manual de instalação e utilização de máquina virtual Linux
