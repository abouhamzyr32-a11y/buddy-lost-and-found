# Product Requirements Document: Buddy Lost and Found

**Status:** Draft  
**Product:** Buddy  
**Audience:** Product, design, engineering, and lost-and-found staff

## 1. Summary

Buddy helps people find lost belongings by matching a natural-language description of an item to photos and details entered by staff when an item is turned in. A person describes what they lost in a search bar—for example, “a pink and purple water bottle with a unicorn pattern”—and Buddy returns likely matches from the lost-and-found inventory.

For the search to work, staff must add at least one clear photo for every found item. For clothing and other items that are hard to identify visually, staff should also photograph identifying details such as the brand or size tag.

## 2. Problem

People often have difficulty finding a lost item because they do not know whether it has been turned in, where to look, or how to describe it using the categories in a traditional lost-and-found system. Staff may also have difficulty matching vague inquiries to a large collection of items.

The product must make it straightforward for staff to create useful, consistent item records and for people to search those records using the words they would naturally use.

## 3. Goals and non-goals

### Goals

- Let a person describe a lost item in their own words and see relevant found-item matches.
- Make item photos a required part of staff intake.
- Prompt staff to add tag or detail photos when they are useful for identifying an item.
- Help people distinguish likely matches and take an appropriate next step to claim or ask about an item.
- Make it clear when results are uncertain or there are no good matches.

### Non-goals for the initial release

- Automatically confirm ownership or transfer an item to a claimant.
- Guarantee that every lost item will be found or that AI matches are correct.
- Search items that staff have not entered into the app.
- Replace the organization’s policies for holding, releasing, or disposing of found property.
- Provide public access to sensitive item details or identifying information.

## 4. Users

### Person searching for a lost item

Has lost an item and may remember its color, type, pattern, brand, or other distinguishing features, but may not know the organization’s inventory categories.

### Staff member recording a found item

Receives an item and records enough information and photos for a person to recognize it later. Staff may be using a phone in a busy environment, so intake should be quick and clear.

### Staff member helping with a claim

Reviews a claim or inquiry, checks ownership, and follows the organization’s process for returning the item.

## 5. User journeys

### Search

1. The person opens the lost-and-found search page.
2. They enter a description, such as “pink and purple water bottle with a unicorn pattern.”
3. Buddy interprets the description and searches item descriptions and photos.
4. The app displays likely matches with a confidence-appropriate explanation and safe, useful details.
5. The person opens a result and follows the organization’s instructions to ask about or claim it.
6. If no useful result appears, the app explains what to try next, such as changing the description or checking again later.

### Staff intake

1. A staff member starts a new found-item record.
2. They enter the required item information and take or upload a clear photo of the item.
3. The app prompts for additional photos when appropriate—for example, a jacket’s brand or size tag.
4. Staff review the photos and details, then save the record.
5. The item becomes searchable according to the organization’s access and publication rules.

### Claim follow-up

1. A person selects a likely match and submits an inquiry or follows the displayed contact instructions.
2. Staff review the inquiry and verify ownership using the organization’s process.
3. Staff record the outcome or provide next steps. A search match alone does not authorize release.

## 6. Product requirements

### 6.1 Search experience

- Provide a prominent search field that accepts natural-language descriptions.
- Include a short prompt and example to show that descriptions can include item type, color, pattern, brand, or distinctive features.
- Allow search without requiring the person to select a category first.
- Use both the entered description and available item information and images to rank candidate matches.
- Present results as likely matches, not confirmed matches. Do not imply that an AI result proves ownership.
- Show relevant, approved item photos and safe descriptive details in each result.
- Provide a useful empty state when there are no results and an option to revise the description.
- Handle partial, misspelled, or vague descriptions gracefully where feasible.
- Provide a way to contact staff or submit an inquiry for a selected result, subject to organization policy.

### 6.2 Buddy assistant

- Identify the search assistant as **Buddy**.
- Buddy’s role in the initial release is to help interpret a description and find matching inventory records.
- Buddy should not invent item details, claim certainty, or say that an item is available unless the record says so.
- If a description is too broad to produce useful matches, Buddy may suggest adding a distinguishing detail.
- Search results and suggestions must be based on the inventory available to the searcher.

### 6.3 Found-item intake

- Require at least one item photo before a record can be saved as searchable.
- Support taking a photo on a mobile device and uploading an existing photo.
- Prompt staff to capture a clear photo that shows the item as a whole.
- Allow multiple photos for a single item.
- Provide an optional notes/description field for details not obvious in the main photo.
- Capture a category or item type and any organization-required fields.
- Prompt staff to add detail photos when useful, particularly for clothing (such as brand, size, or care tags) and other visually ambiguous items.
- Do not make a tag photo mandatory for every item; require it only if the organization configures it for applicable categories.
- Let staff review photos and details before submitting.
- Make it possible for authorized staff to edit, mark claimed/returned, or remove a record according to policy.

