# Andrea Gao's Personal Website

This repository contains the source code for my personal website, hosted at [gytcrt.github.io](https://gytcrt.github.io).

## Overview

This website is built using [Jekyll](https://jekyllrb.com/) and based on the Hydejack theme, a two-column layout optimized for both desktop and mobile viewing. It showcases my blog posts, projects, and resume.

## Features

* Responsive design with mobile-friendly navigation
* Blog posts organized by tags
* Project portfolio 
* Resume section
* Social media integration (GitHub, LinkedIn, Instagram, Twitter)
* Comments powered by Disqus
* Mathematical notation support via KaTeX/MathJax

## Local Development

To run this site locally:

1. Install Jekyll and dependencies:
   ```
   gem install jekyll bundler
   bundle install
   ```

2. Run the development server:
   ```
   bundle exec jekyll serve
   ```

3. Visit `http://localhost:4000` in your browser

## Content Structure

* Blog posts are stored in the `_posts` directory
* Site configuration is managed in `_config.yml`
* Tags are defined in `_data/tags.yml`

## License

This project is licensed under the terms included in the [LICENSE.md](LICENSE.md) file.
