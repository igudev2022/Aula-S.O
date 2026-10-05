const express = require('express');
const os = require('os');

const app = express();
const PORT = process.env.PORT || 3000;

// ===============================
// DADOS DO SISTEMA
// ===============================

function getSystemInfo() {
  const total = os.totalmem();
  const free = os.freemem();
  const used = total - free;

  const cpus = os.cpus();

  const cpuAverage = cpus.reduce((total, cpu) => {
    return total + cpu.times.user + cpu.times.sys;
  }, 0);

  return {
    hostname: os.hostname(),
    plataforma: os.platform(),
    arquitetura: os.arch(),

    memoria: {
      total: Math.round(total / 1024 / 1024),
      usada: Math.round(used / 1024 / 1024),
      livre: Math.round(free / 1024 / 1024),
      percentual: ((used / total) * 100).toFixed(1)
    },

    cpu: {
      quantidade: cpus.length,
      modelo: cpus[0]?.model || 'Desconhecido'
    },

    uptime: Math.floor(os.uptime() / 60)
  };
}


// ===============================
// API
// ===============================

app.get('/api/system', (req, res) => {
  res.json(getSystemInfo());
});


// ===============================
// DASHBOARD
// ===============================

app.get('/', (req, res) => {

  res.send(`

<!DOCTYPE html>

<html lang="pt-BR">

<head>

<meta charset="UTF-8">

<meta name="viewport"
      content="width=device-width, initial-scale=1.0">

<title>SysMonitor</title>


<style>

/* =====================================
   RESET
===================================== */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Inter, Arial, sans-serif;
}

body {

    background:
        radial-gradient(
            circle at top right,
            #172554 0%,
            #080d1c 40%,
            #050812 100%
        );

    color: #f8fafc;

    min-height: 100vh;

}


/* =====================================
   SIDEBAR
===================================== */

.sidebar {

    position: fixed;

    left: 0;
    top: 0;

    width: 250px;
    height: 100vh;

    background: rgba(8, 13, 28, 0.92);

    backdrop-filter: blur(20px);

    border-right: 1px solid rgba(255,255,255,0.06);

    padding: 28px 18px;

    z-index: 10;

}


/* LOGO */

.logo {

    display: flex;

    align-items: center;

    gap: 12px;

    font-size: 21px;

    font-weight: 800;

    margin-bottom: 40px;

}


.logo-icon {

    width: 42px;
    height: 42px;

    display: flex;

    align-items: center;
    justify-content: center;

    border-radius: 12px;

    background:
        linear-gradient(
            135deg,
            #6366f1,
            #8b5cf6
        );

    box-shadow:
        0 8px 25px rgba(99,102,241,.35);

}


/* MENU */

.menu {

    display: flex;

    flex-direction: column;

    gap: 8px;

}


.menu-title {

    color: #64748b;

    font-size: 11px;

    font-weight: bold;

    letter-spacing: 1px;

    margin: 15px 12px 8px;

    text-transform: uppercase;

}


.menu button {

    width: 100%;

    border: none;

    background: transparent;

    color: #94a3b8;

    padding: 13px 15px;

    border-radius: 12px;

    cursor: pointer;

    text-align: left;

    font-size: 14px;

    transition: .25s;

}


.menu button:hover {

    background: rgba(99,102,241,.10);

    color: white;

}


.menu button.active {

    background:
        linear-gradient(
            90deg,
            rgba(99,102,241,.25),
            rgba(139,92,246,.08)
        );

    color: white;

    box-shadow:
        inset 3px 0 #6366f1;

}


.menu-icon {

    margin-right: 10px;

}


/* =====================================
   MAIN
===================================== */

.main {

    margin-left: 250px;

    padding: 35px;

}


/* HEADER */

.header {

    display: flex;

    align-items: center;

    justify-content: space-between;

    margin-bottom: 30px;

}


.header h1 {

    font-size: 30px;

    margin-bottom: 5px;

}


.header p {

    color: #64748b;

    font-size: 14px;

}


/* STATUS */

.status {

    display: flex;

    align-items: center;

    gap: 9px;

    padding: 9px 15px;

    border-radius: 30px;

    background: rgba(34,197,94,.08);

    border: 1px solid rgba(34,197,94,.18);

    color: #4ade80;

    font-size: 13px;

}


.status-dot {

    width: 8px;
    height: 8px;

    background: #22c55e;

    border-radius: 50%;

    box-shadow:
        0 0 12px #22c55e;

}


/* =====================================
   ABAS
===================================== */

.tab {

    display: none;

    animation: fade .3s ease;

}


.tab.active {

    display: block;

}


@keyframes fade {

    from {
        opacity: 0;
        transform: translateY(8px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }

}


/* =====================================
   CARDS
===================================== */

.cards {

    display: grid;

    grid-template-columns:
        repeat(4, 1fr);

    gap: 18px;

    margin-bottom: 20px;

}


.card {

    background:
        linear-gradient(
            145deg,
            rgba(20,28,52,.9),
            rgba(11,17,34,.9)
        );

    border:

        1px solid
        rgba(255,255,255,.06);

    border-radius: 18px;

    padding: 22px;

    position: relative;

    overflow: hidden;

    transition: .25s;

}


.card:hover {

    transform: translateY(-4px);

    border-color:
        rgba(99,102,241,.4);

}


.card::after {

    content: "";

    position: absolute;

    width: 100px;
    height: 100px;

    right: -40px;
    top: -40px;

    background:
        radial-gradient(
            circle,
            rgba(99,102,241,.18),
            transparent 70%
        );

}


.card-icon {

    font-size: 24px;

    margin-bottom: 15px;

}


.card-label {

    color: #64748b;

    font-size: 12px;

    margin-bottom: 8px;

}


.card-value {

    font-size: 22px;

    font-weight: 700;

}


/* =====================================
   PAINÉIS
===================================== */

.grid {

    display: grid;

    grid-template-columns:
        1.5fr 1fr;

    gap: 20px;

}


.panel {

    background:
        rgba(15,23,42,.72);

    border:

        1px solid
        rgba(255,255,255,.06);

    border-radius: 18px;

    padding: 25px;

}


.panel-title {

    font-size: 17px;

    font-weight: 700;

    margin-bottom: 22px;

}


/* =====================================
   MEMÓRIA
===================================== */

.memory {

    display: flex;

    align-items: center;

    gap: 35px;

}


.circle {

    width: 170px;
    height: 170px;

    border-radius: 50%;

    background:
        conic-gradient(
            #6366f1
            0%,

            #8b5cf6
            ${0}%,

            #1e293b
            0%
        );

    display: flex;

    align-items: center;

    justify-content: center;

    position: relative;

}


.circle::before {

    content: "";

    position: absolute;

    width: 130px;
    height: 130px;

    background: #0b1120;

    border-radius: 50%;

}


.circle-content {

    position: relative;

    text-align: center;

}


.circle-number {

    font-size: 28px;

    font-weight: 800;

}


.circle-text {

    color: #64748b;

    font-size: 11px;

}


.memory-info {

    flex: 1;

}


.memory-row {

    display: flex;

    justify-content: space-between;

    padding: 12px 0;

    border-bottom:

        1px solid
        rgba(255,255,255,.05);

    font-size: 13px;

}


.memory-row span {

    color: #64748b;

}


/* =====================================
   SISTEMA
===================================== */

.system-list {

    display: flex;

    flex-direction: column;

    gap: 4px;

}


.system-row {

    display: flex;

    justify-content: space-between;

    padding: 14px 0;

    border-bottom:

        1px solid
        rgba(255,255,255,.05);

    font-size: 13px;

}


.system-row span {

    color: #64748b;

}


/* =====================================
   CPU
===================================== */

.cpu-box {

    text-align: center;

    padding: 35px 20px;

}


.cpu-number {

    font-size: 60px;

    font-weight: 800;

    background:
        linear-gradient(
            135deg,
            #6366f1,
            #c084fc
        );

    -webkit-background-clip: text;

    -webkit-text-fill-color: transparent;

}


.cpu-label {

    color: #64748b;

    margin-top: 5px;

}


/* =====================================
   RESPONSIVO
===================================== */

@media(max-width:1100px) {

    .cards {

        grid-template-columns:
            repeat(2,1fr);

    }

    .grid {

        grid-template-columns: 1fr;

    }

}


@media(max-width:700px) {

    .sidebar {

        width: 70px;

        padding: 20px 10px;

    }

    .logo span {

        display: none;

    }

    .menu button {

        text-align: center;

        font-size: 0;

    }

    .menu-icon {

        font-size: 20px;

        margin: 0;

    }

    .main {

        margin-left: 70px;

        padding: 20px;

    }

    .cards {

        grid-template-columns: 1fr;

    }

    .header {

        flex-direction: column;

        align-items: flex-start;

        gap: 15px;

    }

    .memory {

        flex-direction: column;

    }

}

</style>

</head>


<body>


<!-- =====================================
     SIDEBAR
===================================== -->

<aside class="sidebar">

    <div class="logo">

        <div class="logo-icon">
            🖥️
        </div>

        <span>
            SysMonitor
        </span>

    </div>


    <div class="menu">

        <div class="menu-title">
            Principal
        </div>


        <button
            class="active"
            onclick="abrirAba('dashboard', this)"
        >

            <span class="menu-icon">
                📊
            </span>

            Dashboard

        </button>


        <button
            onclick="abrirAba('memoria', this)"
        >

            <span class="menu-icon">
                🧠
            </span>

            Memória

        </button>


        <button
            onclick="abrirAba('processador', this)"
        >

            <span class="menu-icon">
                ⚡
            </span>

            Processador

        </button>


        <div class="menu-title">
            Sistema
        </div>


        <button
            onclick="abrirAba('sistema', this)"
        >

            <span class="menu-icon">
                ⚙️
            </span>

            Sistema

        </button>


        <button
            onclick="abrirAba('sobre', this)"
        >

            <span class="menu-icon">
                ℹ️
            </span>

            Sobre

        </button>

    </div>

</aside>


<!-- =====================================
     MAIN
===================================== -->

<main class="main">


<div class="header">

    <div>

        <h1 id="titulo">
            Dashboard
        </h1>

        <p id="subtitulo">
            Monitoramento do computador em tempo real
        </p>

    </div>


    <div class="status">

        <span class="status-dot"></span>

        Sistema Online

    </div>

</div>


<!-- =====================================
     DASHBOARD
===================================== -->

<section
    id="dashboard"
    class="tab active"
>


<div class="cards">


    <div class="card">

        <div class="card-icon">
            🖥️
        </div>

        <div class="card-label">
            HOSTNAME
        </div>

        <div
            class="card-value"
            id="hostname"
        >
            Carregando...
        </div>

    </div>


    <div class="card">

        <div class="card-icon">
            💻
        </div>

        <div class="card-label">
            PLATAFORMA
        </div>

        <div
            class="card-value"
            id="plataforma"
        >
            -
        </div>

    </div>


    <div class="card">

        <div class="card-icon">
            ⚡
        </div>

        <div class="card-label">
            PROCESSADORES
        </div>

        <div
            class="card-value"
            id="cpus"
        >
            -
        </div>

    </div>


    <div class="card">

        <div class="card-icon">
            ⏱️
        </div>

        <div class="card-label">
            UPTIME
        </div>

        <div
            class="card-value"
            id="uptime"
        >
            -
        </div>

    </div>

</div>


<div class="grid">


<div class="panel">

    <div class="panel-title">
        🧠 Memória RAM
    </div>


    <div class="memory">


        <div
            class="circle"
            id="memoryCircle"
        >

            <div class="circle-content">

                <div
                    class="circle-number"
                    id="memoryPercent"
                >
                    0%
                </div>

                <div class="circle-text">
                    utilizada
                </div>

            </div>

        </div>


        <div class="memory-info">


            <div class="memory-row">

                <span>
                    Memória utilizada
                </span>

                <strong id="memoryUsed">
                    -
                </strong>

            </div>


            <div class="memory-row">

                <span>
                    Memória livre
                </span>

                <strong id="memoryFree">
                    -
                </strong>

            </div>


            <div class="memory-row">

                <span>
                    Memória total
                </span>

                <strong id="memoryTotal">
                    -
                </strong>

            </div>


        </div>

    </div>

</div>


<div class="panel">

    <div class="panel-title">
        ⚙️ Informações
    </div>


    <div class="system-list">


        <div class="system-row">

            <span>
                Arquitetura
            </span>

            <strong id="arquitetura">
                -
            </strong>

        </div>


        <div class="system-row">

            <span>
                CPU
            </span>

            <strong id="cpuModelo">
                -
            </strong>

        </div>


        <div class="system-row">

            <span>
                CPUs
            </span>

            <strong id="cpuQtd">
                -
            </strong>

        </div>


    </div>

</div>


</div>

</section>


<!-- =====================================
     MEMÓRIA
===================================== -->

<section
    id="memoria"
    class="tab"
>


<div class="panel">

    <div class="panel-title">
        🧠 Monitoramento de Memória
    </div>


    <div class="memory">


        <div
            class="circle"
            id="memoryCircle2"
        >

            <div class="circle-content">

                <div
                    class="circle-number"
                    id="memoryPercent2"
                >
                    0%
                </div>

                <div class="circle-text">
                    RAM utilizada
                </div>

            </div>

        </div>


        <div class="memory-info">

            <div class="memory-row">

                <span>
                    RAM utilizada
                </span>

                <strong id="memoryUsed2">
                    -
                </strong>

            </div>


            <div class="memory-row">

                <span>
                    RAM disponível
                </span>

                <strong id="memoryFree2">
                    -
                </strong>

            </div>


            <div class="memory-row">

                <span>
                    RAM total
                </span>

                <strong id="memoryTotal2">
                    -
                </strong>

            </div>

        </div>

    </div>

</div>

</section>


<!-- =====================================
     PROCESSADOR
===================================== -->

<section
    id="processador"
    class="tab"
>


<div class="panel">

    <div class="panel-title">
        ⚡ Processador
    </div>


    <div class="cpu-box">

        <div
            class="cpu-number"
            id="cpuNumber"
        >
            0
        </div>

        <div class="cpu-label">
            processadores disponíveis
        </div>


        <br>


        <div
            id="cpuModel2"
            style="
                color:#94a3b8;
                font-size:14px;
            "
        >
            -
        </div>

    </div>

</div>

</section>


<!-- =====================================
     SISTEMA
===================================== -->

<section
    id="sistema"
    class="tab"
>


<div class="panel">

    <div class="panel-title">
        ⚙️ Sistema Operacional
    </div>


    <div class="system-list">


        <div class="system-row">

            <span>
                Hostname
            </span>

            <strong id="systemHostname">
                -
            </strong>

        </div>


        <div class="system-row">

            <span>
                Sistema
            </span>

            <strong id="systemPlatform">
                -
            </strong>

        </div>


        <div class="system-row">

            <span>
                Arquitetura
            </span>

            <strong id="systemArch">
                -
            </strong>

        </div>


        <div class="system-row">

            <span>
                Uptime
            </span>

            <strong id="systemUptime">
                -
            </strong>

        </div>


    </div>

</div>

</section>


<!-- =====================================
     SOBRE
===================================== -->

<section
    id="sobre"
    class="tab"
>


<div class="panel">

    <div class="panel-title">
        ℹ️ Sobre o SysMonitor
    </div>


    <p
        style="
            color:#94a3b8;
            line-height:1.8;
        "
    >

        O <strong style="color:white">
        SysMonitor
        </strong>

        é um dashboard desenvolvido com

        <strong style="color:#6366f1">
        Node.js
        </strong>

        e

        <strong style="color:#8b5cf6">
        Express
        </strong>

        para monitoramento de informações
        do sistema operacional.

        <br><br>

        Os dados são atualizados automaticamente
        através de uma API.

    </p>

</div>

</section>


</main>


<script>


// =====================================
// TROCAR ABAS
// =====================================

function abrirAba(nome, botao) {

    document
        .querySelectorAll('.tab')
        .forEach(tab => {

            tab.classList.remove('active');

        });


    document
        .querySelectorAll('.menu button')
        .forEach(btn => {

            btn.classList.remove('active');

        });


    document
        .getElementById(nome)
        .classList.add('active');


    botao.classList.add('active');


    const titulos = {

        dashboard: [
            'Dashboard',
            'Visão geral do sistema'
        ],

        memoria: [
            'Memória',
            'Monitoramento da memória RAM'
        ],

        processador: [
            'Processador',
            'Informações do processador'
        ],

        sistema: [
            'Sistema',
            'Informações do sistema operacional'
        ],

        sobre: [
            'Sobre',
            'Informações do SysMonitor'
        ]

    };


    document.getElementById('titulo')
        .innerText = titulos[nome][0];


    document.getElementById('subtitulo')
        .innerText = titulos[nome][1];

}


// =====================================
// ATUALIZAR DADOS
// =====================================

async function atualizarSistema() {

    try {

        const resposta =
            await fetch('/api/system');

        const dados =
            await resposta.json();


        // HOSTNAME

        document.getElementById(
            'hostname'
        ).innerText =
            dados.hostname;


        document.getElementById(
            'plataforma'
        ).innerText =
            dados.plataforma;


        document.getElementById(
            'cpus'
        ).innerText =
            dados.cpu.quantidade;


        document.getElementById(
            'uptime'
        ).innerText =
            dados.uptime + ' min';


        // MEMÓRIA

        const memoria =
            dados.memoria;


        document.getElementById(
            'memoryPercent'
        ).innerText =
            memoria.percentual + '%';


        document.getElementById(
            'memoryUsed'
        ).innerText =
            memoria.usada + ' MB';


        document.getElementById(
            'memoryFree'
        ).innerText =
            memoria.livre + ' MB';


        document.getElementById(
            'memoryTotal'
        ).innerText =
            memoria.total + ' MB';


        document.getElementById(
            'memoryPercent2'
        ).innerText =
            memoria.percentual + '%';


        document.getElementById(
            'memoryUsed2'
        ).innerText =
            memoria.usada + ' MB';


        document.getElementById(
            'memoryFree2'
        ).innerText =
            memoria.livre + ' MB';


        document.getElementById(
            'memoryTotal2'
        ).innerText =
            memoria.total + ' MB';


        // CÍRCULOS

        document.getElementById(
            'memoryCircle'
        ).style.background =

            \`conic-gradient(
                #6366f1 0%,
                #8b5cf6 \${memoria.percentual}%,
                #1e293b \${memoria.percentual}%,
                #1e293b 100%
            )\`;


        document.getElementById(
            'memoryCircle2'
        ).style.background =

            \`conic-gradient(
                #6366f1 0%,
                #8b5cf6 \${memoria.percentual}%,
                #1e293b \${memoria.percentual}%,
                #1e293b 100%
            )\`;


        // SISTEMA

        document.getElementById(
            'arquitetura'
        ).innerText =
            dados.arquitetura;


        document.getElementById(
            'cpuModelo'
        ).innerText =
            dados.cpu.modelo;


        document.getElementById(
            'cpuQtd'
        ).innerText =
            dados.cpu.quantidade;


        // PROCESSADOR

        document.getElementById(
            'cpuNumber'
        ).innerText =
            dados.cpu.quantidade;


        document.getElementById(
            'cpuModel2'
        ).innerText =
            dados.cpu.modelo;


        // ABA SISTEMA

        document.getElementById(
            'systemHostname'
        ).innerText =
            dados.hostname;


        document.getElementById(
            'systemPlatform'
        ).innerText =
            dados.plataforma;


        document.getElementById(
            'systemArch'
        ).innerText =
            dados.arquitetura;


        document.getElementById(
            'systemUptime'
        ).innerText =
            dados.uptime + ' minutos';


    } catch (erro) {

        console.error(
            'Erro ao obter dados:',
            erro
        );

    }

}


// Atualiza imediatamente

atualizarSistema();


// Atualiza a cada 3 segundos

setInterval(
    atualizarSistema,
    3000
);


</script>


</body>

</html>

  `);

});


app.listen(PORT, () => {
    console.log(`🚀 SysMonitor rodando em http://localhost:${PORT}`);
});

