# Ferramentas

ElevenLabs expõe 149 ferramentas.

### 1. `elevenlabs_get_speech_history`
**Input**: `page_size` (opcional), `start_after_history_item_id` (opcional), `voice_id` (opcional), `model_id` (opcional), `date_before_unix` (opcional), `date_after_unix` (opcional), `sort_direction` (opcional), `search` (opcional), `source` (opcional), `account` (opcional), `start_after_history_item_ids` (opcional), `voice_ids` (opcional), `model_ids` (opcional)

List Generated Items. Returns a list of your generated audio (e.g. text to speech, speech to speech, Studio, dubbing). Music and SFX generations are not included and cannot currently be retrieved via the API. Bulk sup…

### 2. `elevenlabs_get_speech_history_item_by_id`
**Input**: `history_item_id`, `account` (opcional), `history_item_ids` (opcional)

Get History Item. Retrieves a history item. Bulk support: accepts history_item_ids for batched execution.

### 3. `elevenlabs_delete_speech_history_item`
**Input**: `history_item_id`, `account` (opcional), `history_item_ids` (opcional)

Delete History Item. Delete a history item by its ID Bulk support: accepts history_item_ids for batched execution.

### 4. `elevenlabs_get_audio_full_from_speech_history_item`
**Input**: `history_item_id`, `account` (opcional), `history_item_ids` (opcional)

Get Audio From History Item. Returns the audio of an history item. Bulk support: accepts history_item_ids for batched execution.

### 5. `elevenlabs_download_speech_history_items`
**Input**: `history_item_ids`, `output_format` (opcional), `account` (opcional)

Download History Items. Download one or more history items. If one history item ID is provided, we will return a single audio file. If more than one history item IDs are provided, we will provide the history items pac…

### 6. `elevenlabs_sound_generation`
**Input**: `output_format` (opcional), `text`, `loop` (opcional), `duration_seconds` (opcional), `prompt_influence` (opcional), `model_id` (opcional), `account` (opcional), `model_ids` (opcional)

Sound Generation. Turn text into sound effects for your videos, voice-overs or video games using the most advanced sound effects models in the world. Bulk support: accepts model_ids for batched execution.

### 7. `elevenlabs_get_audio_isolation_history`
**Input**: `page_size` (opcional), `page` (opcional), `search` (opcional), `account` (opcional)

Get Audio Isolation History. Returns a list of all your audio isolation generations.

### 8. `elevenlabs_delete_audio_isolation_history_item`
**Input**: `history_item_id`, `account` (opcional), `history_item_ids` (opcional)

Delete Audio Isolation History Item.

### 9. `elevenlabs_delete_sample`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Delete Sample. Removes a sample by its ID. Bulk support: accepts voice_ids, sample_ids for batched execution.

### 10. `elevenlabs_get_audio_from_sample`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Get Audio From Sample. Returns the audio corresponding to a sample attached to a voice. Bulk support: accepts voice_ids, sample_ids for batched execution.

### 11. `elevenlabs_text_to_speech_full`
**Input**: `voice_id`, `enable_logging` (opcional), `optimize_streaming_latency` (opcional), `output_format` (opcional), `text`, `model_id` (opcional), `language_code` (opcional), `voice_settings` (opcional), `pronunciation_dictionary_locators` (opcional), `seed` (opcional), `previous_text` (opcional), `next_text` (opcional), `previous_request_ids` (opcional), `next_request_ids` (opcional), `use_pvc_as_ivc` (opcional), `apply_text_normalization` (opcional), `apply_language_text_normalization` (opcional), `account` (opcional)

Text To Speech. Converts text into speech using a voice of your choice and returns audio.

### 12. `elevenlabs_text_to_dialogue`
**Input**: `output_format` (opcional), `enable_logging` (opcional), `inputs`, `model_id` (opcional), `language_code` (opcional), `settings` (opcional), `pronunciation_dictionary_locators` (opcional), `seed` (opcional), `apply_text_normalization` (opcional), `account` (opcional), `model_ids` (opcional)

Text To Dialogue (Multi-Voice).

### 13. `elevenlabs_create_voice`
**Input**: `voice_name`, `voice_description`, `generated_voice_id`, `labels` (opcional), `played_not_selected_voice_ids` (opcional), `account` (opcional)

Create A New Voice From Voice Preview.

### 14. `elevenlabs_text_to_voice_design`
**Input**: `output_format` (opcional), `voice_description`, `model_id` (opcional), `text` (opcional), `auto_generate_text` (opcional), `loudness` (opcional), `seed` (opcional), `guidance_scale` (opcional), `stream_previews` (opcional), `should_enhance` (opcional), `remixing_session_id` (opcional), `remixing_session_iteration_id` (opcional), `quality` (opcional), `reference_audio_base64` (opcional), `prompt_strength` (opcional), `account` (opcional), `model_ids` (opcional), `remixing_session_ids` (opcional), `remixing_session_iteration_ids` (opcional)

Design A Voice.. Design a voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To create a voice use the genera…

### 15. `elevenlabs_text_to_voice_remix`
**Input**: `voice_id`, `output_format` (opcional), `voice_description`, `text` (opcional), `auto_generate_text` (opcional), `loudness` (opcional), `seed` (opcional), `guidance_scale` (opcional), `stream_previews` (opcional), `remixing_session_id` (opcional), `remixing_session_iteration_id` (opcional), `prompt_strength` (opcional), `account` (opcional), `voice_ids` (opcional), `remixing_session_ids` (opcional), `remixing_session_iteration_ids` (opcional)

