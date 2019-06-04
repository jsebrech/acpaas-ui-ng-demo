# ACPaaS UI Angular Demo

Dit is een voorbeeld van een ACPaaS UI project in Angular, gemaakt met [Angular CLI](https://github.com/angular/angular-cli) versie 7.3.1.

## Development server

Draai `npm start` voor een dev server. Ga naar `http://localhost:4200/`.

## Hoe dit gemaakt werd

1. Start een nieuw Angular project

```sh
  npm install -g @angular/cli
  ng new ng-demo --style=scss
  cd ng-demo
  npm install @a-ui/core @acpaas-ui/ngx-components
```

> `@a-ui/core` is nodig voor toegang tot SASS variabelen

2. Importeer de core branding stijl in `styles.scss`

```scss
  @import url('https://cdn.antwerpen.be/core_branding_scss/3.1.0/main.min.css');
  @import url('https://cdn.antwerpen.be/core_flexboxgrid_scss/1.0.1/flexboxgrid.min.css');
```

3. Voeg favicons toe in `index.html` van https://github.com/a-ui/core_branding_favicons

  ```html
  <link rel="apple-touch-icon" sizes="180x180" href="https://cdn.antwerpen.be/core_branding_favicons/citizens/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="32x32" href="https://cdn.antwerpen.be/core_branding_favicons/citizens/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="https://cdn.antwerpen.be/core_branding_favicons/citizens/favicon-16x16.png">
  <link rel="manifest" href="https://cdn.antwerpen.be/core_branding_favicons/citizens/site.webmanifest">
  <link rel="mask-icon" href="https://cdn.antwerpen.be/core_branding_favicons/citizens/safari-pinned-tab.svg" color="#cf0039">
  <meta name="msapplication-TileColor" content="#cf0039">
  <meta name="theme-color" content="#cf0039">
```

4. Plaats een huisstijl-conforme layout op de startpagina met [ACPaaS UI](https://github.com/digipolisantwerp/acpaas-ui_angular)

Zie het [Header voorbeeld](https://digipolisantwerp.github.io/acpaas-ui_angular/modules/layout/header) in de ACPaaS UI Examples.

In `src/app/app.module.ts`:

```ts
  import { HeaderModule } from '@acpaas-ui/ngx-components/layout';
  import { FooterModule } from '@acpaas-ui/ngx-components/layout';
  import { LogoModule } from '@acpaas-ui/ngx-components/logo';
  imports: …
```

In `src/styles.scss`:

```scss
  body {
    display: flex;
    min-height: 100vh;
  }
```

In `src/index.html`:

```html
  <body class="has-header" ...>
```

In `src/app/app.component.scss`:

```scss
  /* Core branding API */
  @import '~@a-ui/core/dist/assets/styles/quarks';
  
  :host {
    display: flex;
    flex: 1 1 auto;
    flex-direction: column;
    max-width: 100%;
  }

  main {
    flex: 1 0 auto;
    width: 100%;

    @include to($screen-xs-max) {
      padding-left: 0;
    }
  }
```

In `src/app/app.component.html`:

```html
  <aui-header>
    <div auiHeaderContent>
      <div class="o-header__wrapper">
        <aui-logo src="https://cdn.antwerpen.be/core_branding_scss/3.1.0/assets/images/a-logo.svg"></aui-logo>
      </div>
    </div>
    <div auiHeaderMenuItem>
      <a href="/">
        <button class="a-button">
          <span>Home</span>
        </button>
      </a>
    </div>
  </aui-header>
  <main class="u-wrapper">
    <div class="u-container u-margin-top-xx u-margin-bottom-lg" role="main">
      <div class="row">
        <div class="col-xs-12">
          <h1 class="u-margin-top-xl">Hello Angular!</h1>
          <h2 class="h4 u-margin-top">Handy resources:</h2>
          <ul class="a-list">
            <li>ACPaaS UI homepage: <a href="https://acpaas-ui.digipolis.be/home" target="_blank" rel="noopener noreferrer" class="has-icon-right">https://acpaas-ui.digipolis.be<i class="fa fa-external-link"></i></a></li>
            <li>ACPaaS UI components: <a href="https://digipolisantwerp.github.io/acpaas-ui_angular/" target="_blank" rel="noopener noreferrer" class="has-icon-right">https://digipolisantwerp.github.io/acpaas-ui_angular/<i class="fa fa-external-link"></i></a></li>
            <li>Core Branding: <a href="https://a-ui.github.io/core_branding_scss/" target="_blank" rel="noopener noreferrer" class="has-icon-right">https://a-ui.github.io/core_branding_scss/<i class="fa fa-external-link"></i></a></li>
          </ul>
        </div>
      </div>
    </div>
  </main>
  <aui-footer>
    <div auiFooterBottom>
      <aui-subfooter>
        <aui-copyright domain="Stad Antwerpen"></aui-copyright>
      </aui-subfooter>
    </div>
  </aui-footer>
```
