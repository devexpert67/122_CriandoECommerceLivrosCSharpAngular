# ANGULAR – INSTALANDO E CONFIGURANDO

[Desenvolvimento](https://igormenezes.com/category/desenvolvimento/), [Linux](https://igormenezes.com/category/linux/) 2 Comments

![Angular](https://igormenezes.com/wp-content/uploads/2018/03/angular-cli-41.png)

## Angular, Instalando e configurando ambiente de desenvolvimento

1 – Primeiramente, temos que instalar o node.js que é o gerenciador de pacotes utilizado, antes do Angular

| 12   | curl -sL https://deb.nodesource.com/setup_8.x \| sudo -E bash -sudo apt-get install -y nodejs |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

2 – Instalando o Angular globalmente em sua máquina.

| 1    | sudo npm install -g @angular/cli |
| ---- | -------------------------------- |
|      |                                  |

3 – Instalando o Typescript globalmente em sua máquina.

| 1    | sudo npm install -g typescript |
| ---- | ------------------------------ |
|      |                                |

4 – Depois de realizado a instalação dos pacotes acima, vamos gerar um projeto.

| 1    | ng new nomeProjeto |
| ---- | ------------------ |
|      |                    |

5 – Rodar o projeto em seu servidor localhost.

| 1    | ng serve |
| ---- | -------- |
|      |          |



## Comandos básicos e outras dicas

1 – Gerar um modulo.

| 12   | ng generate module nomeModulong g module nomeModulo |
| ---- | --------------------------------------------------- |
|      |                                                     |

2 – Gerar um componente.

| 12   | ng generate component nomeModulo/nomeComponenteng g component nomeModulo/nomeComponente |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

3 – Gerar um serviço.

| 12   | ng generate service nomeServicong g service nomeServico |
| ---- | ------------------------------------------------------- |
|      |                                                         |

4 – Instalar bootstrap em seu projeto.

| 1    | npm install --save bootstrap@next |
| ---- | --------------------------------- |
|      |                                   |

Execute os passos a seguir: [github-bootstrap](https://github.com/angular/angular-cli/wiki/stories-include-bootstrap)

5 – Gerando um build de sua aplicação, ambiente de produção e desenvolvimento.

Ambiente de desenvolvimento

| 1    | ng build |
| ---- | -------- |
|      |          |

Ambiente de produção

| 1    | ng build --prod |
| ---- | --------------- |
|      |                 |

Mais informações sobre Build: https://www.youtube.com/watch?v=U0zHj14mNrI

## Referências de funcionalidade e outras dicas

HTTP:
https://www.youtube.com/watch?v=oLtdDwNcfoM

FormBuilder e FormValidator:
https://www.youtube.com/watch?v=931fynCdTKw
https://www.youtube.com/watch?v=RPL_iVbmC1g
https://www.youtube.com/watch?v=H-HjgIONJ-Y
[coursetro](https://coursetro.com/posts/code/66/Angular-4-Reactive-Forms-Tutorial)
[form-validation](https://angular.io/guide/form-validation)

**Obs:** Não se esqueça, os comandos são digitados em um terminal Ubuntu – Linux

 [ANGULAR](https://igormenezes.com/tag/angular/), [ANGULARCLI](https://igormenezes.com/tag/angularcli/), [BOOTSTRAP](https://igormenezes.com/tag/bootstrap/), [LINUX](https://igormenezes.com/tag/linux/)