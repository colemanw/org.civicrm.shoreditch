# org.civicrm.shoreditch (developmental)

The "Shoreditch" extension is a theme for CiviCRM based on a contemporary [flat design](https://en.wikipedia.org/wiki/Flat_design) and
[Bootstrap(S)CSS](http://getbootstrap.com/css/).  It includes two major components:

 * "`bootstrap.css`" is a build of Bootstrap based on the standard Bootstrap style-guide. It can be used with other CiviCRM extensions which satisfy the Bootstrap style-guide.
 * "`custom-civicrm.css`" is an optional replacement for "civicrm.css". It uses the same visual conventions and SCSS metadata, but it applies to existing core screens.

> This extension is under **active development**. Significant elements may change.

## Using `bootstrap.css`

This extension provides the CSS for Bootstrap.  Other extensions should output compliant HTML, e.g.

```html
<div id="bootstrap-theme">
  ...
  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 class="panel-title">Hello World</h3>
    </div>
    <div class="panel-body">
      This is the Hello World example.
    </div>
  </div>
  ...
</div>
```

Note the use of `id="bootstrap-theme"`.  To avoid conflicts with CMS UIs, the CSS rules are
restricted to `#bootstrap-theme`.

## Using `custom-civicrm.css`

This extension includes an optional file `custom-civicrm.css` which can replace the default
`civicrm.css`.  This uses the same CSS classes as traditional CiviCRM screens, but the
look-and-feel matches the Bootstrap look-and-feel.  It is implemented with the same SCSS variables
and mixins. To use it, figure out the URL for the CSS file:

```
cv url -x shoreditch/css/custom-civicrm.css
```

And then put this URL in the setting `customCSSURL`, e.g.

```
cv api setting.create customCSSURL=$(cv url -x shoreditch/css/custom-civicrm.css --out=list)
```

## Build

If you are doing development on this extension, then you may need to build
new CSS files. This requires the toolchain for SCSS=>CSS compilation.
Install [NodeJS](https://nodejs.org/) and then run:

```
npm install -g gulp
npm install
```

Once you have the tools, you can run `gulp`. This will monitor the SCSS
files and automatically recompile whenever they change.

```
gulp
```
