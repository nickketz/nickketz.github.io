This is Nick Ketz's personal academic/professional website, served at [nickketz.github.io](https://nickketz.github.io) via GitHub Pages.

## Site content

- `_pages/about.md` — bio and research interests (home page)
- `_pages/cv.md` — CV / research experience, education, awards, service
- `_pages/publications.md` — preprints, journal articles, conference proceedings, and patents
- `files/` — static files served at `/files/...` (resume PDF, etc.)
- `_config.yml` — site-wide settings (name, location, social links, etc.)
- `_sass/`, `assets/` — theme styles and static assets (Minimal Mistakes / academicpages theme, see below)

To update the resume, replace `files/nk_resume.pdf` — the link on the about page already points there, so no other changes are needed.

---

A Github Pages template for academic websites. This was forked (then detached) by [Stuart Geiger](https://github.com/staeiou) from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/), which is © 2016 Michael Rose and released under the MIT License. See LICENSE.md.

I think I've got things running smoothly and fixed some major bugs, but feel free to file issues or make pull requests if you want to improve the generic template / theme.

### Note: if you are using this repo and now get a notification about a security vulnerability, delete the Gemfile.lock file. 

# Instructions

1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Fork [this repository](https://github.com/academicpages/academicpages.github.io) by clicking the "fork" button in the top right. 
1. Go to the repository's settings (rightmost item in the tabs that start with "Code", should be below "Unwatch"). Rename the repository "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and create content & metadata (see below -- also see [this set of diffs](http://archive.is/3TPas) showing what files were changed to set up [an example site](https://getorg-testacct.github.io) for a user with the username "getorg-testacct")
1. Upload any files (like PDFs, .zip files, etc.) to the files/ directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.  
1. Check status by going to the repository settings, in the "GitHub pages" section
1. (Optional) Use the Jupyter notebooks or python scripts in the `markdown_generator` folder to generate markdown files for publications and talks from a TSV file.

See more info at https://academicpages.github.io/

## To run locally (not on GitHub Pages, to serve on your own computer)

macOS ships a Ruby that can't build native gem extensions and isn't on `PATH` by default, so use [rbenv](https://github.com/rbenv/rbenv) to install a real Ruby:

```
brew install rbenv ruby-build
rbenv init   # follow its printed instructions to hook into your shell, then restart your terminal
rbenv install 3.2.4
cd nickketz.github.io
rbenv local 3.2.4
gem install bundler
bundle config set path 'vendor/bundle'
bundle install
```

If `bundle install` fails because `Gemfile.lock` was generated with an old Bundler version incompatible with your Ruby, delete `Gemfile.lock` and run `bundle install` again — this only affects your local lockfile, not what GitHub Pages builds.

Then serve the site:

```
LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 bundle exec jekyll serve
```

Open `http://localhost:4000`. The server watches for file changes and rebuilds/reloads automatically.

The `LANG`/`LC_ALL` prefix works around a bug in the old `sass` gem this theme depends on: without a UTF-8 locale set, it misreads valid file encodings as invalid and the build fails with `Invalid US-ASCII character` errors.

# Changelog -- bugfixes and enhancements

There is one logistical issue with a ready-to-fork template theme like academic pages that makes it a little tricky to get bug fixes and updates to the core theme. If you fork this repository, customize it, then pull again, you'll probably get merge conflicts. If you want to save your various .yml configuration files and markdown files, you can delete the repository and fork it again. Or you can manually patch. 

To support this, all changes to the underlying code appear as a closed issue with the tag 'code change' -- get the list [here](https://github.com/academicpages/academicpages.github.io/issues?q=is%3Aclosed%20is%3Aissue%20label%3A%22code%20change%22%20). Each issue thread includes a comment linking to the single commit or a diff across multiple commits, so those with forked repositories can easily identify what they need to patch.