### 6.4 Result details and handoff

- A result should provide enough information to help a person recognize a possible match without exposing private information or all verification details.
- Provide organization-configured next steps, such as contacting staff, visiting a designated desk, or submitting a claim inquiry.
- Ownership verification and item release remain staff-controlled.
- Staff should be able to see the relevant item record and the person’s inquiry, if the inquiry feature is enabled.

### 6.5 Inventory status

- Support at least the states needed to distinguish searchable items from items no longer available, such as available, claimed/returned, and removed.
- Exclude claimed/returned or removed items from ordinary search results.
- Make status visible to authorized staff and avoid showing stale availability to searchers.

## 7. Data requirements

Each item record should support:

- A unique record identifier.
- Item type or category.
- At least one item photo.
- Optional additional photos, including detail/tag photos.
- Staff-entered description and searchable attributes, such as color, pattern, brand, or size when known.
- Date received and current status.
- Any organization-specific location or handling information, restricted to authorized staff.
- A record of relevant status changes and staff actions, subject to the organization’s retention policy.

The app should collect only the information needed to identify, manage, and return an item. Photos should avoid capturing people, unrelated personal information, or sensitive details where possible.

## 8. AI matching behavior

- Rank records by relevance to the person’s description, using text and image information where supported.
- Treat AI matches as recommendations, not definitive identifications.
- Prefer useful matches with a clear uncertainty presentation over a confident but unsupported answer.
- Never expose hidden staff notes or restricted details through generated text.
- Do not use a person’s search description to alter an item record.
- The product team should evaluate matching quality on representative descriptions and inventory photos before launch and monitor it after launch.

## 9. Privacy, safety, and access

- Apply organization-defined access rules to item photos and details.
- Keep staff-only notes, precise storage locations, claimant information, and verification clues out of public search results.
- Define how long item photos, inquiries, and search-related data are retained.
- Provide staff authentication and role-appropriate permissions for intake and inventory management.
- Use secure transport and storage for photos and personal information.
- Provide an appropriate process to report or remove an incorrectly published or sensitive photo.

## 10. Success metrics

Establish a baseline during a pilot, then measure:

- **Search success rate:** share of search sessions that lead to a useful result or staff inquiry.
- **Time to find:** time from beginning a search to selecting a likely match or reaching the claim step.
- **Intake completeness:** share of searchable records with a clear main photo and required fields.
- **Detail-photo coverage:** share of eligible clothing/ambiguous items with a useful tag or detail photo.
- **Match usefulness:** share of selected results that staff confirm are relevant, where outcome tracking is available.
- **Return rate:** share of recorded items returned to their owners.
- **Operational burden:** staff time required to intake an item and handle an inquiry.

Metrics should be interpreted alongside the volume of items turned in and the organization’s existing lost-and-found process.

## 11. Acceptance criteria

1. A person can search using a free-text description without choosing a category.
2. The search returns candidate found items using available record information and photos, or clearly explains that no useful matches were found.
3. Results are presented as possible matches and do not confirm ownership.
4. Staff cannot submit a searchable item record without at least one photo.
5. Staff can add more than one photo and can add a tag/detail photo when appropriate.
6. Searchers cannot view staff-only notes or sensitive verification details.
7. Items marked claimed/returned or removed no longer appear in ordinary search results.
8. A person viewing a possible match can follow the configured next step to contact staff or submit an inquiry.
9. Staff retain control of ownership verification and item release.

## 12. Dependencies and rollout

- A staff-facing intake workflow and searchable item store.
- Image storage and an AI/text-and-image matching capability appropriate to the organization’s privacy requirements.
- Organization decisions on public access, contact/claim flow, inventory statuses, retention, and release procedures.
- A pilot with staff and representative inventory before broader launch.

Suggested rollout:

1. Pilot staff intake and photo quality with a small group.
2. Test search relevance using realistic descriptions, including vague and misspelled queries.
3. Launch to a limited audience with staff-assisted claim handling.
4. Review search outcomes, intake completeness, privacy issues, and staff feedback before expanding.

## 13. Open questions

- Is search public, or limited to authenticated members of the organization?
- What contact and claim process should be used, and what information may a searcher submit?
- Which item categories require tag/detail photos?
- Which item details and photos are safe to show before ownership is verified?
- What are the organization’s item retention, removal, and disposal policies?
- Should Buddy ask a follow-up question for vague descriptions, or simply show broad matches and suggestions?
- Which languages and accessibility requirements must be supported at launch?
- What systems, if any, must the app integrate with?
