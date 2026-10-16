# Geneticode Lab

Website for [Geneticode Lab](https://geneticode.org), built with Jekyll so it can be published by GitHub Pages.

The lab name and tagline are **Geneticode Lab** and **Decoding genetic codes, mapping biological functions**. Pages: Home, Research, People, Publications, News, and Contact.

This repository uses only [plugins GitHub Pages allows](https://pages.github.com/versions/) (`jekyll-seo-tag`, `jekyll-sitemap`, `jekyll-feed`) and a layout that lives in the repo. The built-in Pages Jekyll builder can publish it. A custom GitHub Actions workflow is not required unless you add a plugin or theme that is not on that list.

## Edit content

Most text that changes often is in `_data/`. Markdown pages hold the page title and a short introduction. Rebuild or push to `main` and the site picks up the edits. No HTML change is required for a new person, paper, or news item.

| What | Where |
| --- | --- |
| Intro, email, GitHub, affiliation, address | [`_data/lab.yml`](_data/lab.yml) |
| Navigation labels | [`_data/navigation.yml`](_data/navigation.yml) |
| Members (`photo`, `name`, `role`, `links`) | [`_data/members.yml`](_data/members.yml) |
| Research cards | [`_data/research.yml`](_data/research.yml) |
| Publications, grouped by `year` | [`_data/publications.yml`](_data/publications.yml) |
| News items for the home page and News page | [`_data/news.yml`](_data/news.yml) |
| Longer news write-ups | [`_posts/`](_posts/) |
| Page titles and ledes | `index.html`, `research.md`, `people.md`, `publications.md`, `news.md`, `contact.md` |

### People

Each person in `_data/members.yml` uses:

- `name` and optional `name_zh`
- `role` (and optional Chinese `role_zh`)
- `photo`: root-relative path such as `/assets/images/people/dong-wang.jpg`, or empty for an initials avatar
- `links`: a list of `label` / `url` pairs (homepage, mailto, GitHub, and so on)
- `pi: true` for the principal investigator, who is shown first
- `placeholder: true` to show a dashed “Placeholder · 占位” card

Put portrait files in `assets/images/people/`. JPG, PNG, and WebP all work.

Dong Wang（王东）, Assistant Professor, is listed with [https://dwang.net](https://dwang.net) and `csdwang@ncepu.edu.cn`. The second card is a marked placeholder so the fields are visible; replace or delete it.

### Publications

Add a record to `_data/publications.yml`. The Publications page groups entries by `year`, newest year first. A commented template sits at the bottom of the file.

Useful fields: `title`, `authors`, `corresponding`, `year`, `venue`, `details`, `doi`, `url`, `code`, `pdf`, `citation`. Set `highlight: true` to feature a paper on the home page.

The 2026 S2DA-GO paper (Frontiers in Genetics, doi:10.3389/fgene.2026.1880976) is included from the public record. SpaSem has public code but no citation on the site yet; add one here when you have it.

### News

Two ways to post news:

1. Add an entry to `_data/news.yml` (`date`, `title`, `summary`, optional `title_zh` / `summary_zh` / `url`). These entries show on the home page and the News page.
2. Add `YYYY-MM-DD-slug.md` under `_posts/` for a longer note. Set the data entry’s `url` to the post permalink (for example `/news/s2da-go-published/`) to link them. A post with no data entry still appears on the News page, but not on the home page.

### Affiliation

`_data/lab.yml` holds the affiliation block. The university name is **North China Electric Power University / 华北电力大学 (NCEPU)**. That wording comes from the `ncepu.edu.cn` email domain and from public author affiliations on the S2DA-GO paper. Confirm it and replace the department and postal address, which are still marked placeholders. The Contact page repeats this note in English and Chinese.

### Chinese and English

Chinese is stored next to English in the data files (`title_zh`, `summary_zh`, `name_zh`, and similar). The layout tags those strings with `lang="zh-Hans"`. The type uses Source Sans 3 / Source Serif 4 for Latin text and Noto Sans SC / Noto Serif SC for Chinese, with common system CJK fonts as fallbacks (PingFang SC, Microsoft YaHei, Noto Sans CJK, Songti).

The Chinese tagline in `_data/lab.yml` (`解码遗传密码，刻画生物学功能`) is an editable rendering of the English tagline. Change it there if you want different wording.

## Preview locally

Requirements: Ruby and Bundler. GitHub Pages currently builds with Jekyll 3.10 (see the versions page linked above). This `Gemfile` pins `github-pages` 232 so the local build matches that environment.

```bash
bundle install
bundle exec jekyll build
bundle exec jekyll serve
```

Then open [http://127.0.0.1:4000/](http://127.0.0.1:4000/).

`baseurl` in `_config.yml` is empty because the custom domain serves the site at the root of `https://geneticode.org`. If you need the site to work at the project URL `https://geneticodelab.github.io/index/` before the domain is attached, set `baseurl: "/index"` temporarily, preview, and set it back to `""` before relying on the custom domain.

## GitHub Pages

1. On GitHub, open **geneticodelab/index → Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Branch: `main`. Folder: `/ (root)`. Save.
4. Under **Custom domain**, enter `geneticode.org`. This repository already contains a `CNAME` file whose only line is `geneticode.org`. Saving the setting in Pages should match that file. Do not add a second host in `CNAME`.
5. Wait until Pages reports the site as published and DNS as checked. Then turn on **Enforce HTTPS**.

The first project URL, before the custom domain works, is `https://geneticodelab.github.io/index/`. After the custom domain is active, use `https://geneticode.org`.

Leave the Pages source on the classic Jekyll builder. Do not add a `.nojekyll` file. If you later add a plugin or theme that is not on the [allowlist](https://pages.github.com/versions/), switch the source to **GitHub Actions** and add a Pages workflow. Until then, Actions is unnecessary.

## Custom domain on Cloudflare

DNS for `geneticode.org` should point at GitHub Pages. In the Cloudflare dashboard for the zone, add these records.

**Apex (`geneticode.org`, name `@`) — A**

| Type | Name | Content | Proxy |
| --- | --- | --- | --- |
| A | `@` | `185.199.108.153` | DNS only, while the certificate is issued |
| A | `@` | `185.199.109.153` | DNS only, while the certificate is issued |
| A | `@` | `185.199.110.153` | DNS only, while the certificate is issued |
| A | `@` | `185.199.111.153` | DNS only, while the certificate is issued |

**Apex — AAAA**

| Type | Name | Content |
| --- | --- | --- |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

**www**

| Type | Name | Content |
| --- | --- | --- |
| CNAME | `www` | `geneticodelab.github.io` |

The CNAME target is the GitHub Pages host for the organization. It is not a path such as `geneticodelab.github.io/index`. GitHub routes the custom domain to whichever repository has `geneticode.org` configured.

Recommended Cloudflare SSL/TLS mode: **Full**. After GitHub has issued a certificate and `https://geneticode.org` loads, you can move to **Full (strict)**.

Proxy notes:

- Leave the records on **DNS only** (grey cloud) until GitHub Pages finishes provisioning the certificate and **Enforce HTTPS** succeeds. An orange-cloud proxy can block that HTTP challenge.
- Do **not** use SSL mode **Flexible**. GitHub Pages redirects HTTP to HTTPS, and Flexible terminates HTTPS at Cloudflare while talking HTTP to the origin, which produces a redirect loop.
- After HTTPS works, the orange-cloud proxy is optional. If you turn it on, keep SSL at **Full** or **Full (strict)**.
- Avoid extra Cloudflare redirect rules that also force HTTPS until you have confirmed the site loads. One redirect (GitHub’s) is enough at the start.

GitHub’s current addresses are documented in [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). If GitHub publishes new addresses, update the apex records to match.

## Repository layout

```
_config.yml          Site title, URL, plugins
_data/               Editable YAML
_layouts/            HTML shells
_includes/           Header, footer, cards
_posts/              Long-form news
assets/css/main.css  Styles
assets/images/       Logo and member photos
CNAME                Custom domain
```
