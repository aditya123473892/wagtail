> These steps can only be followed by Torchbox staff or those with access to the Wagtail website production admin.

## Setting up the post

1. Sign in to the admin interface
2. In the page explorer, load the Homepage `>` 'This Week in Wagtail' folder
3. Create a copy of the last page (e.g. `Issue #503`)
4. Update the URL slug and the title to be the next consecutive number
5. Go to edit the page
6. Change the date to the expected newsletter date
7. Change the Intro text to have the correct issue number
8. Update the content to include a link to the previous issue
9. Copy the "This Week's GitHub updates" posts into the doc, sometimes this may require multiple week's together. Sometimes some clean up is required and removal of commits that are not really helpful to the community (e.g. adding changelog, fix typo)
10. Add the news section, update the RFCs section
11. Publish and send a link to the published page to the `#twiw` channel for review, give 12-24 hours for any feedback.
12. Fix any issues or additional items then it should be ready to distribute to email

## Distribution via Mailchimp

1. Log into Mailchimp
2. Create Campaign -> Regular campaign
3. Choose Wagtail recipient list -> Send to entire list and click 'Next', hidden unexpectedly at the very bottom-right of the window.
4. Set:
  - Name your campaign: "TWIW Issue #[whatever]", substituting the issue number as appropriate
  - Email subject: "This Week In Wagtail Issue #[whatever]"
  - (Leave everything else)
5. Click 'Next' (bottom right)
6. Select your template: Code your own (tab) -> Import from URL
7. Set:
  - Campaign URL: Paste the URL of the page on Wagtail.io, appending "?email=true" to the URL e.g  https://wagtail.io/this-week-in-wagtail/issue-4/?email=true". Click 'Import'.
8. Click 'Next', check the summary, then
9. Click 'Send', also bottom right.