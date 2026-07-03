# Documentation

## 2026-07-03

- Milestone: convert Teaching metadata to field lists.
- Success criteria: Teaching entries expose Role and Rating fields where applicable, course/workshop links live in their own fields, NBER lists co-teachers as a field, and the page remains visually lightweight.
- Decision: replaced teaching metadata paragraphs with responsive definition-list fields for `Role`, `Course` or `Workshop`, `Rating`, and `Co-taught with`, reusing muted label styling to keep the page compact.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/teaching/index.html` renders separate `Role`, `Course` or `Workshop`, `Rating`, and `Co-taught with` fields in `teaching-fields` definition lists, and `_site/assets/main.css` contains responsive field-list styling.
- Deviations/blockers: none.

- Milestone: lighten Teaching page structure on refactor branch.
- Success criteria: Teaching entries are more compact and scannable, ratings and resources read as lighter metadata, and topic lists are introduced by short labels instead of full-weight prose.
- Decision: rewrote the Teaching page entries into compact role/rating/resource lines, added `Selected topics` labels, and added small muted CSS classes for teaching metadata, labels, and resource links.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/teaching/index.html` renders compact `teaching-meta`, `teaching-label`, and `teaching-resource` entries, and `_site/assets/main.css` contains the new muted teaching styles.
- Deviations/blockers: none.

- Milestone: explore restrained site-wide visual polish on refactor branch.
- Success criteria: research entries have clearer hierarchy, links feel more deliberate, content has a little more breathing room, the profile photo treatment is quieter, and mobile/header spacing remains coherent.
- Decision: widened the wrapper slightly, refined link underline behavior, added a subtle left rule and metadata color treatment to research entries, aligned abstract spacing with the entry rule, softened the profile photo shadow, and added small mobile overrides for title/nav/research spacing.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` contains the wider wrapper, refined link underline rules, subtle research-entry left rule, softer photo shadow, and mobile spacing overrides.
- Deviations/blockers: none.

- Milestone: soften homepage contact labels.
- Success criteria: Contact field labels remain visually distinct while feeling less like all-caps product UI.
- Decision: kept the contact definition-list layout, but changed labels to title-case styling with muted color, normal letter spacing, no uppercase transform, and a modest medium weight.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` compiles contact labels at `0.92rem`, medium weight, normal letter spacing, and no uppercase transform.
- Deviations/blockers: none.

- Milestone: tighten homepage contact layout.
- Success criteria: the Contact section sits closer to the open-source project list and the contact fields are visually distinct without bold labels.
- Decision: moved Contact into the homepage copy flow after the software list, reduced the section spacing, and replaced bold/plain contact lines with a lightweight definition-list layout using small muted uppercase labels.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders Contact inside the homepage copy after the open-source project list, and `_site/assets/main.css` includes the tighter Contact spacing plus normal-weight muted uppercase contact labels.
- Deviations/blockers: none.

- Milestone: soften header and page background contrast.
- Success criteria: the site uses the selected subtle blue-gray Option 1 pairing for body and header backgrounds while preserving the existing accent palette.
- Decision: changed the page background to `#f6f9fa` and replaced the near-white translucent header with an explicit `#f2f7f8` header background token, making the blue-gray contrast visible while keeping it subdued.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` compiles the page background as `#f6f9fa` and the header background as `#f2f7f8`.
- Deviations/blockers: none.

- Milestone: align homepage intro line with body typography.
- Success criteria: the opening homepage sentence uses the selected Avenir-style Option 2 treatment and the temporary intro style preview page is removed.
- Decision: changed `.home-copy p:first-child` from the larger Georgia treatment to the body font stack at `1.12rem`, regular weight, with a slightly relaxed line height. Removed `intro-style-options.html` after selection.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` compiles `.home-copy p:first-child` with the Avenir-first body stack, `font-size: 1.12rem`, regular weight, and no temporary `intro-style-options.html` page.
- Deviations/blockers: none.

- Milestone: apply selected site-title typography.
- Success criteria: the top-left `Michael Cai` site title uses the selected regular-weight Baskerville option and the temporary font preview page is removed.
- Decision: kept the existing Baskerville-first title stack and changed the site-title font weight from semibold to regular to reduce visual clunkiness. Removed `site-title-font-options.html` after the selection.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/assets/main.css` compiles the Baskerville site-title rule with `font-weight: 400`, and `site-title-font-options.html` is no longer present in the worktree.
- Deviations/blockers: none.

- Milestone: structure Teaching page content.
- Success criteria: Teaching page separates the Rutgers instructor role, NBER workshop assistantship, and Northwestern intermediate macro assistantship into distinct headed sections with years.
- Decision: added a Rutgers Econ 321 instructor section with course link and average rating, moved the intermediate macro topic bullets from Northwestern to Rutgers, removed `Quantity theory of money`, and added `AD-AS` after `IS-LM`.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/teaching/index.html` renders the Rutgers Econ 321 heading, linked course title, bold `4.55/5` rating, the moved topic list with `AD-AS`, and no `Quantity theory of money`.
- Deviations/blockers: none.

- Milestone: update homepage contact emails.
- Success criteria: Contact section distinguishes personal email from school email and includes `michael.cai [at] rutgers [dot] edu`.
- Decision: changed the existing email label to `Personal Email` and added a separate `School Email` line using the same non-literal address style.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders `Personal Email` and `School Email` with `michael.cai [at] rutgers [dot] edu`.
- Deviations/blockers: none.

- Milestone: finalize homepage typography and software copy.
- Success criteria: site title uses the selected Baskerville-style font, homepage software text wraps with the intro instead of leaving awkward whitespace after research interests, Contact heading is smaller, software projects are reordered with `StateSpaceRoutines.jl` before `DSGE.jl`, and the software lead sentence is updated.
- Decision: applied a Baskerville-first site title stack, moved software copy/list into the floated intro text flow, added a smaller Contact heading override, and converted the software links to explicit HTML list items to preserve wrapping and ordering.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders the updated software sentence, keeps software links inside the homepage intro flow, orders `StateSpaceRoutines.jl` before `DSGE.jl`, and confirmed `_site/assets/main.css` contains the Baskerville site-title stack and smaller Contact heading rule.
- Deviations/blockers: none.

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
