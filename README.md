# ccs_html_portifolio_challenge
Desafio de HTML5 & CSS3 para conclusão de curso online do Gustavo Guanabara. Embora seja o trabalho de conclusão de curso, estou extrapolando, e muito, o que foi ensinado no curso, adicionando animações complexas e elementos de design mais ousados que os ensinados/recomendados no curso.

### Status do projeto:
- Em Desenvolvimento. Por volta de 40% do projeto concluído.

[x] Item 1

[x] Item 2

[ ] Item 3

## O que aprendi?

### SVG
- É possível chamar vários ícones diferentes de um único SVG monocromático.
- O parâmetro `fill="currentColor"` no XML permite que o SVG receba a cor da fonte (`color`) do CSS.
- Inkscape é capaz de editar o XML do SVG atual diretamente através do menu  `Edit > SVG File`¹.
- Polígonos complexos não são tags reais em XML, como alguns editores podem fazer parecer, na verdade eles são `path`. Formas simples suportadas se limitam á `circle`, `rect` e `elipse`.
- SVG com textura pode ser inserido diretamente no html. Importante que esteja no `<body>`, preferencialmente lodo no topo da tag. Exemplo:
```html   
<body>

    <svg width="100px" height="100px" xmlns="http://www.w3.org/2000/svg">
        <defs>
            <pattern id="dotPattern" width="6" height="6" patternUnits="userSpaceOnUse">
                <circle cx="3" cy="3" r="2" fill="#fa0" />
            </pattern>
        </defs>
        <rect x="0" y="0" width="100%" height="100%" fill="url(#dotPattern)" stroke="black" stroke-width="1"/>
    </svg>

    <!-- Restante do Corpo-->

</body>
```
 

### CSS - Perigos Escondidos

*Disclaimer: O que segue nesta sessão são opiniões pessoais, e talvez um pouco radicais. Essa postura é pessoalmente importante pra mim, pois me ajudam a gravar regras com mais facilidade, mas considerem como contendo um pouco de exagero*

- **Não use Pseudo-objetos!** `::after` e `::before` são remendos, na maioria das vezes. Embora seja um atalho irresistível, ele torna o empilhamento de design de elementos um problema e ainda desrespeita boas práticas. O ideal é sempre abrir uma nova `<div>` com um nome de `class=` ou `id=` que especifique bem a função daquela camada/objeto. Neste projeto em especifico, acabei caindo na armadilha e vi como ele é capaz de bagunçar a organização. Só faz sentido se semanticamente o pseudo objeto for **literalmente** "objeto-antes" e "objeto-depois", ainda assim ,você pode precisar de duas camadas do "objeto-frente" o que novamente compromete a leitura e entendimento do fluxo. Outra exceção é quando é necessário inserir texto de forma dinâmica a um elemento, embora talvez existam formar mais corretas de fazer isso também. Mas o atalho fácil sobre o fácil ainda é: **Pseudo-objetos são gambiarra!**

- **Outline não é objeto de Design!** Essa é uma função criada originalmente para questões de acessibilidade e comunicação por `tabIndex` - ele não é um objeto de design, e sim um seletor pra mostrar onde o foco do seletor está. Se precisar de duas bordas, ou mais, o caminho é mesmo pra erradicar pseudo-objetos: volte pro HTML e adicione novas *"divs"* com bons nomes. O `outline` só ser torna uma elementos de design, quando um dos objetivos da página é ter uma boa navegação por teclado. Neste caso, convém que o feedback visual de `:focus` tenha um visual condizente com todo o contexto.




### CSS - Gradientes
- Gradiente na verdade são renderizados como imagem, e por isso são chamados com `background-image:`.

- Gradiente não pode ser renderizado menor e ser esticado de forma pixelizada para fazer saltos de cores. Se esta função for necerrária, é preciso fazer os saltos bruscos diretamente.

### CSS - Variáveis
- Variáveis geralmente são declaradas no `root{...}` mas também podem estar dentro de objetos.

- Variáveis podem ser animadas, desde que elas seja tipadas usando a regra @property. O 'canvas', biblioteca do javascript parece ser capaz de fazer esta ação.

```css
@property --minha-cor {
  syntax: '<color>';
  initial-value: #c0ffee;
  inherits: false;
}
```

### CSS - Animações

- Algumas propriedade quando animadas trabalham com  pixel-perfect e outras trabalham com sub-pixel. Normalmente o segundo caso é preferível, principalmente em animações lentas e suaves, pois as que são pixel-perfect acabam dando saltos e impressão de estar rodando a animação com baixo FPS.
    - Exemplo de Propriedades pixel-perfect ou 'salto de pixels": `height`, `width`, `background`, `mask` etc
    - Exemplo de Propriedades com sub-pixel nas animações: `transform`, `filter` etc.

- 



