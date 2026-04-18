# una-blazor-lista12.

## 📌 Identificação
Nome: GUILHERME FÁBIO SILVA DE MORAIS 
RA:4261213582
CURSO: ANÁLISE E DESENVOLVIMENTO DE SISTEMAS.
Components/Pages/EcoStatus.razor

<h3>@Titulo</h3>

<p>Pontos por ação: @Peso</p>
<p>Total acumulado: @Total</p>

<button @onclick="Incrementar">Registrar Atividade</button>

@if (Total >= 50)
{
    <p style="color: green;">Meta atingida!</p>
}

@if (Total >= 100)
{
    <p style="color: green;">🌱 Você é um Herói do Planeta!</p>
}

@code {
    [Parameter]
    public string Titulo { get; set; } = "";

    [Parameter]
    public int Peso { get; set; }

    private int Total = 0;

    void Incrementar()
    {
        Total += Peso;
    }
}

Components/Pages/Index.razor

@page "/"

<h1>EcoMonitor</h1>

<EcoStatus Titulo="Reciclagem de Plástico" Peso="1" />
<EcoStatus Titulo="Descarte de Eletrônicos" Peso="5" />
<EcoStatus Titulo="Plantio de Árvores" Peso="10" />

Components/_Imports.razor

@using Ecomonitor.Components
@using Ecomonitor.Components.Pages
@using Microsoft.AspNetCore.Components

Components/Routes.razor

<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(Layout.MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(Layout.MainLayout)">
            <p>Página não encontrada</p>
        </LayoutView>
    </NotFound>
</Router>

Components/App.razor

<Routes />

Program.cs

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddRazorComponents()
    .AddInteractiveServerComponents();

var app = builder.Build();

app.UseHttpsRedirection();
app.UseStaticFiles();

app.MapRazorComponents<App>()
    .AddInteractiveServerRenderMode();

app.Run();

# 🌱 EcoMonitor

---

## 🎯 Descrição do Projeto

O EcoMonitor é uma aplicação desenvolvida em Blazor com o objetivo de registrar ações sustentáveis realizadas por um usuário, exibindo o impacto dessas ações em tempo real.

Cada ação possui um peso (pontuação), e o sistema acumula pontos conforme o usuário interage.

---

## ⚙️ Funcionalidades

- Registro de ações sustentáveis
- Contador dinâmico de pontos
- Componentes reutilizáveis
- Mensagem de meta atingida
- Feedback visual para o usuário

---

## 🧠 Heurísticas de Nielsen aplicadas

### 1. Visibilidade do Status do Sistema
O sistema mostra o total acumulado de pontos em tempo real após cada interação do usuário.

### 2. Feedback Imediato
Ao clicar no botão, o usuário recebe uma resposta instantânea com a atualização do contador e mensagens quando metas são atingidas.

---

## 🚀 Guia de Execução

1. Abrir o projeto no Visual Studio
2. Executar o projeto (F5)
3. A aplicação será aberta automaticamente no navegador

---

## 🔧 Explicação Técnica

O componente EcoStatus utiliza o atributo `[Parameter]` para receber dados externos, como o título da ação e seu peso.

Isso permite que o mesmo componente seja reutilizado diversas vezes com comportamentos diferentes, tornando o sistema modular e eficiente.

O estado da aplicação é controlado pela variável `Total`, que é atualizada a cada clique do usuário.

---

## ⭐ Diferenciais Implementados

- Mensagem especial ao atingir 100 pontos
- Mudança de cor ao atingir meta