Remix A Voice.. Remix an existing voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To create a voice use th…

### 16. `elevenlabs_text_to_voice_preview_stream`
**Input**: `generated_voice_id`, `account` (opcional), `generated_voice_ids` (opcional)

Text To Voice Preview Streaming.

### 17. `elevenlabs_get_user_info`
**Input**: `account` (opcional)

Get User Info. Gets information about the user

### 18. `elevenlabs_get_user_subscription_info`
**Input**: `account` (opcional)

Get User Subscription Info. Gets extended information about the users subscription

### 19. `elevenlabs_get_voice_settings_default`
**Input**: `account` (opcional)

Get Default Voice Settings.. Gets the default settings for voices. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app.

### 20. `elevenlabs_get_voice_settings`
**Input**: `voice_id`, `account` (opcional), `voice_ids` (opcional)

Get Voice Settings. Returns the settings for a specific voice. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app. Bulk…

### 21. `elevenlabs_edit_voice_settings`
**Input**: `voice_id`, `stability` (opcional), `use_speaker_boost` (opcional), `similarity_boost` (opcional), `style` (opcional), `speed` (opcional), `account` (opcional), `voice_ids` (opcional)

Edit Voice Settings. Edit your settings for a specific voice. "similarity_boost" corresponds to "Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app. Bulk…

### 22. `elevenlabs_get_voice_accents`
**Input**: `language` (opcional), `model_id` (opcional), `account` (opcional), `model_ids` (opcional)

Get Voice Accents. Gets the list of available accents in the shared voice library. Bulk support: accepts model_ids for batched execution.

### 23. `elevenlabs_get_voices`
**Input**: `show_legacy` (opcional), `account` (opcional)

List Voices. Returns a list of all available voices for a user. Stops working once the user's workspace exceeds 500 voices.

### 24. `elevenlabs_get_voice_by_id`
**Input**: `voice_id`, `with_settings` (opcional), `account` (opcional), `voice_ids` (opcional)

Get Voice. Returns metadata about a specific voice. Bulk support: accepts voice_ids for batched execution.

### 25. `elevenlabs_delete_voice`
**Input**: `voice_id`, `account` (opcional), `voice_ids` (opcional)

Delete Voice. Deletes a voice by its ID. Bulk support: accepts voice_ids for batched execution.

### 26. `elevenlabs_get_user_voices_v2`
**Input**: `next_page_token` (opcional), `page_size` (opcional), `search` (opcional), `sort` (opcional), `sort_direction` (opcional), `voice_type` (opcional), `category` (opcional), `fine_tuning_state` (opcional), `collection_id` (opcional), `gender` (opcional), `age` (opcional), `language` (opcional), `accent` (opcional), `use_cases` (opcional), `min_notice_period_days` (opcional), `include_custom_rates` (opcional), `include_live_moderated` (opcional), `high_quality` (opcional), `include_total_count` (opcional), `voice_ids` (opcional), `account` (opcional)

Get Voices V2. Gets a list of all available voices for a user with search, filtering and pagination.

### 27. `elevenlabs_replicate_voice_to_isolated_environment`
**Input**: `voice_id`, `target_workspace_id`, `preserve_voice_id` (opcional), `account` (opcional), `voice_ids` (opcional), `target_workspace_ids` (opcional), `preserve_voice_ids` (opcional)

Replicate Voice To Isolated Environment.

### 28. `elevenlabs_add_sharing_voice`
**Input**: `public_user_id`, `voice_id`, `new_name`, `bookmarked` (opcional), `account` (opcional), `public_user_ids` (opcional), `voice_ids` (opcional)

Add Shared Voice. Add a shared voice to your collection of voices. Bulk support: accepts public_user_ids, voice_ids for batched execution.

### 29. `elevenlabs_create_podcast`
**Input**: `safety-identifier` (opcional), `model_id`, `mode`, `source`, `quality_preset` (opcional), `duration_scale` (opcional), `language` (opcional), `intro` (opcional), `outro` (opcional), `instructions_prompt` (opcional), `highlights` (opcional), `callback_url` (opcional), `apply_text_normalization` (opcional), `account` (opcional), `model_ids` (opcional)

Create Podcast. Create and auto-convert a podcast project. Currently, the LLM cost is covered by us but you will still be charged for the audio generation. In the future, you will be charged for both the LLM and audio…

### 30. `elevenlabs_update_pronunciation_dictionaries`
**Input**: `project_id`, `pronunciation_dictionary_locators`, `invalidate_affected_text` (opcional), `account` (opcional), `project_ids` (opcional)

Create Pronunciation Dictionaries.

### 31. `elevenlabs_get_projects`
**Input**: `account` (opcional)

List Studio Projects. Returns a list of your Studio projects with metadata.

### 32. `elevenlabs_get_project_by_id`
**Input**: `project_id`, `share_id` (opcional), `account` (opcional), `project_ids` (opcional), `share_ids` (opcional)

Get Studio Project. Returns information about a specific Studio project. This endpoint returns more detailed information about a project than `GET /v1/studio`. Bulk support: accepts project_ids, share_ids for batched…

