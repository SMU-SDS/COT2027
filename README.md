# CoTS 2027 website

Source for <https://smu-sds.github.io/cots2027/>, the site for the Conference of
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

Optional. With Ruby installed:

```
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>.

## Publishing

1. Create a public repository named `cots2027` in the SMU-SDS organization and
   push this folder to the `main` branch.
2. In the repository, go to Settings, then Pages.
3. Under Build and deployment, set Source to "Deploy from a branch", branch
   `main`, folder `/ (root)`.
4. The site appears at <https://smu-sds.github.io/cots2027/> within a minute or
   two.

`baseurl` in `_config.yml` must match the repository name. It is set to
`/cots2027`. If the site later moves to a repository named
`smu-sds.github.io`, set `baseurl: ""` instead.

## Custom domain

If SMU provides a subdomain later, add it under Settings, then Pages, then
Custom domain. GitHub writes a `CNAME` file to the repository, SMU IT adds a DNS
CNAME record pointing to `smu-sds.github.io`, and GitHub issues a certificate
once the record resolves. Then set `url:` to the new address and `baseurl: ""`
in `_config.yml`, since a custom domain serves the site at the root.
