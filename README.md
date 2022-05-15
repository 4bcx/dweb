# dweb - Dumb static WEbsite Builder

## Preface
After many years of starting blogs and never use them because of how they just don't seem right, I decided that I'll write my own static site generator. After all, I just need a static site generator that I understand the underlying mechanics of it without having to learn a whole new framework to be able to maintain it. [Jes Olson](https://j3s.sh/) wrote [an article](https://j3s.sh/thought/my-website-is-one-binary.html) that describes my motive better. The only difference is that I really *really* like writing these ~~stupid~~ simple programs in portable shell scripts.

I started this by writing a few loops in a [.gitlab-ci.yml](https://gitlab.com/4bcx/4b.cx/-/blob/851550a6b3a28c70242ff11981e237dff7938503/.gitlab-ci.yml) since I decided I'd be using [GitLab pages](https://pages.gitlab.io/) and it grew to this 300+ lines script that could be used with any static site host.

## Usage & example
I'll write this properly later I promise, but this should do for now.

```
Dumb static WEbsite Builder

Usage: ./dweb [build] [-e KEY[=VALUE]...] [-f CONFIG_FILE]
       ./dweb serve [-e KEY[=VALUE]...] [-f CONFIG_FILE]
       ./dweb config [-e KEY[=VALUE]...] [-f CONFIG_FILE]
       ./dweb -h | -v
Builds or serves a static website from esht templates.

Commands:
  build                         build the website (default action)
  serve                         launch a lightweight webserver
  config                        write configuration to file

Options:
  -h, --help                    display this help text and exit
  -v, --version                 print version and exit
  -e, --env KEY[=VALUE]...      define variable KEY
  -f, --config-file FILE        use configuration from FILE

Variables and defaults:
  SITE_TITLE                    default site title
                                  default: 'example'
  SITE_URL                      site root url
                                  default: 'example.com'
  SITE_DESC                     default description used in meta tags
  SITE_IMAGE                    default image used in meta tags
  SITE_INDEX                    file to symlink to index.html
  SOURCE_DIR                    content directory
                                  default: './src'
  PARTS_DIR                     parts and templates directory
                                  default: './prt'
  BUILD_DIR                     output directory
                                  default: './out'
  TEMP_DIR                      temporaty directory
                                  default: './tmp'
  INCLUDES_DIR                  static files directory
                                  default: './inc'
  MAPPER_FILE                   mapper file to include
                                  default: './map'
  ESHT_SCRIPT                   esht executable
                                  default: './lib/esht/esht'
  MARKDOWN_EXT                  markdown files extension
                                  default: 'md'
  MARKDOWN_BIN                  markdown parsing executable
                                  default: 'markdown'
  MAIN_TEMPLATE                 default main template filename
                                  default: 'main.html.esht'
  META_EXT                      default meta files extension
                                  default: 'meta'
  SERVE_BIN                     webserver command
                                  default: 'httpd -f -v -p 8000'

Variables precedence:
  1. Variables supplied using -e or --env options
  2. Variables in configuration file or ./cfg file if found
  3. Environmental variables exported brior to running ./dweb
  4. Default values below

Meta files:
  Meta files contain useful metadata required for each page
much like JSON or YAML frontmatter used in other static site
generators. They must be in the same directory as the page
source file and with the same name but with .meta or the defined
META_EXT appended to it. Generally the variables defined
in the meta file are used by esht templates.

Dependencies:
  esht          REQUIRED        to process the templates
  git           OPTIONAL        automatically get creation dates
                                  update dates and author of pages
  discount      OPTIONAL        provides default markdown processor
  darkhttpd     OPTIONAL        default webserver
```

## TODO
- [ ] Write proper README
- [ ] Add example and fallback templates
- [ ] Use [imgg](https://gitlab.com/4bcx/imgg) to generate cover pictures
- [ ] Better handling of files types
- [ ] Write more test inputs to detect edge cases
- [ ] Write proper documentation

## Credits
- [darkhttpd](https://unix4lyfe.org/darkhttpd/) by [Emil Mikulic](https://unix4lyfe.org/) is an optional dependency for **dweb** and is published under [ISC License](https://github.com/emikulic/darkhttpd/blob/master/COPYING)
- [CHANGELOG](./CHANGELOG.md) format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
- This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
- And I try my best to follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [.gitignore](./.gitignore) was generated using [gitignore.io](https://www.toptal.com/developers/gitignore)

## License
This project is licensed under [The Unlicense](./LICENSE)