### 33. `elevenlabs_edit_project`
**Input**: `project_id`, `name`, `default_title_voice_id`, `default_paragraph_voice_id`, `title` (opcional), `author` (opcional), `isbn_number` (opcional), `volume_normalization` (opcional), `account` (opcional), `project_ids` (opcional), `default_title_voice_ids` (opcional), `default_paragraph_voice_ids` (opcional)

Update Studio Project. Updates the specified Studio project by setting the values of the parameters passed. Bulk support: accepts project_ids, default_title_voice_ids, default_paragraph_voice_ids for batched execution.

### 34. `elevenlabs_delete_project`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Delete Studio Project. Deletes a Studio project. Bulk support: accepts project_ids for batched execution.

### 35. `elevenlabs_convert_project_endpoint`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Convert Studio Project. Starts conversion of a Studio project and all of its chapters. Bulk support: accepts project_ids for batched execution.

### 36. `elevenlabs_get_project_snapshots`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

List Studio Project Snapshots.

### 37. `elevenlabs_get_project_snapshot_endpoint`
**Input**: `project_id`, `project_snapshot_id`, `account` (opcional), `project_ids` (opcional), `project_snapshot_ids` (opcional)

Get Project Snapshot. Returns the project snapshot. Bulk support: accepts project_ids, project_snapshot_ids for batched execution.

### 38. `elevenlabs_stream_project_snapshot_archive_60141b`
**Input**: `project_id`, `project_snapshot_id`, `account` (opcional), `project_ids` (opcional), `project_snapshot_ids` (opcional)

Stream Archive With Studio Project Audio.

### 39. `elevenlabs_get_chapters`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

List Chapters. Returns a list of a Studio project's chapters. Bulk support: accepts project_ids for batched execution.

### 40. `elevenlabs_add_chapter`
**Input**: `project_id`, `name`, `from_url` (opcional), `account` (opcional), `project_ids` (opcional)

Create Chapter. Creates a new chapter either as blank or from a URL. Bulk support: accepts project_ids for batched execution.

### 41. `elevenlabs_get_chapter_by_id_endpoint`
**Input**: `project_id`, `chapter_id`, `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional)

Get Chapter. Returns information about a specific chapter. Bulk support: accepts project_ids, chapter_ids for batched execution.

### 42. `elevenlabs_edit_chapter`
**Input**: `project_id`, `chapter_id`, `name` (opcional), `content` (opcional), `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional)

Update Chapter. Updates a chapter. Bulk support: accepts project_ids, chapter_ids for batched execution.

### 43. `elevenlabs_delete_chapter_endpoint`
**Input**: `project_id`, `chapter_id`, `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional)

Delete Chapter. Deletes a chapter. Bulk support: accepts project_ids, chapter_ids for batched execution.

### 44. `elevenlabs_convert_chapter_endpoint`
**Input**: `project_id`, `chapter_id`, `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional)

Convert Chapter. Starts conversion of a specific chapter. Bulk support: accepts project_ids, chapter_ids for batched execution.

### 45. `elevenlabs_get_chapter_snapshots`
**Input**: `project_id`, `chapter_id`, `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional)

List Chapter Snapshots. Gets information about all the snapshots of a chapter. Each snapshot can be downloaded as audio. Whenever a chapter is converted a snapshot will automatically be created. Bulk support: accepts…

### 46. `elevenlabs_get_chapter_snapshot_endpoint`
**Input**: `project_id`, `chapter_id`, `chapter_snapshot_id`, `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional), `chapter_snapshot_ids` (opcional)

Get Chapter Snapshot. Returns the chapter snapshot. Bulk support: accepts project_ids, chapter_ids, chapter_snapshot_ids for batched execution.

### 47. `elevenlabs_stream_chapter_snapshot_audio`
**Input**: `project_id`, `chapter_id`, `chapter_snapshot_id`, `convert_to_mpeg` (opcional), `account` (opcional), `project_ids` (opcional), `chapter_ids` (opcional), `chapter_snapshot_ids` (opcional)

Stream Chapter Audio. Stream the audio from a chapter snapshot. Use `GET /v1/studio/projects/{project_id}/chapters/{chapter_id}/snapshots` to return the snapshots of a chapter. Bulk support: accepts project_ids, chapt…

### 48. `elevenlabs_get_project_muted_tracks_endpoint`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Get Project Muted Tracks. Returns a list of chapter IDs that have muted tracks in a project. Bulk support: accepts project_ids for batched execution.

### 49. `elevenlabs_dubbing_project_list`
**Input**: `cursor` (opcional), `page_size` (opcional), `status` (opcional), `sort_direction` (opcional), `account` (opcional)

List Dubbing Projects. List the workspace's dubbing projects (cursor-paginated).

### 50. `elevenlabs_dubbing_project_get`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Get Dubbing Project. Full project detail, including its language target ids. Bulk support: accepts project_ids for batched execution.

### 51. `elevenlabs_dubbing_project_delete`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Delete Dubbing Project. Delete a project and its language targets. Bulk support: accepts project_ids for batched execution.

### 52. `elevenlabs_dubbing_language_list`
**Input**: `project_id`, `cursor` (opcional), `page_size` (opcional), `status` (opcional), `account` (opcional), `project_ids` (opcional)

List Dubbing Language Targets.

### 53. `elevenlabs_dubbing_language_create`
**Input**: `project_id`, `target_language`, `voice_settings` (opcional), `translations` (opcional), `account` (opcional), `project_ids` (opcional)

Create Dubbing Language Target.

