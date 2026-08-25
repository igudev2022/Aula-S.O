# Aula-S.O

# 💻 História dos Sistemas Operacionais
## Resumo do Capítulo – Tanenbaum & Bos (2015)

> Disciplina: Sistemas Operacionais
>
> Livro Base: **Sistemas Operacionais Modernos**
>
> Autores: **Andrew S. Tanenbaum** e **Herbert Bos**
>
> Edição: 4ª edição (2015)

---

# 📚 Sumário

- Introdução
- O que é um Sistema Operacional
- Evolução Histórica
- Primeira Geração (1945–1955)
- Segunda Geração (1955–1965)
- Terceira Geração (1965–1980)
- Quarta Geração (1980–Presente)
- Quinta Geração (1990–Presente)
- Linha do Tempo
- Conclusão
- Referências

---

# 📖 Introdução

Os sistemas operacionais evoluíram juntamente com o hardware dos computadores.

Nos primeiros computadores não existia nenhum sistema operacional.

Toda tarefa precisava ser executada manualmente.

Os próprios programadores controlavam a máquina.

Era necessário configurar os equipamentos, inserir cartões perfurados, carregar programas e acompanhar toda a execução.

Com o aumento da capacidade dos computadores, essa forma de trabalho deixou de ser eficiente.

Foi nesse contexto que surgiram os primeiros sistemas operacionais.

Sua principal função era organizar o funcionamento do computador e facilitar a utilização dos recursos disponíveis.

Ao longo dos anos, os sistemas operacionais passaram por diversas transformações.

Cada geração de computadores trouxe novos desafios e novas soluções.

Segundo Tanenbaum e Bos, a evolução dos sistemas operacionais acompanha diretamente a evolução da arquitetura dos computadores. :contentReference[oaicite:1]{index=1}

---

# 💡 O que é um Sistema Operacional?

Um Sistema Operacional (SO) é um software responsável por controlar os recursos do computador.

Ele funciona como intermediário entre:

- Hardware
- Programas
- Usuário

Sem um sistema operacional, cada programa precisaria controlar diretamente:

- Processador
- Memória RAM
- Disco
- Monitor
- Teclado
- Mouse
- Impressoras
- Rede

Isso tornaria o desenvolvimento extremamente complexo.

---

## Principais funções

| Função | Descrição |
|--------|-----------|
| Gerenciamento da CPU | Controla qual processo utilizará o processador |
| Gerenciamento de Memória | Organiza a utilização da memória RAM |
| Gerenciamento de Arquivos | Controla onde os dados serão armazenados |
| Entrada e Saída | Coordena a comunicação com dispositivos |
| Segurança | Controla permissões de acesso |
| Interface | Facilita a interação entre usuário e computador |

---

# 🖥️ O Sistema Operacional como Máquina Estendida

Uma das ideias apresentadas por Tanenbaum é que o sistema operacional funciona como uma **máquina estendida**.

Isso significa que ele esconde a complexidade do hardware.

Por exemplo, quando um usuário salva um arquivo, ele não precisa conhecer detalhes sobre:

- setores do disco;
- controladoras;
- endereços físicos;
- comandos elétricos.

O Sistema Operacional realiza todo esse trabalho automaticamente.

Assim, o usuário enxerga apenas uma interface simples e intuitiva.

---

# ⚙️ O Sistema Operacional como Gerenciador de Recursos

Outra visão importante apresentada pelos autores é que o Sistema Operacional funciona como um **gerenciador de recursos**.

Todos os recursos do computador são compartilhados entre diversos programas.

Entre esses recursos estão:

- CPU;
- Memória RAM;
- Disco;
- Impressora;
- Placa de vídeo;
- Interface de rede.

O Sistema Operacional decide:

- quem poderá utilizar cada recurso;
- por quanto tempo;
- em qual ordem.

Esse gerenciamento evita conflitos entre programas e melhora o desempenho do computador. :contentReference[oaicite:2]{index=2}

---

# 🕰️ A Evolução dos Sistemas Operacionais

A história dos sistemas operacionais pode ser dividida em cinco grandes gerações.

Cada geração representa uma evolução tanto do hardware quanto do software.

```text
1ª Geração → Válvulas
        ↓
2ª Geração → Transistores
        ↓
3ª Geração → Circuitos Integrados
        ↓
4ª Geração → Computadores Pessoais
        ↓
5ª Geração → Dispositivos Móveis e Computação Moderna
```

Cada nova geração trouxe melhorias importantes como:

- aumento da velocidade;
- redução do tamanho dos computadores;
- aumento da capacidade de armazenamento;
- surgimento das interfaces gráficas;
- conectividade em rede;
- computação móvel;
- computação em nuvem.

---

# 📜 Primeira Geração (1945–1955)

## Características

A primeira geração foi marcada pela utilização de válvulas eletrônicas.

Os computadores eram extremamente grandes.

Uma única máquina ocupava salas inteiras.

Consumiam enorme quantidade de energia elétrica.

Produziam muito calor.

Apresentavam baixa confiabilidade.

---

## Como era a programação?

Não existiam linguagens de programação modernas.

Tudo era realizado diretamente em linguagem de máquina.

Em muitos casos utilizavam-se:

- chaves elétricas;
- painéis de controle;
- cabos;
- cartões perfurados.

Cada programa precisava ser carregado manualmente.

Depois de terminar sua execução, todo o procedimento precisava ser repetido.

---

## Existia Sistema Operacional?

Não.

Durante essa geração não existia Sistema Operacional.

O próprio usuário era responsável por controlar completamente a máquina.

Entre suas tarefas estavam:

- carregar programas;
- iniciar a execução;
- acompanhar erros;
- remover programas;
- configurar dispositivos.

Cada computador funcionava praticamente de maneira exclusiva para um único usuário.

---

## Principais computadores

| Computador | Ano |
|------------|-----|
| ENIAC | 1945 |
| EDVAC | 1949 |
| EDSAC | 1949 |
| UNIVAC I | 1951 |

Esses computadores representam o início da computação eletrônica moderna.

---

## Resumo da Primeira Geração

| Característica | Situação |
|---------------|----------|
| Sistema Operacional | Não existia |
| Programação | Linguagem de Máquina |
| Interface | Painéis e cartões perfurados |
| Processamento | Um programa por vez |
| Usuários | Apenas especialistas |

---