---
layout: page
title: Inicio
description: >
  O Forestry basicamente permite o gerenciamento de arquivos estáticos sem a necessidade de conhecimentos técnicos. Ideal para forcamos mais em nossa parte criativa e técnica.
hide_description: true
sitemap: false
---

O [Forestry](#entrar) basicamente permite o gerenciamento de arquivos estáticos sem a necessidade de conhecimentos técnicos. Ideal para forcamos mais em nossa parte criativa e técnica.


## Entrar

Primeiramente, certifique-se de que está logado no github do site ou tenha a senha para acessá-lo. Então vá para https://app.forestry.io/ ou clique aqui: [![Entrar no forestry][dtn]][forestry]

Selecione a opção **_log in with GitHub_**.
Prontinho, você está na página inicial.

Há uma opção chamada **meghna-hugo**, clique nela. É aqui que as alterações no site irão ocorrer. O que irá se mais frequente para se alterar/adicionar no site são os [artigos](#adicionando-artigos), os [autores](#adicionando-autor) e a [galeria de fotos](#galeria).

[forestry]: https://app.forestry.io/
[dtn]: https://assets.forestry.io/import-to-forestryK.svg

## Adicionando Artigos

Canto superior esquerdo, o Post(en), é onde deve ir para alterar ou adicionar um artigo. Ao clicar nessa opção, os artigos publicados serão dispostos em ordem de publicação. Acima deles há a opção **Create new**, para criar um novo artigo. Ao clicá-la, confirme a opção de _create a new document_. Adicione o título, a data, o autor, as imagens e a metadescrição -- esta é um resumo sobre o assunto do post, ao compartilhar o link do post será essa descrição que aparecerá abaixo do compartilhamento.

Sobre as imagens, pede-se para upar uma imagem no formato webp. Esse formato de imagem irá otimizar o carregamento do site, otimizando a compressão de imagens preservando uma qualidade melhor que o formato png e menos pesada que o jpg. Existem sites que convertem a imagem para o formato webp, por exemplo [para converter jpg em webp][convertio].

[convertio]: https://convertio.co/pt/jpg-webp/

Certo, entendi. Mas por que terei de upar dois formatos de imagens? Porque esse é um formato novo, nem todos os navegadores o aceitam, por isso vamos upar também um formato mais popular.

### Adicionando autor

If your existing site combines theme files with your content (as did previous verisons of Hydejack/PRO),
make sure to delete the following folders:

- `_layouts`
- `_includes`
- `_sass`
- `assets`

The `assets` folder most likely includes theme files as well as your personal/content files.
Make sure to only delete files that belong to the old theme!

## Galeria

If you want to build your site on [GitHub Pages][ghp], check out the [`gh-pages` branch][gpb] in the Hydejack Starter Kit repo.
For **PRO users**, find the `starter-kit-gh-pages` folder in the downloaded zip.

Note that Hydejack has a reduced feature set when built on GitHub Pages.
Specifically, using KaTeX math formulas doesn't work when built in this way.
{:.note}

[ghp]: https://jekyllrb.com/docs/github-pages/
[gpb]: https://github.com/hydecorp/hydejack-starter-kit/tree/gh-pages

### GH Pages + Free Version

For existing sites to use the _Free Version_, you can instead set the `remote_theme` key as follows:

```yml
# file: `_config.yml`
remote_theme: hydecorp/hydejack@v9.0.5
```

Make sure the `plugins` list contains `jekyll-include-cache` (create if it doesn't exist):

```yml
# file: `_config.yml`
plugins:
  - jekyll-include-cache
```

To run this configuration locally, make sure the following is part of your `Gemfile`:

```ruby
# file: `Gemfile`
gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
```

### GH Pages + PRO Version

For existing sites to use the _PRO Version_ several steps are necessary, because GitHub Pages does not support keeping theme files in a separate folder.

If it's possible, use the `starter-kit-gh-pages` in the downloaded zip.
It's often easier to copy your content into the starter kit than the reverse.

To use Hydejack PRO on GitHub Pages with an existing repository, copy the following files form `#jekyll-theme-hydejack` into the root of your repo.

- `_layouts`
- `_includes`
- `_sass`
- `assets`

You should also copy `_data` from either of the starter kits.

If possible, use the `_config.yml` from the starter kit. Otherwise do the following:

Make sure the `plugins` list contains `jekyll-include-cache` (create if it doesn't exist):

```yml
# file: `_config.yml`
plugins:
  - jekyll-include-cache
```

Make sure neither `theme` nor `remote_theme` is present.
For local testing make sure `math_engine` is set to `mathjax`.

Finally, copy the following (plugin) configurations:

```yml
# file: `_config.yml`
# Plugin Configs
# ---------------------------------------------------------------------------------------
optional_front_matter:
  remove_originals: true

readme_index:
  remove_originals: true
  with_frontmatter: true

relative_links:
  collections: true

titles_from_headings:
  strip_title: true
  collections: true

compress_html:
  comments: ["<!-- ", " -->"]
  clippings: all
  endings: all
  ignore:
    envs: [development]

sass:
  style: compressed
```

## Running locally

Make sure you've `cd`ed into the directory where `_config.yml` is located.
Before running for the first time, dependencies need to be fetched from [RubyGems](https://rubygems.org/):

```bash
$ bundle install
```

If you are missing the `bundle` command, you can install Bundler by running `gem install bundler`.
{:.note}

Now you can run Jekyll on your local machine:

```bash
$ bundle exec jekyll serve
```

and point your browser to <http://localhost:4000> to see Hydejack in action.

Continue with [Config](config.md){:.heading.flip-title}
{:.read-more}

[upgrade]: upgrade.md
