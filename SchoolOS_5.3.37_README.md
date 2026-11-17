# School OS 5.3.37 — Visible parent registration links

[Open the installable update on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.37_Parent_Link_Access_Update.zip)

The parent-registration link now has a prominent card on both **School admin home** and **Admissions overview**, and at the top of **Admissions → Family onboarding**. The card is outside collapsed settings and shows a clear next step for each state.

## Real school accounts

1. Install this ZIP through Platform Super Admin → Core updates, then refresh open tabs.
2. Open school admin home or Admissions → Family onboarding.
3. Find **Parent self-registration link**.
4. If shown, click **Prepare family onboarding**. If no link exists, click **Generate & enable school link**. A paused school link has **Enable parent registration** instead.
5. Click **Copy parent registration link** and send that generated URL to existing parents. It contains `family_join=` and opens the school's multi-child parent form.

Admissions sees and can copy the same enabled school link. School administrators retain control of preparation, generation and enabling; admissions is not silently given these permissions. Existing school links remain unchanged unless an administrator chooses to replace one in settings.

If the canonical installation address is missing, the card explains that the Platform Super Admin must configure it under Setup & account. Invalid/paused links are not offered as working copy buttons.

The internal school workspace is `index.php?s=applications&view=families`. The generated `family_join=` URL is the link intended for parents.

## Shared demo accounts

The screenshot's blank sharing area came from the shared demo's intentionally disabled live-registration links. The demo now has clearly labelled **Preview parent registration form** and **Copy demo preview link** buttons, with a populated example-preview URL.

The example supports adding child sections, but does not submit or save registration data. POST is refused, and the preview submit button is disabled. It contains example class choices rather than a directory of real school records. Use fictional information only. Real schools generate their own live link through their actual school-admin account.

External email/WhatsApp handovers and provider changes remain disabled in the shared demo.

## Layout

The Family onboarding page uses separate grid rows and consistent gaps. Nested settings no longer create a second glass panel border inside the first. The sharing actions have clear colours, full opacity, visible labels and touch-sized buttons. Light/dark layouts were checked at desktop and phone widths, including expanded settings.

This is a cumulative 36-file update plus release.json. It preserves the family registration/review/password setup introduced in 5.3.36. No configuration, credentials, private keys, test data or test render pages are included. No new database tables are introduced by this patch.

Back up application files and database before installing. This session did not deploy the update on the hosted school.

[Validation](SchoolOS_5.3.37_Validation.md) · [Checksum](SchoolOS_5.3.37_SHA256SUMS.txt) · [Family onboarding guide](SchoolOS_5.3.36_Family_Onboarding_Guide.md)
