### Minimal Reset CSS

````css
html{box-sizing: border-box; font-size: 16px;}
*, *:before, *:after {box-sizing: inherit;}
body, h1, h2, h3, h4, h5, h6, p, ol, ul {margin: 0;padding: 0;font-weight: normal; }
ol, ul {list-style: none;}
img {max-width: 100%;height: auto; }
````

### Styles Structure
````
├── /base
│  ├── _core.scss
│  ├── _colors.scss
│  ├── _settings.scss
│  └── _typography.scss
├── /utils
│  ├── _animations.scss
│  ├── _easings.scss
│  ├── _grid.scss
│  └── _misc.scss
├── /components
│  ├── _header.scss
│  ├── _footer.scss
│  ├── _button.scss
│  └── _sidebar.scss
└── main.scss
````

#### main.scss
````scss
// *** Vendor ***
@import 'sanitize.css';

// *** Settings ***
@import './base/settings';
@import './base/colors';

// *** Utils ***
@import './utils/easings';
@import './utils/animations';
@import './utils/grid';
@import './utils/ui';

// *** Base ***
@import './base/core';
@import './base/typography';

// *** Components ***
@import './components/header';
@import './components/footer';
@import './components/button';
@import './components/sidebar'
````
