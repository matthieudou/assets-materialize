## Setup

Ensure you have the following gems in your Rails `Gemfile`

```ruby
# Gemfile
gem 'materialize-sass'
gem 'font-awesome-sass'
gem 'simple_form-materialize'
gem 'autoprefixer-rails'
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
