## Setup

Ensure you have the following gems in your Rails `Gemfile`

```ruby
# Gemfile
gem 'materialize-sass'
gem 'font-awesome-sass'
gem 'simple_form-materialize'
gem 'autoprefixer-rails'
```

In your terminal, generate SimpleForm Bootstrap config.

```shell
$ bundle install
$ rails generate simple_form:install --bootstrap
```

Then replace Rails' stylesheets by this stylesheets:
```shell
$ rm -rf app/assets/stylesheets
$ curl -L https://github.com/matthieudou/assets-materialize/archive/master.zip > stylesheets.zip
$ unzip stylesheets.zip -d app/assets && rm stylesheets.zip && mv app/assets/assets-materialize-master app/assets/stylesheets
```

Don't forget the sprockets directives in assets/javascripts/application.js

```shell
// app/assets/javascripts/application.js

//= require jquery
//= require jquery_ujs
//= require materialize
//= require materialize/extras/nouislider
//= require_tree .
```

And the viewport in the layout
```html
<!-- app/views/layouts/application.html.erb -->
<head>
  <!-- Add these line for detecting device width -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
</head>
```


## Adding new `.scss` files

Look at your main `application.scss` file to see how SCSS files are imported.


For every folder (**`components`**, **`layout`**, **`pages`**, **`vendor`**), there is one `_index.scss` partial which is responsible for importing all the other partials of its folder.

**Example 1**: Let's say you add a new `_contact.scss` file in **`pages`** then modify `pages/_index.scss` as:

```scss
// pages/_index.scss
@import "home";
@import "contact";
```

**Example 2**: Let's say you add a new `_sidebar.scss` file in **`layout`** then modify `layout/_index.scss` as:

```scss
// layout/_index.scss
@import "base";
@import "utilities";
@import "footer";
@import "navbar";
@import "sidebar";
```
