# COTS 2027 website

Source for <https://smu-sds.github.io/COTS2027/>, the site for the Conference of
Texas Statisticians hosted by SMU.

Built with Jekyll, which GitHub Pages compiles automatically on every push. No
build step or GitHub Actions workflow is needed.

## Repository layout

```
_config.yml            site title, dates, contact email, URL
_data/navigation.yml   the menu bar
_layouts/default.html  page shell used by every page
assets/css/style.css   all styling
assets/img/campus.svg  illustrated campus skyline used behind the headers
index.md               home page
pages/                 program, speakers, registration, venue, sponsors, organizers
```

## Editing

- Conference dates, email address, and site title live in `_config.yml`. Set
  `dates:` once the date is fixed and every page picks it up.
- To edit a page, open the `.md` file and change the text below the front matter.
  Markdown headings, lists, links, and tables all work.
- To add a page, copy an existing file in `pages/`, change `title` and
  `permalink`, then add an entry to `_data/navigation.yml`.
- Registration and poster links go in `pages/registration.md`. HTML comments in
  that file mark the two spots.
- Speakers go in `pages/speakers.md` and sponsors in `pages/sponsors.md`, each
  with a commented template block.
- Edits can be made in the browser through the GitHub web editor, or locally with
  git.

## Using real photos

The headers use a drawn campus illustration, `assets/img/campus.svg`, so nothing
needs to be licensed. To swap in a photograph, drop a wide image such as
`assets/img/campus.jpg` into that folder and uncomment `hero_image:` in
`_config.yml`. A single page can override it with `background:` in its front
matter. Aim for roughly 2000 pixels wide, and keep the subject away from the
center since text sits there.

Photos of campus belong to SMU or to the photographer, so ask SMU Marketing and
Communications for permission before posting one, or use an image with a Creative
Commons license and credit it in the footer.

## Previewing locally

Jekyll runs on Ruby. On Ubuntu, install it once:

```
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install jekyll bundler
```

Then, from this folder:

```
bundle install
bundle exec jekyll serve --livereload --baseurl ""
```

Open <http://localhost:4000>, which is the same address as
<http://127.0.0.1:4000>. Stop the server with Ctrl+C. `bundle install` is needed
only the first time and after the Gemfile changes, so later sessions are just the
serve line.

Notes:

- `--baseurl ""` overrides the deployed `/COTS2027` path so the local site sits
  at the root. Without it, the preview lives at
  <http://localhost:4000/COTS2027/>.
- Markdown pages and the stylesheet rebuild on save, and `--livereload`
  refreshes the browser.
- Changes to `_config.yml` need a restart with Ctrl+C and the same serve command.
- Jekyll uses port 4000 and Hugo uses 1313, so a Hugo site can serve at the same
  time. Add `--port 4001` only if another Jekyll site is already running.
- "no acceptor (port is in use)" comes from LiveReload on port 35729, usually an
  earlier server still running. Drop `--livereload`, or add
  `--livereload-port 35730`.
- Do not name a setting `host` in `_config.yml`. Jekyll reserves it for the
  server address, and the site name goes in `institution` instead.