### 54. `elevenlabs_dubbing_language_get`
**Input**: `project_id`, `language_id`, `account` (opcional), `project_ids` (opcional), `language_ids` (opcional)

Get Dubbing Language Target. Full language-target detail. Bulk support: accepts project_ids, language_ids for batched execution.

### 55. `elevenlabs_dubbing_language_delete`
**Input**: `project_id`, `language_id`, `account` (opcional), `project_ids` (opcional), `language_ids` (opcional)

Delete Dubbing Language Target.

### 56. `elevenlabs_dubbing_transcript_get`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Get Dubbing Transcript. The project's source transcript, as editable segments. Bulk support: accepts project_ids for batched execution.

### 57. `elevenlabs_dubbing_transcript_segment_update`
**Input**: `project_id`, `segment_id`, `text` (opcional), `speaker_id` (opcional), `start_s` (opcional), `end_s` (opcional), `account` (opcional), `project_ids` (opcional), `segment_ids` (opcional), `speaker_ids` (opcional)

Update Dubbing Transcript Segment.

### 58. `elevenlabs_dubbing_transcript_segment_delete`
**Input**: `project_id`, `segment_id`, `account` (opcional), `project_ids` (opcional), `segment_ids` (opcional)

Delete Dubbing Transcript Segment.

### 59. `elevenlabs_dubbing_transcript_segments_update`
**Input**: `project_id`, `segments`, `account` (opcional), `project_ids` (opcional)

Update Dubbing Transcript Segments.

### 60. `elevenlabs_dubbing_transcript_segment_add`
**Input**: `project_id`, `text`, `speaker_id`, `start_s`, `end_s`, `account` (opcional), `project_ids` (opcional), `speaker_ids` (opcional)

Add Dubbing Transcript Segment.

### 61. `elevenlabs_dubbing_target_transcript_get`
**Input**: `project_id`, `language_id`, `account` (opcional), `project_ids` (opcional), `language_ids` (opcional)

Get Dubbing Target Transcript.

### 62. `elevenlabs_dubbing_target_transcript_segmen_b565e6`
**Input**: `project_id`, `language_id`, `segment_id`, `translation` (opcional), `account` (opcional), `project_ids` (opcional), `language_ids` (opcional), `segment_ids` (opcional)

Update Dubbing Target Transcript Segment.

### 63. `elevenlabs_dubbing_target_transcript_segmen_fa79db`
**Input**: `project_id`, `language_id`, `segments`, `account` (opcional), `project_ids` (opcional), `language_ids` (opcional)

Update Dubbing Target Transcript Segments.

### 64. `elevenlabs_dubbing_target_transcript_regenerate`
**Input**: `project_id`, `language_id`, `account` (opcional), `project_ids` (opcional), `language_ids` (opcional)

Regenerate Dubbing Target. Enterprise only. Re-dub a target from its edited transcript, re-synthesizing only the edited regions (charged like a generation). Conflicts when the target has no edits to apply -- nothing i…

### 65. `elevenlabs_list_dubs`
**Input**: `cursor` (opcional), `page_size` (opcional), `dubbing_status` (opcional), `dubbing_statuses` (opcional), `dubbing_models` (opcional), `target_language_codes` (opcional), `creation_sources` (opcional), `filter_by_creator` (opcional), `order_by` (opcional), `order_direction` (opcional), `account` (opcional)

List Dubs. List the dubs you have access to.

### 66. `elevenlabs_get_dubbed_metadata`
**Input**: `dubbing_id`, `account` (opcional), `dubbing_ids` (opcional)

Get Dubbing. Returns metadata about a dubbing project, including whether it's still in progress or not Bulk support: accepts dubbing_ids for batched execution.

### 67. `elevenlabs_delete_dubbing`
**Input**: `dubbing_id`, `account` (opcional), `dubbing_ids` (opcional)

Delete Dubbing. Deletes a dubbing project. Bulk support: accepts dubbing_ids for batched execution.

### 68. `elevenlabs_get_dubbed_file`
**Input**: `dubbing_id`, `language_code`, `account` (opcional), `dubbing_ids` (opcional)

Get Dubbed File. Returns dub as a streamed MP3 or MP4 file. If this dub has been edited using Dubbing Studio you need to use the resource render endpoint as this endpoint only returns the original automatic dub result…

### 69. `elevenlabs_get_dubbing_transcripts`
**Input**: `dubbing_id`, `language_code`, `format_type`, `account` (opcional), `dubbing_ids` (opcional)

Retrieve A Transcript. Fetch the transcript for one of the languages in a dub. Bulk support: accepts dubbing_ids for batched execution.

### 70. `elevenlabs_get_models`
**Input**: `account` (opcional)

Get Models. Gets a list of available models.

### 71. `elevenlabs_get_audio_native_project_setting_340fd1`
**Input**: `project_id`, `account` (opcional), `project_ids` (opcional)

Get Audio Native Project Settings.

### 72. `elevenlabs_audio_native_update_content_from_url`
**Input**: `url`, `author` (opcional), `title` (opcional), `account` (opcional)

Update Audio-Native Content From Url.

### 73. `elevenlabs_get_library_voices`
**Input**: `page_size` (opcional), `category` (opcional), `gender` (opcional), `age` (opcional), `accent` (opcional), `language` (opcional), `locale` (opcional), `search` (opcional), `use_cases` (opcional), `descriptives` (opcional), `featured` (opcional), `min_notice_period_days` (opcional), `include_custom_rates` (opcional), `include_live_moderated` (opcional), `reader_app_enabled` (opcional), `owner_id` (opcional), `sort` (opcional), `page` (opcional), `account` (opcional), `owner_ids` (opcional)

