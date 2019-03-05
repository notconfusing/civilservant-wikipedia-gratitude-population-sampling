# Data Model

## Candidate (a user who might be thanked)
### 1-1 with wikipedia users if updating, many-1 if inserting not updating
+ cand_id (internal)
+ created_at (when the record was created)
+ lang (wikipedia code)
+ user_id (wikipedia user id unique to language)
+ user_name (wikipedia user name unique to language)
+ user_reg (datetime when the wikipedia account was created)
+ edit_count (num edits on wiki)
+ thanks_sent (num thanks sent on wiki)
+ thanks_received (num thanks received on wiki)
+ has_email (user can be emailed via wiki)

## randomizations
### many-1 to candidate
+ randomization_id (internal)
+ cand_id (foreign key)
+ condition (enum[non-in-experiment, thankee, placebo])
+ condition_created_at (date)

## edits
+ edit_id (internal)
+ rev_id (wikipedia id unique to lang)
+ page_name
+ page_id
+ page_namespace
+ ores_damaging
+ ores_goodfaith
+ ores_damaging_score
+ ores_goodfaith_score
+ de_flagged (de-only)
+ de_flagging_algo_version 


## edits_display
+ html_blob
+ lang (redundant, could not store)
+ newRevId (redundant, could not store)
+ newRevDate (redundant, could not store)
+ newRevUser (redundant, could not store)
+ newRevComment
+ oldRevId
+ oldRevDate
+ oldRevUser
+ oldRevComment

## worksets
### a collection of edits for thanking consideration
+ worsket_id
+ edits (how to make dynamic in case of skipping?)

##  workset_responses
+ response_id (internal)
+ cand_id (foreign)
+ responder_id (wikipedia user id)
+ action (enum[editid, or "SKIP"])