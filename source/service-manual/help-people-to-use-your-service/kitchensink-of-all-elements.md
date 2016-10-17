---
layout: blank
title: A kitchensink of all elements
category: Help people to use your service
draft: true
---

<head>
  <meta charset="utf-8">
  <title>{{ page.title }} - {{ site.title }} - dorel.io</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">

  <!-- Fundament style to reset browser defaults -->
  <link rel="stylesheet" type="text/css" href="./assets/styles/style-fundament.css">

  {% comment %}
    *
    * webcomponents-lite.min.js = polyfill for polymer elements
    *
    * important: include this file before any code that touches the DOM
    *
  {% endcomment %}
  <script src="/bower_components/webcomponentsjs/webcomponents-lite.min.js"></script>

  <link rel="import" href="/bower_components/iron-flex-layout/iron-flex-layout.html">
  <link rel="import" href="/bower_components/iron-iconset/iron-iconset.html">

  <link rel="import" href="/bower_components/paper-header-panel/paper-header-panel.html">
  <link rel="import" href="/bower_components/paper-toolbar/paper-toolbar.html">
  <link rel="import" href="/bower_components/paper-badge/paper-badge.html">
  
  <!-- paper-styles -->
  <link rel="import" href="/bower_components/paper-styles/color.html">
  <link rel="import" href="/bower_components/paper-styles/shadow.html">
  <link rel="import" href="/bower_components/paper-styles/typography.html">

  <!-- themes 
  Add theme files the <head> tag _AFTER_ the
  webcomponents-lite.min.js and other HTML imports. 
  - These can be used for the template switcher.
  -->
  <link rel="import" href="/bower_components/paper-styles/default-theme">

  <!--script src="/bower_components/platform/platform.js"></script-->
</head>

<!-- Custom style for polymer objects -->
<style is="custom-style">

  .shadow {
    display: inline-block;
    padding: 8px;
    margin: 16px;
    height: 50px;
    width: 50px;
  }

  .shadow-2dp {
    @apply(--shadow-elevation-2dp);
  }

</style>

