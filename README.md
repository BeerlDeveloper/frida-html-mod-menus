# 📘 Mod Menu HTML — Componentes Essenciais

Este documento explica COMO criar os principais componentes
do mod menu em HTML + CSS + JavaScript puro.

--------------------------------------------------
📂 CATEGORY (Separador de seção)
--------------------------------------------------

Usado apenas para organização visual do menu.

HTML:
```html
<div class="category">Player</div>
```

Observações:
- Não precisa de JavaScript
- Pode ser usado quantas vezes quiser
- Serve para separar grupos de opções

--------------------------------------------------
🔘 SWITCH (Toggle On / Off)
--------------------------------------------------

Usado para ativar ou desativar funções.

HTML:
```html
<div class="row">
    <span>God Mode</span>
    <label class="switch">
        <input type="checkbox" id="godmode">
        <span class="sliderSwitch"></span>
    </label>
</div>
```

JS (ler estado):
const enabled = document.getElementById("godmode").checked;

Uso comum:
- God Mode
- No Clip
- Infinite Ammo

--------------------------------------------------
🎚️ SLIDER (Texto + Barra deslizante)
--------------------------------------------------

Usado para controlar valores variáveis.

HTML:
```html
<div class="slider-row">
    <span>Speed</span>
    <input type="range" id="speed" min="0" max="100" value="50">
</div>
```

JS (ler valor):
const speedValue = document.getElementById("speed").value;

Uso comum:
- Speed
- Gravity
- Damage
- FOV

--------------------------------------------------
🔢 INPUT — INTEIRO
--------------------------------------------------

Usado para receber números inteiros.

HTML:
```html
<input type="number" id="intValue" step="1" placeholder="Integer value">
```

JS (ler valor):
const intValue = parseInt(document.getElementById("intValue").value);

Uso comum:
- Quantidade
- Level
- IDs numéricos

--------------------------------------------------
🔢 INPUT — FLOAT (Decimal)
--------------------------------------------------

Usado para valores decimais.

HTML:
```html
<input type="number" id="floatValue" step="0.01" placeholder="Float value">
```

JS (ler valor):
const floatValue = parseFloat(document.getElementById("floatValue").value);

Uso comum:
- Multiplicadores
- Escalas
- Valores precisos

--------------------------------------------------
🔘 BUTTON (Ação única)
--------------------------------------------------

Usado para executar ações.

HTML:
```html
<button class="btn" onclick="applySettings()">
    Apply Settings
</button>
```

JS:
function applySettings() {
    alert("Button pressed");
}

Uso comum:
- Aplicar configurações
- Executar comandos
- Enviar ações ao Frida

--------------------------------------------------
📦 SUBMENU (Collapse / Advanced)
--------------------------------------------------

Usado para esconder opções avançadas.

HTML:
```html
<div class="collapse">
    <div class="collapse-header">Advanced</div>
    <div class="collapse-content">
        <div class="row">
            <span>Unlimited Ammo</span>
            <input type="checkbox" id="ammo">
        </div>
    </div>
</div>
```

JS (necessário):

```js
document.querySelectorAll(".collapse-header").forEach(header => {
    header.addEventListener("click", () => {
        const content = header.nextElementSibling;
        content.style.display =
            content.style.display === "block" ? "none" : "block";
        content.style.maxHeight = content.style.maxHeight
            ? null
            : content.scrollHeight + "px";
    });
});
```

Uso comum:
- Opções avançadas
- Submenus
- Features experimentais

--------------------------------------------------
📌 OBSERVAÇÃO FINAL
--------------------------------------------------

Todos os componentes:
- São independentes
- Não usam frameworks
- Funcionam em Android WebView
- Podem ser ligados ao Frida facilmente

Este README serve como guia rápido de implementação.

# Example

```html
<div class="category">Player</div>

<div class="row">
    <span>God Mode</span>
    <label class="switch">
        <input type="checkbox">
        <span class="sliderSwitch"></span>
    </label>
</div>

<div class="progress">
    <span></span>
</div>

<div class="slider-row">
    <span>Speed</span>
    <input type="range" min="0" max="100">
</div>

<div class="category">Inputs</div>

<!-- INT INPUT -->
<input type="number" step="1" placeholder="Integer value">

<!-- FLOAT INPUT -->
<input type="number" step="0.01" placeholder="Float value">

<div class="category">Options</div>

<select>
    <option>Low</option>
    <option>Medium</option>
    <option>High</option>
    <option>Extreme</option>
</select>

<div class="collapse">
    <div class="collapse-header">Advanced</div>
    <div class="collapse-content">
        <div class="row">
            <span>Unlimited Ammo</span>
            <input type="checkbox">
        </div>
    </div>
</div>
```