Get Voices. Retrieves a list of shared voices. Bulk support: accepts owner_ids for batched execution.

### 74. `elevenlabs_add_from_rules`
**Input**: `rules`, `name`, `description` (opcional), `workspace_access` (opcional), `account` (opcional)

Add A Pronunciation Dictionary.

### 75. `elevenlabs_get_pronunciation_dictionary_metadata`
**Input**: `pronunciation_dictionary_id`, `account` (opcional), `pronunciation_dictionary_ids` (opcional)

Get Metadata For A Pronunciation Dictionary.

### 76. `elevenlabs_patch_pronunciation_dictionary`
**Input**: `pronunciation_dictionary_id`, `archived` (opcional), `name` (opcional), `account` (opcional), `pronunciation_dictionary_ids` (opcional)

Update Pronunciation Dictionary.

### 77. `elevenlabs_set_rules`
**Input**: `pronunciation_dictionary_id`, `rules`, `account` (opcional), `pronunciation_dictionary_ids` (opcional)

Set Rules On The Pronunciation Dictionary.

### 78. `elevenlabs_add_rules`
**Input**: `pronunciation_dictionary_id`, `rules`, `account` (opcional), `pronunciation_dictionary_ids` (opcional)

Add Rules To The Pronunciation Dictionary.

### 79. `elevenlabs_remove_rules`
**Input**: `pronunciation_dictionary_id`, `rule_strings`, `account` (opcional), `pronunciation_dictionary_ids` (opcional)

Remove Rules From The Pronunciation Dictionary.

### 80. `elevenlabs_get_pronunciation_dictionary_ver_45baf2`
**Input**: `dictionary_id`, `version_id`, `account` (opcional), `dictionary_ids` (opcional), `version_ids` (opcional)

Get A Pls File With A Pronunciation Dictionary Version Rules.

### 81. `elevenlabs_get_pronunciation_dictionaries_metadata`
**Input**: `cursor` (opcional), `page_size` (opcional), `sort` (opcional), `sort_direction` (opcional), `include_archived` (opcional), `account` (opcional)

Get Pronunciation Dictionaries.

### 82. `elevenlabs_disable`
**Input**: `api_key_name`, `account` (opcional)

Disable Api Key. Disable the API key used to authenticate this request. Requires the query parameter `api_key_name=self` as an explicit confirmation.

### 83. `elevenlabs_set_third_party_disabling_policy`
**Input**: `third_party_disable_allowed` (opcional), `account` (opcional)

Set Workspace Third-Party Disabling Policy.

### 84. `elevenlabs_get_service_account_api_keys_route`
**Input**: `service_account_user_id`, `account` (opcional), `service_account_user_ids` (opcional)

Get Service Account Api Keys Route.

### 85. `elevenlabs_create_service_account_api_key`
**Input**: `service_account_user_id`, `name`, `permissions`, `character_limit` (opcional), `allowed_ips` (opcional), `third_party_disable_allowed` (opcional), `account` (opcional), `service_account_user_ids` (opcional)

Create Service Account Api Key.

### 86. `elevenlabs_edit_service_account_api_key`
**Input**: `service_account_user_id`, `api_key_id`, `is_enabled` (opcional), `name` (opcional), `permissions` (opcional), `character_limit` (opcional), `allowed_ips` (opcional), `third_party_disable_allowed` (opcional), `account` (opcional), `service_account_user_ids` (opcional), `api_key_ids` (opcional)

Edit Service Account Api Key. Update an existing API key for a service account Bulk support: accepts service_account_user_ids, api_key_ids for batched execution.

### 87. `elevenlabs_delete_service_account_api_key`
**Input**: `service_account_user_id`, `api_key_id`, `account` (opcional), `service_account_user_ids` (opcional), `api_key_ids` (opcional)

Delete Service Account Api Key.

### 88. `elevenlabs_get_workspace_audit_logs`
**Input**: `limit` (opcional), `cursor` (opcional), `time_from_unix_ms` (opcional), `time_to_unix_ms` (opcional), `actor_uid` (opcional), `class_name` (opcional), `activity_name` (opcional), `account` (opcional)

Get Workspace Audit Logs. Returns the audit log for the workspace. Requires enterprise tier and the audit_log_read permission.

### 89. `elevenlabs_list_auth_connections`
**Input**: `account` (opcional)

Get Workspace Auth Connections.

### 90. `elevenlabs_create_auth_connection`
**Input**: `body`, `account` (opcional)

Create Workspace Auth Connection.

### 91. `elevenlabs_update_auth_connection`
**Input**: `auth_connection_id`, `body`, `account` (opcional), `auth_connection_ids` (opcional)

Update Workspace Auth Connection.

### 92. `elevenlabs_delete_auth_connection`
**Input**: `auth_connection_id`, `account` (opcional), `auth_connection_ids` (opcional)

Delete Workspace Auth Connection.

### 93. `elevenlabs_get_workspace_service_accounts`
**Input**: `account` (opcional)

Get Workspace Service Accounts.

### 94. `elevenlabs_create_service_account`
**Input**: `name`, `default_sharing_groups` (opcional), `account` (opcional)

