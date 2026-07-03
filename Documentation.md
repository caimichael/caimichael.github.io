# Documentation

## 2026-07-03

- Milestone: refine body typography.
- Success criteria: ordinary body and navigation text use a more distinctive readable sans-serif without adding an external font dependency.
- Decision: introduced a `$body-font` stack preferring `Avenir Next`/`Avenir`, with Helvetica/Arial fallbacks, and applied it through the existing body font rule.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` compiles the Avenir-first body font stack while preserving the existing serif rules for site title, section headings, homepage lead text, and paper titles.
- Deviations/blockers: none.

- Milestone: refine research item formatting and header spacing.
- Success criteria: Work in Progress paper title uses the same title styling as other research entries, desktop header has more balanced vertical spacing, and nav links are larger.
- Decision: added the `.paper-title` class to the Work in Progress entry and overrode Minima's desktop header float/line-height behavior with an explicit flex layout, larger nav text, and more vertical padding.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/research/index.html` renders the Work in Progress item with `class="paper-title"` and `_site/assets/main.css` contains the larger header/nav font sizes plus the desktop flex header spacing rules.
- Deviations/blockers: none.

- Milestone: align visual palette with profile photo.
- Success criteria: replace the burgundy/beige visual language with a cooler blue-green palette that better matches the profile photo while preserving the recent layout and typography improvements.
- Decision: changed the central Sass color tokens to slate ink, blue accent links/rules, muted green bullet markers, pale blue page background, and blue-tinted image shadow. Replaced the block pseudo-element nav underline with a desktop flex nav and simple border underline after it caused awkward header spacing.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` contains the new blue-green palette tokens, no longer contains the prior burgundy/beige tokens, and uses the fixed desktop flex nav/border underline rules instead of the block pseudo-element underline.
- Deviations/blockers: none.

- Milestone: make the site visual design less generic.
- Success criteria: default Minima blue-link/basic-header feel is replaced with a more distinctive palette, typography, header treatment, research-entry styling, and the large stock page titles are removed from the top of the Research and Teaching pages.
- Decision: kept the existing Jekyll/Minima structure, but added a warmer page background, burgundy accent links, serif headings/paper titles, refined navigation hover states, custom abstract toggles, and hid `.post-title` to remove the oversized generated page headers.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` contains the new palette, typography, header, title-hiding, and abstract-button rules; confirmed `_site/research/index.html` and `_site/teaching/index.html` still generate page metadata while relying on `.post-title` styling to hide the oversized visible page titles.
- Deviations/blockers: none.

- Milestone: correct work-in-progress paper title capitalization.
- Success criteria: the research page uses standard title case for the parenthetical phrase in `When Lagged Observables Can (and Should) Be Used as Instruments`.
- Decision: lowercased the coordinating conjunction `and` inside the parenthetical while leaving the rest of the title in title case.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/research/index.html` renders the title as `When Lagged Observables Can (and Should) Be Used as Instruments`.
- Deviations/blockers: none.

- Milestone: revise homepage research-interest blurb.
- Success criteria: homepage introduction states appointment, lists research interests as bullets, and presents software contributions without a separate Software heading.
- Decision: used a short paragraph plus bullet list in `index.md`, preserving the existing software links as secondary text.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders the research-interest bullet list and no `Software` heading.
- Deviations/blockers: none.

- Milestone: refactor site presentation.
- Success criteria: homepage uses responsive image and clearer intro/software/contact sections; research entries use shared classes instead of inline spacing; generated local files are ignored.
- Decision: kept the Minima theme and existing content, but moved visual presentation into `assets/main.scss` and added lightweight academic-site hierarchy rather than a more decorative redesign.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html`, `_site/research/index.html`, and `_site/assets/main.css` contain the new homepage/research classes and no research-page inline spacing styles.
- Deviations/blockers: none.

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
