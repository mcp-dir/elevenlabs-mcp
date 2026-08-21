# ElevenLabs

### ElevenLabs para Claude, ChatGPT e agentes de IA

ElevenLabs em linguagem natural: gere fala em qualquer idioma, crie e gerencie vozes, componha música, dublagem, dicionários de pronúncia, histórico e uso da conta. Você conecta com a sua própria API key do ElevenLabs, e os créditos saem da sua assinatura.

- 📊 **149 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `ElevenLabs` e **URL** `https://api.mcp.ai/p_elevenlabs`.

### Cursor

[➕ Instalar ElevenLabs no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=elevenlabs&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9lbGV2ZW5sYWJzIn0=)

### VS Code (Copilot Chat)

[➕ Instalar ElevenLabs no VS Code](vscode:mcp/install?name=elevenlabs&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_elevenlabs%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_elevenlabs
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Liste as vozes disponíveis na minha conta do ElevenLabs
Gere um áudio dizendo 'bom dia, time' com a voz Rachel
Quantos créditos ainda tenho neste ciclo?
```

---

## 149 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `elevenlabs_get_speech_history` | List Generated Items. Returns a list of your generated audio (e.g. text to speech, speech to speech, Studio, dubbing). Music and SFX generations are not included and cannot currently be retrieved via the API. Bulk sup… |
| `elevenlabs_get_speech_history_item_by_id` | Get History Item. Retrieves a history item. Bulk support: accepts history_item_ids for batched execution. |
| `elevenlabs_delete_speech_history_item` | Delete History Item. Delete a history item by its ID Bulk support: accepts history_item_ids for batched execution. |
| `elevenlabs_get_audio_full_from_speech_history_item` | Get Audio From History Item. Returns the audio of an history item. Bulk support: accepts history_item_ids for batched execution. |
| `elevenlabs_download_speech_history_items` | Download History Items. Download one or more history items. If one history item ID is provided, we will return a single audio file. If more than one history item IDs are provided, we will provide the history items pac… |
| `elevenlabs_sound_generation` | Sound Generation. Turn text into sound effects for your videos, voice-overs or video games using the most advanced sound effects models in the world. Bulk support: accepts model_ids for batched execution. |
| `elevenlabs_get_audio_isolation_history` | Get Audio Isolation History. Returns a list of all your audio isolation generations. |
| `elevenlabs_delete_audio_isolation_history_item` | Delete Audio Isolation History Item. |
| `elevenlabs_delete_sample` | Delete Sample. Removes a sample by its ID. Bulk support: accepts voice_ids, sample_ids for batched execution. |
| `elevenlabs_get_audio_from_sample` | Get Audio From Sample. Returns the audio corresponding to a sample attached to a voice. Bulk support: accepts voice_ids, sample_ids for batched execution. |
| `elevenlabs_text_to_speech_full` | Text To Speech. Converts text into speech using a voice of your choice and returns audio. |
| `elevenlabs_text_to_dialogue` | Text To Dialogue (Multi-Voice). |
| `elevenlabs_create_voice` | Create A New Voice From Voice Preview. |
| `elevenlabs_text_to_voice_design` | Design A Voice.. Design a voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To create a voice use the genera… |
| `elevenlabs_text_to_voice_remix` | Remix A Voice.. Remix an existing voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To create a voice use th… |
| `elevenlabs_text_to_voice_preview_stream` | Text To Voice Preview Streaming. |
| `elevenlabs_get_user_info` | Get User Info. Gets information about the user |
| `elevenlabs_get_user_subscription_info` | Get User Subscription Info. Gets extended information about the users subscription |
| `elevenlabs_get_voice_settings_default` | Get Default Voice Settings.. Gets the default settings for voices. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app. |
| `elevenlabs_get_voice_settings` | Get Voice Settings. Returns the settings for a specific voice. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app. Bulk… |
| `elevenlabs_edit_voice_settings` | Edit Voice Settings. Edit your settings for a specific voice. "similarity_boost" corresponds to "Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in the web app. Bulk… |
| `elevenlabs_get_voice_accents` | Get Voice Accents. Gets the list of available accents in the shared voice library. Bulk support: accepts model_ids for batched execution. |
| `elevenlabs_get_voices` | List Voices. Returns a list of all available voices for a user. Stops working once the user's workspace exceeds 500 voices. |
| `elevenlabs_get_voice_by_id` | Get Voice. Returns metadata about a specific voice. Bulk support: accepts voice_ids for batched execution. |
| `elevenlabs_delete_voice` | Delete Voice. Deletes a voice by its ID. Bulk support: accepts voice_ids for batched execution. |
| `elevenlabs_get_user_voices_v2` | Get Voices V2. Gets a list of all available voices for a user with search, filtering and pagination. |
| `elevenlabs_replicate_voice_to_isolated_environment` | Replicate Voice To Isolated Environment. |
| `elevenlabs_add_sharing_voice` | Add Shared Voice. Add a shared voice to your collection of voices. Bulk support: accepts public_user_ids, voice_ids for batched execution. |
| `elevenlabs_create_podcast` | Create Podcast. Create and auto-convert a podcast project. Currently, the LLM cost is covered by us but you will still be charged for the audio generation. In the future, you will be charged for both the LLM and audio… |
| `elevenlabs_update_pronunciation_dictionaries` | Create Pronunciation Dictionaries. |
| `elevenlabs_get_projects` | List Studio Projects. Returns a list of your Studio projects with metadata. |
| `elevenlabs_get_project_by_id` | Get Studio Project. Returns information about a specific Studio project. This endpoint returns more detailed information about a project than `GET /v1/studio`. Bulk support: accepts project_ids, share_ids for batched… |
| `elevenlabs_edit_project` | Update Studio Project. Updates the specified Studio project by setting the values of the parameters passed. Bulk support: accepts project_ids, default_title_voice_ids, default_paragraph_voice_ids for batched execution. |
| `elevenlabs_delete_project` | Delete Studio Project. Deletes a Studio project. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_convert_project_endpoint` | Convert Studio Project. Starts conversion of a Studio project and all of its chapters. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_get_project_snapshots` | List Studio Project Snapshots. |
| `elevenlabs_get_project_snapshot_endpoint` | Get Project Snapshot. Returns the project snapshot. Bulk support: accepts project_ids, project_snapshot_ids for batched execution. |
| `elevenlabs_stream_project_snapshot_archive_60141b` | Stream Archive With Studio Project Audio. |
| `elevenlabs_get_chapters` | List Chapters. Returns a list of a Studio project's chapters. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_add_chapter` | Create Chapter. Creates a new chapter either as blank or from a URL. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_get_chapter_by_id_endpoint` | Get Chapter. Returns information about a specific chapter. Bulk support: accepts project_ids, chapter_ids for batched execution. |
| `elevenlabs_edit_chapter` | Update Chapter. Updates a chapter. Bulk support: accepts project_ids, chapter_ids for batched execution. |
| `elevenlabs_delete_chapter_endpoint` | Delete Chapter. Deletes a chapter. Bulk support: accepts project_ids, chapter_ids for batched execution. |
| `elevenlabs_convert_chapter_endpoint` | Convert Chapter. Starts conversion of a specific chapter. Bulk support: accepts project_ids, chapter_ids for batched execution. |
| `elevenlabs_get_chapter_snapshots` | List Chapter Snapshots. Gets information about all the snapshots of a chapter. Each snapshot can be downloaded as audio. Whenever a chapter is converted a snapshot will automatically be created. Bulk support: accepts… |
| `elevenlabs_get_chapter_snapshot_endpoint` | Get Chapter Snapshot. Returns the chapter snapshot. Bulk support: accepts project_ids, chapter_ids, chapter_snapshot_ids for batched execution. |
| `elevenlabs_stream_chapter_snapshot_audio` | Stream Chapter Audio. Stream the audio from a chapter snapshot. Use `GET /v1/studio/projects/{project_id}/chapters/{chapter_id}/snapshots` to return the snapshots of a chapter. Bulk support: accepts project_ids, chapt… |
| `elevenlabs_get_project_muted_tracks_endpoint` | Get Project Muted Tracks. Returns a list of chapter IDs that have muted tracks in a project. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_dubbing_project_list` | List Dubbing Projects. List the workspace's dubbing projects (cursor-paginated). |
| `elevenlabs_dubbing_project_get` | Get Dubbing Project. Full project detail, including its language target ids. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_dubbing_project_delete` | Delete Dubbing Project. Delete a project and its language targets. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_dubbing_language_list` | List Dubbing Language Targets. |
| `elevenlabs_dubbing_language_create` | Create Dubbing Language Target. |
| `elevenlabs_dubbing_language_get` | Get Dubbing Language Target. Full language-target detail. Bulk support: accepts project_ids, language_ids for batched execution. |
| `elevenlabs_dubbing_language_delete` | Delete Dubbing Language Target. |
| `elevenlabs_dubbing_transcript_get` | Get Dubbing Transcript. The project's source transcript, as editable segments. Bulk support: accepts project_ids for batched execution. |
| `elevenlabs_dubbing_transcript_segment_update` | Update Dubbing Transcript Segment. |
| `elevenlabs_dubbing_transcript_segment_delete` | Delete Dubbing Transcript Segment. |
| `elevenlabs_dubbing_transcript_segments_update` | Update Dubbing Transcript Segments. |
| `elevenlabs_dubbing_transcript_segment_add` | Add Dubbing Transcript Segment. |
| `elevenlabs_dubbing_target_transcript_get` | Get Dubbing Target Transcript. |
| `elevenlabs_dubbing_target_transcript_segmen_b565e6` | Update Dubbing Target Transcript Segment. |
| `elevenlabs_dubbing_target_transcript_segmen_fa79db` | Update Dubbing Target Transcript Segments. |
| `elevenlabs_dubbing_target_transcript_regenerate` | Regenerate Dubbing Target. Enterprise only. Re-dub a target from its edited transcript, re-synthesizing only the edited regions (charged like a generation). Conflicts when the target has no edits to apply -- nothing i… |
| `elevenlabs_list_dubs` | List Dubs. List the dubs you have access to. |
| `elevenlabs_get_dubbed_metadata` | Get Dubbing. Returns metadata about a dubbing project, including whether it's still in progress or not Bulk support: accepts dubbing_ids for batched execution. |
| `elevenlabs_delete_dubbing` | Delete Dubbing. Deletes a dubbing project. Bulk support: accepts dubbing_ids for batched execution. |
| `elevenlabs_get_dubbed_file` | Get Dubbed File. Returns dub as a streamed MP3 or MP4 file. If this dub has been edited using Dubbing Studio you need to use the resource render endpoint as this endpoint only returns the original automatic dub result… |
| `elevenlabs_get_dubbing_transcripts` | Retrieve A Transcript. Fetch the transcript for one of the languages in a dub. Bulk support: accepts dubbing_ids for batched execution. |
| `elevenlabs_get_models` | Get Models. Gets a list of available models. |
| `elevenlabs_get_audio_native_project_setting_340fd1` | Get Audio Native Project Settings. |
| `elevenlabs_audio_native_update_content_from_url` | Update Audio-Native Content From Url. |
| `elevenlabs_get_library_voices` | Get Voices. Retrieves a list of shared voices. Bulk support: accepts owner_ids for batched execution. |
| `elevenlabs_add_from_rules` | Add A Pronunciation Dictionary. |
| `elevenlabs_get_pronunciation_dictionary_metadata` | Get Metadata For A Pronunciation Dictionary. |
| `elevenlabs_patch_pronunciation_dictionary` | Update Pronunciation Dictionary. |
| `elevenlabs_set_rules` | Set Rules On The Pronunciation Dictionary. |
| `elevenlabs_add_rules` | Add Rules To The Pronunciation Dictionary. |
| `elevenlabs_remove_rules` | Remove Rules From The Pronunciation Dictionary. |
| `elevenlabs_get_pronunciation_dictionary_ver_45baf2` | Get A Pls File With A Pronunciation Dictionary Version Rules. |
| `elevenlabs_get_pronunciation_dictionaries_metadata` | Get Pronunciation Dictionaries. |
| `elevenlabs_disable` | Disable Api Key. Disable the API key used to authenticate this request. Requires the query parameter `api_key_name=self` as an explicit confirmation. |
| `elevenlabs_set_third_party_disabling_policy` | Set Workspace Third-Party Disabling Policy. |
| `elevenlabs_get_service_account_api_keys_route` | Get Service Account Api Keys Route. |
| `elevenlabs_create_service_account_api_key` | Create Service Account Api Key. |
| `elevenlabs_edit_service_account_api_key` | Edit Service Account Api Key. Update an existing API key for a service account Bulk support: accepts service_account_user_ids, api_key_ids for batched execution. |
| `elevenlabs_delete_service_account_api_key` | Delete Service Account Api Key. |
| `elevenlabs_get_workspace_audit_logs` | Get Workspace Audit Logs. Returns the audit log for the workspace. Requires enterprise tier and the audit_log_read permission. |
| `elevenlabs_list_auth_connections` | Get Workspace Auth Connections. |
| `elevenlabs_create_auth_connection` | Create Workspace Auth Connection. |
| `elevenlabs_update_auth_connection` | Update Workspace Auth Connection. |
| `elevenlabs_delete_auth_connection` | Delete Workspace Auth Connection. |
| `elevenlabs_get_workspace_service_accounts` | Get Workspace Service Accounts. |
| `elevenlabs_create_service_account` | Create Service Account. Create a new service account in the workspace. By default, a workspace can have up to 20 service accounts. Enterprise customers may request an increase to this limit, up to 100. |
| `elevenlabs_get_groups_endpoint` | Get All Groups. Get all groups in the workspace |
| `elevenlabs_search_groups` | Search User Groups. Searches for user groups in the workspace. Multiple or no groups may be returned. |
| `elevenlabs_remove_member` | Delete Member From User Group. |
| `elevenlabs_add_member` | Add Member To User Group. Adds a member of your workspace to the specified group. Requires `group_members_manage` permission. Bulk support: accepts group_ids for batched execution. |
| `elevenlabs_invite_user` | Invite User. Sends an email invitation to join your workspace to the provided email. If the user doesn't have an account they will be prompted to create one. If the user accepts this invite they will be added as a use… |
| `elevenlabs_invite_users_bulk` | Invite Multiple Users. Sends email invitations to join your workspace to the provided emails. Requires all email addresses to be part of a verified domain. If the users don't have an account they will be prompted to c… |
| `elevenlabs_delete_invite` | Delete Existing Invitation. Invalidates an existing email invitation. The invitation will still show up in the inbox it has been delivered to, but activating it to join the workspace won't work. This endpoint may only… |
| `elevenlabs_get_workspace_members` | Get Workspace Members. Gets a list of all members of the workspace, including locked members. Service accounts are excluded. Requires the workspace_members_read permission. |
| `elevenlabs_update_workspace_member` | Update Member. Updates attributes of a workspace member. Apart from the email identifier, all parameters will remain unchanged unless specified. This endpoint may only be called by workspace administrators. |
| `elevenlabs_get_resource_metadata` | Get Resource. Gets the metadata of a resource by ID. Bulk support: accepts resource_ids for batched execution. |
| `elevenlabs_share_resource_endpoint` | Share Workspace Resource. Grants a role (one of 'admin', 'editor', 'commenter', or 'viewer') on a workspace resource to a user, group, or workspace (service account) API key. This overrides any existing role the targe… |
| `elevenlabs_unshare_resource_endpoint` | Unshare Workspace Resource. Removes any existing role on a workspace resource from a user, group, or workspace (service account) API key. To target a user or service account, pass only the user email; the user must be… |
| `elevenlabs_get_workspace_webhooks_route` | List Workspace Webhooks. List all webhooks for a workspace |
| `elevenlabs_create_workspace_webhook_route` | Create Workspace Webhook. Create a new webhook for the workspace with the specified authentication type. |
| `elevenlabs_edit_workspace_webhook_route` | Update Workspace Webhook. Update the specified workspace webhook Bulk support: accepts webhook_ids for batched execution. |
| `elevenlabs_delete_workspace_webhook_route` | Delete Workspace Webhook. Delete the specified workspace webhook Bulk support: accepts webhook_ids for batched execution. |
| `elevenlabs_get_transcript_by_id` | Get Transcript By Id. Retrieve a previously generated transcript by its ID. Bulk support: accepts transcription_ids for batched execution. |
| `elevenlabs_delete_transcript_by_id` | Delete Transcript By Id. Delete a previously generated transcript by its ID. Bulk support: accepts transcription_ids for batched execution. |
| `elevenlabs_get_single_use_token` | Create Single Use Token. Generate a time limited single-use token with embedded authentication for frontend clients. |
| `elevenlabs_list_speech_engines` | List Speech Engines. Returns a paginated list of Speech Engine resources. |
| `elevenlabs_create_speech_engine` | Create Speech Engine. Create a new Speech Engine resource |
| `elevenlabs_get_speech_engine` | Get Speech Engine. Retrieve a Speech Engine resource Bulk support: accepts speech_engine_ids for batched execution. |
| `elevenlabs_update_speech_engine` | Update Speech Engine. Update a Speech Engine resource (partial update) Bulk support: accepts speech_engine_ids for batched execution. |
| `elevenlabs_delete_speech_engine` | Delete Speech Engine. Delete a Speech Engine resource Bulk support: accepts speech_engine_ids for batched execution. |
| `elevenlabs_compose_plan` | Generate Composition Plan. Generate a composition plan from a prompt. Bulk support: accepts model_ids for batched execution. |
| `elevenlabs_generate` | Compose Music. Compose a song from a prompt or a composition plan. Bulk support: accepts model_ids, finetune_ids for batched execution. |
| `elevenlabs_get_finetunes` | Get Music Finetunes. List music finetunes accessible to you (your own, workspace-shared, and ElevenLabs-curated), with optional filtering, sorting, and cursor pagination. |
| `elevenlabs_get_finetune` | Get Music Finetune. Get a music finetune. Bulk support: accepts finetune_ids for batched execution. |
| `elevenlabs_update_finetune` | Update Music Finetune. Update a music finetune. Bulk support: accepts finetune_ids for batched execution. |
| `elevenlabs_delete_finetune` | Delete Music Finetune. Delete a music finetune Bulk support: accepts finetune_ids for batched execution. |
| `elevenlabs_public_list_orders` | List Orders. Lists Productions orders in the workspace. Supports filtering by status and date range, with pagination. |
| `elevenlabs_public_create_order` | Create Order. Creates a new Productions order in the workspace. The order starts in the open state and can be configured with items before submission. |
| `elevenlabs_public_get_order` | Get Order. Retrieves full details for a Productions order. Quote and pricing information may not be available immediately; if you wish to see the quote before submission, you may need to poll the order details until i… |
| `elevenlabs_public_update_order` | Update Order. Updates an open order. Bulk support: accepts order_ids for batched execution. |
| `elevenlabs_public_get_media_info` | Get Media Info. Retrieves metadata and a time-limited download URL for a previously uploaded media file. Bulk support: accepts order_ids, media_ids for batched execution. |
| `elevenlabs_public_upsert_order_item` | Upsert Order Item. Adds or updates an order item on an open order. Returns the item ID and the quoted price. Bulk support: accepts order_ids for batched execution. |
| `elevenlabs_public_remove_order_item` | Remove Order Item. Removes an order item from an open order. Bulk support: accepts order_ids, item_ids for batched execution. |
| `elevenlabs_public_submit_order` | Submit Order. Submits an open order for processing. The order must have at least one item. Once submitted, items can no longer be modified. Upon submission, the workspace will be charged for the order. The quote is ba… |
| `elevenlabs_public_get_order_deliverables` | Get Order Deliverables. Retrieves the delivered files for a completed order. Returns an empty list if the order is not yet completed. Bulk support: accepts order_ids for batched execution. |
| `elevenlabs_public_get_available_languages` | Get Available Languages. Returns the available languages for a given order item kind. |
| `elevenlabs_create_pvc_voice` | Create Pvc Voice. Creates a new PVC voice with metadata but no samples |
| `elevenlabs_edit_pvc_voice` | Edit Pvc Voice. Edit PVC voice metadata Bulk support: accepts voice_ids for batched execution. |
| `elevenlabs_edit_pvc_voice_sample` | Update Pvc Voice Sample. Update a PVC voice sample - apply noise removal, select speaker, change trim times or file name. |
| `elevenlabs_delete_pvc_voice_sample` | Delete Pvc Voice Sample. Delete a sample from a PVC voice. Bulk support: accepts voice_ids, sample_ids for batched execution. |
| `elevenlabs_get_pvc_sample_audio` | Retrieve Voice Sample Audio. Retrieve the first 30 seconds of voice sample audio with or without noise removal. Bulk support: accepts voice_ids, sample_ids for batched execution. |
| `elevenlabs_get_pvc_sample_visual_waveform` | Retrieve Voice Sample Visual Waveform. |
| `elevenlabs_get_pvc_sample_speakers` | Retrieve Speaker Separation Status. |
| `elevenlabs_start_speaker_separation` | Start Speaker Separation. Start speaker separation process for a sample Bulk support: accepts voice_ids, sample_ids for batched execution. |
| `elevenlabs_get_speaker_audio` | Retrieve Separated Speaker Audio. |
| `elevenlabs_get_pvc_voice_captcha` | Get Pvc Voice Captcha. Get captcha for PVC voice verification. Bulk support: accepts voice_ids for batched execution. |
| `elevenlabs_run_pvc_voice_training` | Run Pvc Training. Start PVC training process for a voice. Bulk support: accepts voice_ids, model_ids for batched execution. |
| `elevenlabs_usage_by_product_over_time` | Get Workspace Usage. Returns credit usage broken down by product type over time. The response is a tabular structure with columns, column_types, column_units, and rows. |
| `elevenlabs_requests_list` | List Api Requests. Returns a list of API requests. Supports filtering by time range, column filters, and search terms. At least one of start_time or end_time must be provided. An optional sort parameter controls times… |
| `elevenlabs_redirect_to_mintlify` | Redirect To Mintlify |
| `elevenlabs_list_accounts` | Lista as contas conectadas neste MCP (id, email, label). |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Grátis.

---

## Privacidade & LGPD

- **Sub-processadores**: ElevenLabs, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_elevenlabs`.


---

## Suporte

- 📧 [elevenlabs@mcp.ai](mailto:elevenlabs@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/elevenlabs-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_elevenlabs` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