Create Service Account. Create a new service account in the workspace. By default, a workspace can have up to 20 service accounts. Enterprise customers may request an increase to this limit, up to 100.

### 95. `elevenlabs_get_groups_endpoint`
**Input**: `account` (opcional)

Get All Groups. Get all groups in the workspace

### 96. `elevenlabs_search_groups`
**Input**: `name`, `account` (opcional)

Search User Groups. Searches for user groups in the workspace. Multiple or no groups may be returned.

### 97. `elevenlabs_remove_member`
**Input**: `group_id`, `email`, `account` (opcional), `group_ids` (opcional)

Delete Member From User Group.

### 98. `elevenlabs_add_member`
**Input**: `group_id`, `email`, `account` (opcional), `group_ids` (opcional)

Add Member To User Group. Adds a member of your workspace to the specified group. Requires `group_members_manage` permission. Bulk support: accepts group_ids for batched execution.

### 99. `elevenlabs_invite_user`
**Input**: `email`, `workspace_permission` (opcional), `seat_type` (opcional), `group_ids` (opcional), `usage_limit` (opcional), `account` (opcional)

Invite User. Sends an email invitation to join your workspace to the provided email. If the user doesn't have an account they will be prompted to create one. If the user accepts this invite they will be added as a use…

### 100. `elevenlabs_invite_users_bulk`
**Input**: `emails`, `seat_type` (opcional), `group_ids` (opcional), `usage_limit` (opcional), `account` (opcional)

Invite Multiple Users. Sends email invitations to join your workspace to the provided emails. Requires all email addresses to be part of a verified domain. If the users don't have an account they will be prompted to c…

### 101. `elevenlabs_delete_invite`
**Input**: `email`, `account` (opcional)

Delete Existing Invitation. Invalidates an existing email invitation. The invitation will still show up in the inbox it has been delivered to, but activating it to join the workspace won't work. This endpoint may only…

### 102. `elevenlabs_get_workspace_members`
**Input**: `account` (opcional)

Get Workspace Members. Gets a list of all members of the workspace, including locked members. Service accounts are excluded. Requires the workspace_members_read permission.

### 103. `elevenlabs_update_workspace_member`
**Input**: `email`, `is_locked` (opcional), `workspace_role` (opcional), `workspace_seat_type` (opcional), `account` (opcional)

Update Member. Updates attributes of a workspace member. Apart from the email identifier, all parameters will remain unchanged unless specified. This endpoint may only be called by workspace administrators.

### 104. `elevenlabs_get_resource_metadata`
**Input**: `resource_id`, `resource_type`, `account` (opcional), `resource_ids` (opcional)

Get Resource. Gets the metadata of a resource by ID. Bulk support: accepts resource_ids for batched execution.

### 105. `elevenlabs_share_resource_endpoint`
**Input**: `resource_id`, `role`, `resource_type`, `user_email` (opcional), `group_id` (opcional), `workspace_api_key_id` (opcional), `account` (opcional), `resource_ids` (opcional), `group_ids` (opcional), `workspace_api_key_ids` (opcional)

Share Workspace Resource. Grants a role (one of 'admin', 'editor', 'commenter', or 'viewer') on a workspace resource to a user, group, or workspace (service account) API key. This overrides any existing role the targe…

### 106. `elevenlabs_unshare_resource_endpoint`
**Input**: `resource_id`, `resource_type`, `user_email` (opcional), `group_id` (opcional), `workspace_api_key_id` (opcional), `account` (opcional), `resource_ids` (opcional), `group_ids` (opcional), `workspace_api_key_ids` (opcional)

Unshare Workspace Resource. Removes any existing role on a workspace resource from a user, group, or workspace (service account) API key. To target a user or service account, pass only the user email; the user must be…

### 107. `elevenlabs_get_workspace_webhooks_route`
**Input**: `include_usages` (opcional), `account` (opcional)

List Workspace Webhooks. List all webhooks for a workspace

### 108. `elevenlabs_create_workspace_webhook_route`
**Input**: `settings`, `account` (opcional)

Create Workspace Webhook. Create a new webhook for the workspace with the specified authentication type.

### 109. `elevenlabs_edit_workspace_webhook_route`
**Input**: `webhook_id`, `is_disabled`, `name`, `retry_enabled` (opcional), `request_headers` (opcional), `events` (opcional), `account` (opcional), `webhook_ids` (opcional)

Update Workspace Webhook. Update the specified workspace webhook Bulk support: accepts webhook_ids for batched execution.

### 110. `elevenlabs_delete_workspace_webhook_route`
**Input**: `webhook_id`, `account` (opcional), `webhook_ids` (opcional)

Delete Workspace Webhook. Delete the specified workspace webhook Bulk support: accepts webhook_ids for batched execution.

### 111. `elevenlabs_get_transcript_by_id`
**Input**: `transcription_id`, `account` (opcional), `transcription_ids` (opcional)

Get Transcript By Id. Retrieve a previously generated transcript by its ID. Bulk support: accepts transcription_ids for batched execution.

### 112. `elevenlabs_delete_transcript_by_id`
**Input**: `transcription_id`, `account` (opcional), `transcription_ids` (opcional)

Delete Transcript By Id. Delete a previously generated transcript by its ID. Bulk support: accepts transcription_ids for batched execution.

### 113. `elevenlabs_get_single_use_token`
**Input**: `token_type`, `account` (opcional)

Create Single Use Token. Generate a time limited single-use token with embedded authentication for frontend clients.

