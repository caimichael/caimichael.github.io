# Documentation

## 2026-07-03

- Milestone: revise homepage contact information.
- Success criteria: homepage contact sentence includes the Rutgers office address and a less directly scrapable email format.
- Decision: kept the email readable for humans while replacing the literal address in `index.md` with `michael [at] michaelcai [dot] com`; this is a lightweight spam-reduction measure, not a guarantee against modern scrapers.
- Validation: `bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders the Room 415 contact sentence with `michael [at] michaelcai [dot] com`.
- Deviations/blockers: none.

- Milestone: remove lower footer identity/contact banner.
- Success criteria: rendered pages no longer include the Minima footer block repeating the site title, email, Twitter handle, or GitHub handle.
- Decision: added a local `_includes/footer.html` override that emits no footer content, instead of removing metadata from `_config.yml`.
- Validation: `bundle exec jekyll build` completed successfully. Confirmed `_site/research/index.html` ends without the Minima footer block and rendered pages no longer include `michael@michaelcai.com`, `michaeldcai`, or the lower `caimichael` handle.
- Deviations/blockers: none.

- Milestone: restore research-page abstract spacing.
- Success criteria: abstract toggle styles are compiled into the loaded Jekyll stylesheet, and paper entries get consistent spacing after abstract blocks.
- Decision: moved the abstract styling into `assets/main.scss`, the Jekyll asset entrypoint that produces `/assets/main.css`. The previous `assets/css/main.scss` file was only copied to `_site/assets/css/main.scss` and was not loaded by the research page.
- Validation: `bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` contains the compiled abstract button and `.post-content details` spacing rules.
- Deviations/blockers: none.
