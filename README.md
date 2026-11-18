# Learn Oracle

Interactive, offline learning dashboards about Oracle: ORDS, APEX and the database.
They are published as part of the Learning Lab at
**https://learn.prabidhis.com/#/** under **Oracle**.

This repo holds only the Oracle pages. The Lab itself (menu, design, theme and the
website) lives in [learn-simulation-dashboard](https://gitlab.com/Prabidhi/learn-simulation-dashboard).

## How it reaches the website

1. You push to `main` here.
2. This repo's pipeline checks every page's security policy, then asks the Lab's
   pipeline to rebuild.
3. The Lab's build copies these files into `oracle/` on the site and adds the
   entries in `pages.json` to its menu.

So a page at `ords/ords-403-explained.html` here is served at
`https://learn.prabidhis.com/oracle/ords/ords-403-explained.html`.

## Adding a page

1. Add the `.html` file in the folder matching its place in the menu
   (`ords/`, `apex/`, or a new one).
2. Add an entry to `pages.json`. `href` is the path from this repo's root.
   `section` is `Oracle`, and `topic` picks the sub-menu (`ords`, `apex`, ...).
3. Refresh the page's security policy with the Lab's script:

   ```bash
   python3 ../learn-simulation-dashboard/scripts/update_csp.py --root .
   ```

4. Preview it inside the Lab before pushing:

   ```bash
   cd ../learn-simulation-dashboard
   python3 scripts/build_site.py --local oracle=../learn-oracle
   python3 -m http.server -d public 8000
   ```

Pages follow the rules in the Lab's
[LEARNING_DASHBOARD_GUIDE.md](https://gitlab.com/Prabidhi/learn-simulation-dashboard/-/blob/main/LEARNING_DASHBOARD_GUIDE.md):
one self-contained file, no network calls, the three Lab themes, and public data only.

## Copies

GitLab is the main copy. A copy is kept at
[github.com/Prabidhi/learn-oracle](https://github.com/Prabidhi/learn-oracle).