### 114. `elevenlabs_list_speech_engines`
**Input**: `page_size` (opcional), `search` (opcional), `sort_direction` (opcional), `sort_by` (opcional), `cursor` (opcional), `account` (opcional)

List Speech Engines. Returns a paginated list of Speech Engine resources.

### 115. `elevenlabs_create_speech_engine`
**Input**: `name` (opcional), `speech_engine`, `asr` (opcional), `tts` (opcional), `turn` (opcional), `vad` (opcional), `conversation` (opcional), `privacy` (opcional), `call_limits` (opcional), `language` (opcional), `tags` (opcional), `overrides` (opcional), `account` (opcional)

Create Speech Engine. Create a new Speech Engine resource

### 116. `elevenlabs_get_speech_engine`
**Input**: `speech_engine_id`, `account` (opcional), `speech_engine_ids` (opcional)

Get Speech Engine. Retrieve a Speech Engine resource Bulk support: accepts speech_engine_ids for batched execution.

### 117. `elevenlabs_update_speech_engine`
**Input**: `speech_engine_id`, `name` (opcional), `speech_engine` (opcional), `asr` (opcional), `tts` (opcional), `turn` (opcional), `vad` (opcional), `conversation` (opcional), `privacy` (opcional), `call_limits` (opcional), `language` (opcional), `tags` (opcional), `overrides` (opcional), `account` (opcional), `speech_engine_ids` (opcional)

Update Speech Engine. Update a Speech Engine resource (partial update) Bulk support: accepts speech_engine_ids for batched execution.

### 118. `elevenlabs_delete_speech_engine`
**Input**: `speech_engine_id`, `account` (opcional), `speech_engine_ids` (opcional)

Delete Speech Engine. Delete a Speech Engine resource Bulk support: accepts speech_engine_ids for batched execution.

### 119. `elevenlabs_compose_plan`
**Input**: `prompt`, `music_length_ms` (opcional), `source_composition_plan` (opcional), `model_id` (opcional), `account` (opcional), `model_ids` (opcional)

Generate Composition Plan. Generate a composition plan from a prompt. Bulk support: accepts model_ids for batched execution.

### 120. `elevenlabs_generate`
**Input**: `output_format` (opcional), `prompt` (opcional), `generation_mode` (opcional), `music_prompt` (opcional), `lyrics_text` (opcional), `composition_plan` (opcional), `music_length_ms` (opcional), `model_id` (opcional), `seed` (opcional), `force_instrumental` (opcional), `finetune_id` (opcional), `finetune_strength` (opcional), `use_phonetic_names` (opcional), `respect_sections_durations` (opcional), `store_for_inpainting` (opcional), `sign_with_c2pa` (opcional), `account` (opcional), `model_ids` (opcional), `finetune_ids` (opcional)

Compose Music. Compose a song from a prompt or a composition plan. Bulk support: accepts model_ids, finetune_ids for batched execution.

### 121. `elevenlabs_get_finetunes`
**Input**: `cursor` (opcional), `page_size` (opcional), `visibility` (opcional), `created_by` (opcional), `sort` (opcional), `sort_direction` (opcional), `account` (opcional)

Get Music Finetunes. List music finetunes accessible to you (your own, workspace-shared, and ElevenLabs-curated), with optional filtering, sorting, and cursor pagination.

### 122. `elevenlabs_get_finetune`
**Input**: `finetune_id`, `account` (opcional), `finetune_ids` (opcional)

Get Music Finetune. Get a music finetune. Bulk support: accepts finetune_ids for batched execution.

### 123. `elevenlabs_update_finetune`
**Input**: `finetune_id`, `name` (opcional), `tags` (opcional), `primary_genre` (opcional), `visibility` (opcional), `account` (opcional), `finetune_ids` (opcional)

Update Music Finetune. Update a music finetune. Bulk support: accepts finetune_ids for batched execution.

### 124. `elevenlabs_delete_finetune`
**Input**: `finetune_id`, `account` (opcional), `finetune_ids` (opcional)

Delete Music Finetune. Delete a music finetune Bulk support: accepts finetune_ids for batched execution.

### 125. `elevenlabs_public_list_orders`
**Input**: `page_size` (opcional), `offset` (opcional), `status` (opcional), `start_date` (opcional), `end_date` (opcional), `account` (opcional)

List Orders. Lists Productions orders in the workspace. Supports filtering by status and date range, with pagination.

### 126. `elevenlabs_public_create_order`
**Input**: `body` (opcional), `account` (opcional)

Create Order. Creates a new Productions order in the workspace. The order starts in the open state and can be configured with items before submission.

### 127. `elevenlabs_public_get_order`
**Input**: `order_id`, `account` (opcional), `order_ids` (opcional)

Get Order. Retrieves full details for a Productions order. Quote and pricing information may not be available immediately; if you wish to see the quote before submission, you may need to poll the order details until i…

### 128. `elevenlabs_public_update_order`
**Input**: `order_id`, `request`, `account` (opcional), `order_ids` (opcional)

Update Order. Updates an open order. Bulk support: accepts order_ids for batched execution.

### 129. `elevenlabs_public_get_media_info`
**Input**: `order_id`, `media_id`, `account` (opcional), `order_ids` (opcional), `media_ids` (opcional)

Get Media Info. Retrieves metadata and a time-limited download URL for a previously uploaded media file. Bulk support: accepts order_ids, media_ids for batched execution.

