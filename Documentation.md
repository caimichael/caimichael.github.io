# Documentation

## 2026-07-15

- Milestone: rename the GitHub publishing branch from `master` to `main`.
- Success criteria: GitHub uses `main` as the repository default and publishing branch, the obsolete remote `master` branch is removed, and the local `main` branch tracks `origin/main`.
- Decision: created `origin/main` at the current published commit, changed the repository default branch through the GitHub API, deleted `origin/master`, updated the local upstream configuration, and recreated the GitHub Pages configuration with `main` at `/` as its publishing source while preserving `www.michaelcai.com`.
- Validation: `git ls-remote --symref origin HEAD refs/heads/main refs/heads/master` confirmed remote `HEAD` and the sole requested branch ref point to `main`; the GitHub repository API reported `main` as the default branch; the Pages workflow completed successfully from `main`; the deployed Research page returned HTTP 200; and all linked local PDFs (`asset_market_channel.pdf`, `MichaelCai_JMP_Inertia.pdf`, `rss_heterogeneity.pdf`, `sr844.pdf`, `MichaelCai_CV.pdf`, and `MichaelCai_Teachingevals.pdf`) returned HTTP 200 with `application/pdf` content types.
- Deviations/blockers: GitHub CLI authorization was required because the GitHub connector and unavailable Chrome control backend could not change the repository default branch. Deleting the old publishing branch removed the prior Pages configuration and briefly produced 404 responses; recreating Pages with `main` as the source restored the site and static PDFs.

- Milestone: update the work-in-progress instruments paper entry.
- Success criteria: the Research page renames the paper to `When Predetermined Variables Can (and Should) Be Used as Instruments`, presents the supplied abstract in the existing collapsible abstract treatment, and renders correctly in a local browser.
- Decision: renamed the paper entry and added the abstract beneath the author line, using the same `paper-abstract`, `btn-abstract`, and `abstract-text` structure as the other research entries; rendered the supplied slope notation as the native characters `κ → 0` for reliable browser display without an added math dependency.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/research/index.html` contains the renamed title, collapsible abstract markup, full abstract text, and native `κ → 0` notation. Started the site at `http://127.0.0.1:4001/`, opened the Research page in the default browser, and visually verified the desktop rendering with a headless Chrome screenshot.
- Deviations/blockers: the in-app browser controller rejected its session metadata, so visual verification used headless Chrome and the local preview was opened in the system browser instead. Port 4001 was used because port 4000 was already occupied.

## 2026-07-03

- Milestone: add mobile-only homepage intro line break.
- Success criteria: on mobile, the opening homepage sentence breaks after `Economics`, leaving `at Rutgers University` on the second centered line; desktop rendering remains unchanged.
- Decision: inserted a dedicated `mobile-intro-break` element before `at Rutgers University`, hidden by default and displayed only inside the existing max-width `700px` mobile breakpoint.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/index.html` renders `<br class="mobile-intro-break" />` before `at Rutgers University`, `_site/assets/main.css` hides `.mobile-intro-break` by default, and the existing max-width `700px` mobile media query sets it to `display: block`.
- Deviations/blockers: none.

- Milestone: update vulnerable Ruby dependencies.
- Success criteria: Dependabot-reported Ruby advisories for `addressable`, `concurrent-ruby`, and `rexml` are resolved while preserving the existing Jekyll site build.
- Decision: ran a targeted Bundler update for `addressable`, `concurrent-ruby`, and `rexml`, which updated `addressable` to `2.9.0`, `concurrent-ruby` to `1.3.7`, `rexml` to `3.4.4`, and `public_suffix` to `7.0.5` as a transitive dependency.
- Validation: `/opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. `GEM_HOME=/private/tmp/cai-bundler-audit GEM_PATH=/private/tmp/cai-bundler-audit /private/tmp/cai-bundler-audit/bin/bundle-audit check --update` completed successfully with `No vulnerabilities found`.
- Deviations/blockers: none.

- Milestone: refine mobile header and homepage intro.
- Success criteria: mobile header spacing avoids the menu overlap issue, the stacked mobile name/navigation are centered, the profile photo and opening sentence are centered on mobile while the rest of the homepage text remains left-aligned, the homepage `research` word links visibly to the Research page, and About/Teaching render cleanly at a mobile viewport.
- Decision: replaced the mobile hamburger toggle with a centered stacked link row, centered the mobile site title, centered only the profile image and opening homepage sentence, kept subsequent homepage copy left-aligned, added wrapping safeguards, and linked `research` in the homepage blurb to `/research/` with a slightly stronger underline treatment.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Chrome DevTools Protocol mobile emulation at 390px width confirmed no horizontal overflow on About or Teaching (`scrollWidth: 390`), centered mobile title/navigation, centered profile photo and opening sentence, `researchHref: "/research/"`, and Teaching field lists collapsing to block layout on mobile. Screenshots were saved to `/private/tmp/cai-home-mobile-final.png` and `/private/tmp/cai-teaching-mobile-final.png` for visual inspection.
- Deviations/blockers: none.

- Milestone: consolidate Teaching supporting fields.
- Success criteria: Teaching entries use one consistent field-list style for roles, links, ratings, selected topics, materials, and evaluations.
- Decision: moved `Selected topics`, `Materials`, `Evaluations`, and years into the same `teaching-fields` definition lists, using `Term` for the year field after `Course`/`Co-taught with`; shortened Northwestern's role to `Teaching assistant`; revised the NBER topic list; matched standard Teaching field-label styling to the homepage Contact labels; made the `Co-taught with` label a lighter secondary exception; capitalized the evaluations link label; and removed the now-unused teaching label/resource styles.
- Validation: `BUNDLE_PATH=/Users/michaelcai/caimichael.github.io/main/vendor/bundle /opt/homebrew/opt/ruby/bin/bundle exec jekyll build` completed successfully. Confirmed `_site/teaching/index.html` renders `Term` after `Course` for Rutgers/Northwestern and after `Co-taught with` for NBER, retains the four NBER bullets, and keeps the secondary co-teacher label styling.
- Deviations/blockers: none.

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