<body>

  <paper-header-panel mode="waterfall-tall">
    <paper-toolbar>
      <div>Header</div>
    </paper-toolbar>
  </paper-header-panel>

  <main>

    <section class="typography">
      <h1>Typography</h1>
      <h2>Heading 2</h2>
      <h3>Heading 3</h3>
      <h4>Heading 4</h4>
      <h5>Heading 5</h5>
      <h6>Heading 6</h6>
      <div class="paper-font-display4">Display 4</div>
      <div class="paper-font-display3">Display 3</div>
      <div class="paper-font-display2">Display 2</div>
      <div class="paper-font-display1">Display 1</div>
      <div class="paper-font-headline">Headline</div>
      <div class="paper-font-title">Title</div>
      <div class="paper-font-subhead">Subhead</div>
      <div class="paper-font-body2">Body 2</div>
      <div class="paper-font-body1">Body 1</div>
      <div class="paper-font-caption">Caption</div>
      <div class="paper-font-menu">Menu</div>
      <div class="paper-font-button">Button</div>
      <div class="paper-font-body2">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Non igitur potestis voluptate omnia dirigentes aut tueri aut retinere virtutem. Equidem e Cn. Quid, si etiam iucunda memoria est praeteritorum malorum? Ita multo sanguine profuso in laetitia et in victoria est mortuus. Nunc ita separantur, ut disiuncta sint, quo nihil potest esse perversius. Duo Reges: constructio interrete.</p>
      </div>
      <div class="paper-font-body1">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Non igitur potestis voluptate omnia dirigentes aut tueri aut retinere virtutem. Equidem e Cn. Quid, si etiam iucunda memoria est praeteritorum malorum? Ita multo sanguine profuso in laetitia et in victoria est mortuus. Nunc ita separantur, ut disiuncta sint, quo nihil potest esse perversius. Duo Reges: constructio interrete.</p>
      </div>
    </section>

    <section id="shadow">
      <h2>shadow.html</h2>
      <div class="shadow shadow-2dp">2dp</div>
      <div class="shadow shadow-3dp">3dp</div>
      <div class="shadow shadow-4dp">4dp</div>
      <div class="shadow shadow-6dp">6dp</div>
      <div class="shadow shadow-8dp">8dp</div>
      <div class="shadow shadow-12dp">12dp</div>
      <div class="shadow shadow-16dp">16dp</div>
    </section>

    <section id="demo-page">
      <h2>demo-pages.html</h2>

      <h3>Horizontal sections</h3>
      <div class="horizontal-section-container">
        <div>
          <h4>Column 1</h4>
          <div class="horizontal-section">
            <div>Oxygen</div>
            <div>Carbon</div>
            <div>Hydrogen</div>
            <div>Nitrogen</div>
            <div>Calcium</div>
          </div>
        </div>

        <div>
          <h4>Column 2</h4>
          <div class="horizontal-section">
            <div>Oxygen</div>
            <div>Carbon</div>
            <div>Hydrogen</div>
            <div>Nitrogen</div>
            <div>Calcium</div>
          </div>
        </div>

        <div>
          <h4>Column 3</h4>
          <div class="horizontal-section">
            <div>Oxygen</div>
            <div>Carbon</div>
            <div>Hydrogen</div>
            <div>Nitrogen</div>
            <div>Calcium</div>
          </div>
        </div>
      </div>

      <h3>Vertical sections</h3>
      <div class="vertical-section-container">
        <div>
          <h4>Section 1</h4>
          <div class="vertical-section">
            <div>Oxygen</div>
            <div>Carbon</div>
            <div>Hydrogen</div>
            <div>Nitrogen</div>
            <div>Calcium</div>
          </div>
        </div>
      </div>

      <div class="vertical-section-container centered">
        <h4>Section 2 (centered)</h4>
        <div class="vertical-section">
          <div>Oxygen</div>
          <div>Carbon</div>
          <div>Hydrogen</div>
          <div>Nitrogen</div>
          <div>Calcium</div>
        </div>
      </div>
    </section>

    <section id="default-theme">
      <h2>default-theme.html</h2>
      <section class="mobile-app">
        <div class="toolbar">
          Title
        </div>
        <div class="item">
          <div class="fab">+</div>
          <div class="primary">Primary text</div>
          <div class="secondary">Secondary text</div>
        </div>
        <div class="disabled-item">
          Disabled
        </div>
      </section>
    </section>

    <section id="badges">

        <demo-snippet class="centered-demo">
          <template>
            <paper-icon-button id="number" icon="communication:email" alt="inbox">
            </paper-icon-button>
            <paper-badge for="number" label="4">
            </paper-badge>

            <paper-icon-button id="icon" icon="account-box" alt="person">
            </paper-icon-button>
            <paper-badge icon="social:mood" for="icon" label="happy">
            </paper-badge>
          </template>
        </demo-snippet>

        <h3>Badges can be applied to direct siblings</h3>
        <demo-snippet class="centered-demo">
          <template>
            <div class="container" tabindex="0">
              <span>Inbox</span>
              <paper-badge label="4"></paper-badge>
            </div>

            <div class="container" tabindex="0">
              <span>Mood</span>
              <paper-badge icon="social:mood" label="happy"></paper-badge>
            </div>

            <style is="custom-style">
              .container {
                display: inline-block;
                margin-left: 30px;
                margin-right: 30px;
              }
              /* Need to position the badge to look like a text superscript */
              .container > paper-badge {
                --paper-badge-margin-left: 20px;
                --paper-badge-margin-bottom: 0px;
              }
            </style>
          </template>
        </demo-snippet>

        <h3>Badges can be customized using custom properties</h3>
        <demo-snippet class="centered-demo">
          <template>
            <paper-icon-button id="number2" icon="communication:email" alt="inbox">
            </paper-icon-button>
            <paper-badge for="number2" label="4" class="red">
            </paper-badge>

            <paper-icon-button id="icon2" icon="account-box" alt="account-box">
            </paper-icon-button>
            <paper-badge icon="social:mood" for="icon2" label="happy" class="blue">
            </paper-badge>

            <style is="custom-style">
              .red {
                --paper-badge-background: var(--paper-red-300);
              }
              .blue {
                --paper-badge-background: var(--paper-light-blue-300);
              }
            </style>
          </template>
        </demo-snippet>

    </section>

    <section>
      <paper-input label="text input"></paper-input>
      <paper-textarea label="autoresizing textarea input"></paper-textarea>
      <paper-input label="password input" type="password"></paper-input>
      <paper-input label="disabled input" disabled></paper-input>
      <paper-input-container>
        <label>Your name</label>
        <input is="iron-input">
      </paper-input-container>
    </section>

  </main>

  <script>
    // Uses webcomponents-lite.min.js.
    // If you aren't using the polyfill, you can't rely on the WebComponentsReady.
    // To ensure that elements are ready on polyfilled browsers, 
    // wait for WebComponentsReady.
    document.addEventListener('WebComponentsReady', function() {
      var input = document.querySelector('paper-input');
      var button = document.querySelector('paper-button');
      var greeting = document.getElementById("greeting");
      button.addEventListener('click', function() {
        greeting.textContent = 'Hello, ' + input.value;
      });
    });
  </script>

</body>