### 130. `elevenlabs_public_upsert_order_item`
**Input**: `order_id`, `request`, `account` (opcional), `order_ids` (opcional)

Upsert Order Item. Adds or updates an order item on an open order. Returns the item ID and the quoted price. Bulk support: accepts order_ids for batched execution.

### 131. `elevenlabs_public_remove_order_item`
**Input**: `order_id`, `item_id`, `account` (opcional), `order_ids` (opcional), `item_ids` (opcional)

Remove Order Item. Removes an order item from an open order. Bulk support: accepts order_ids, item_ids for batched execution.

### 132. `elevenlabs_public_submit_order`
**Input**: `order_id`, `account` (opcional), `order_ids` (opcional)

Submit Order. Submits an open order for processing. The order must have at least one item. Once submitted, items can no longer be modified. Upon submission, the workspace will be charged for the order. The quote is ba…

### 133. `elevenlabs_public_get_order_deliverables`
**Input**: `order_id`, `account` (opcional), `order_ids` (opcional)

Get Order Deliverables. Retrieves the delivered files for a completed order. Returns an empty list if the order is not yet completed. Bulk support: accepts order_ids for batched execution.

### 134. `elevenlabs_public_get_available_languages`
**Input**: `order_item_kind`, `account` (opcional)

Get Available Languages. Returns the available languages for a given order item kind.

### 135. `elevenlabs_create_pvc_voice`
**Input**: `name`, `language`, `description` (opcional), `labels` (opcional), `account` (opcional)

Create Pvc Voice. Creates a new PVC voice with metadata but no samples

### 136. `elevenlabs_edit_pvc_voice`
**Input**: `voice_id`, `name` (opcional), `language` (opcional), `description` (opcional), `labels` (opcional), `account` (opcional), `voice_ids` (opcional)

Edit Pvc Voice. Edit PVC voice metadata Bulk support: accepts voice_ids for batched execution.

### 137. `elevenlabs_edit_pvc_voice_sample`
**Input**: `voice_id`, `sample_id`, `remove_background_noise` (opcional), `selected_speaker_ids` (opcional), `trim_start_time` (opcional), `trim_end_time` (opcional), `file_name` (opcional), `account` (opcional)

Update Pvc Voice Sample. Update a PVC voice sample - apply noise removal, select speaker, change trim times or file name.

### 138. `elevenlabs_delete_pvc_voice_sample`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Delete Pvc Voice Sample. Delete a sample from a PVC voice. Bulk support: accepts voice_ids, sample_ids for batched execution.

### 139. `elevenlabs_get_pvc_sample_audio`
**Input**: `voice_id`, `sample_id`, `remove_background_noise` (opcional), `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Retrieve Voice Sample Audio. Retrieve the first 30 seconds of voice sample audio with or without noise removal. Bulk support: accepts voice_ids, sample_ids for batched execution.

### 140. `elevenlabs_get_pvc_sample_visual_waveform`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Retrieve Voice Sample Visual Waveform.

### 141. `elevenlabs_get_pvc_sample_speakers`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Retrieve Speaker Separation Status.

### 142. `elevenlabs_start_speaker_separation`
**Input**: `voice_id`, `sample_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional)

Start Speaker Separation. Start speaker separation process for a sample Bulk support: accepts voice_ids, sample_ids for batched execution.

### 143. `elevenlabs_get_speaker_audio`
**Input**: `voice_id`, `sample_id`, `speaker_id`, `account` (opcional), `voice_ids` (opcional), `sample_ids` (opcional), `speaker_ids` (opcional)

Retrieve Separated Speaker Audio.

### 144. `elevenlabs_get_pvc_voice_captcha`
**Input**: `voice_id`, `account` (opcional), `voice_ids` (opcional)

Get Pvc Voice Captcha. Get captcha for PVC voice verification. Bulk support: accepts voice_ids for batched execution.

### 145. `elevenlabs_run_pvc_voice_training`
**Input**: `voice_id`, `model_id` (opcional), `account` (opcional), `voice_ids` (opcional), `model_ids` (opcional)

Run Pvc Training. Start PVC training process for a voice. Bulk support: accepts voice_ids, model_ids for batched execution.

### 146. `elevenlabs_usage_by_product_over_time`
**Input**: `start_time`, `end_time`, `interval_seconds` (opcional), `group_by` (opcional), `filters` (opcional), `time_zone` (opcional), `account` (opcional)

Get Workspace Usage. Returns credit usage broken down by product type over time. The response is a tabular structure with columns, column_types, column_units, and rows.

### 147. `elevenlabs_requests_list`
**Input**: `start_time` (opcional), `end_time` (opcional), `limit` (opcional), `sort` (opcional), `filters` (opcional), `search` (opcional), `account` (opcional)

List Api Requests. Returns a list of API requests. Supports filtering by time range, column filters, and search terms. At least one of start_time or end_time must be provided. An optional sort parameter controls times…

### 148. `elevenlabs_redirect_to_mintlify`
**Input**: `account` (opcional)

Redirect To Mintlify

### 149. `elevenlabs_list_accounts`
**Input**: nenhum input

Lista as contas conectadas neste MCP (id, email, label).

## Prompts de exemplo

```
Liste as vozes disponíveis na minha conta do ElevenLabs
Gere um áudio dizendo 'bom dia, time' com a voz Rachel
Quantos créditos ainda tenho neste ciclo?
```
