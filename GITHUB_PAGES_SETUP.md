# GitHub Pages With Custom Domain `thk-ai.de`

This repository is published with GitHub Pages and should be reachable at:

- `https://thk-ai.de/`

## 1. DomainFactory: Domain-Einstellungen

Set the domain to use DNS entries managed in `Nameserver-Einstellungen`.

- Keep nameserver at DomainFactory default (unless you deliberately moved DNS to another provider).
- Do not use URL forwarding for `thk-ai.de` to GitHub Pages.
- Web/mail services can remain active for mail records (MX/CNAME mail hostnames).

## 2. DomainFactory: Nameserver-Einstellungen (DNS Zone)

Replace the current website records that point to `139.6.56.127`.

### Required records for apex (`thk-ai.de`)

Create/keep these records for `thk-ai.de`:

- `A` -> `185.199.108.153`
- `A` -> `185.199.109.153`
- `A` -> `185.199.110.153`
- `A` -> `185.199.111.153`
- `AAAA` -> `2606:50c0:8000::153`
- `AAAA` -> `2606:50c0:8001::153`
- `AAAA` -> `2606:50c0:8002::153`
- `AAAA` -> `2606:50c0:8003::153`

### Optional but recommended `www`

Create:

- `www` `CNAME` -> `thk-ai.github.io`

This lets `https://www.thk-ai.de` work and redirect to the primary domain configured in GitHub.

### Records to remove or change

- Remove `thk-ai.de A 139.6.56.127`
- Remove `*.thk-ai.de A 139.6.56.127` (wildcard A to old host)
- Remove default placeholder `AAAA` entries for `thk-ai.de` and `*.thk-ai.de` if they are not the GitHub IPv6 addresses above.

### Records to keep unchanged

- Keep existing mail-related records (MX and CNAME like `imap`, `smtp`, `webmail`, etc.).

## 3. GitHub Repository Settings (Pages)

In GitHub repository `thk-ai/thk-ai`:

1. Open `Settings -> Pages`.
2. Under `Build and deployment`, keep your existing publishing source (typically `GitHub Actions` for Quarto, or `gh-pages` branch if used).
3. In `Custom domain`, enter `thk-ai.de` and save.
4. Enable `Enforce HTTPS` after DNS is valid and certificate is issued.

GitHub will create/use a `CNAME` file during deployment for the custom domain.

## 4. Quarto configuration in this repo

`_quarto.yml` should use:

- `website.site-url: https://thk-ai.de/`

This is already configured.

## 5. Verification checklist

After DNS changes (can take minutes to 24h depending on TTL):

1. `dig +short thk-ai.de A` returns the four GitHub IPv4 addresses.
2. `dig +short thk-ai.de AAAA` returns the four GitHub IPv6 addresses.
3. `dig +short www.thk-ai.de CNAME` returns `thk-ai.github.io.` (if configured).
4. `https://thk-ai.de/` opens the GitHub Pages site.
5. In GitHub Pages settings, certificate status is active and `Enforce HTTPS` stays enabled.

## 6. Notes on current state

Current DNS points web traffic to `139.6.56.127` (old hosting). That must be removed/replaced for GitHub Pages to answer for `thk-ai.de`.
