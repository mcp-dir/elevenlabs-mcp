---
name: elevenlabs-mcp
description: Skill da REST API do ElevenLabs na MCP.AI: 148 endpoints em /api/elevenlabs. ElevenLabs em linguagem natural: gere fala em qualquer idioma, crie e gerencie vozes, componha música, dublagem, dicionários de pronúncia, histórico e uso da conta. Você conecta com a sua própria API key do ElevenLabs, e os créditos saem da sua assinatura. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# ElevenLabs — REST API skill

Você tem acesso à **ElevenLabs** REST API na MCP.AI.

> ElevenLabs em linguagem natural: gere fala em qualquer idioma, crie e gerencie vozes, componha música, dublagem, dicionários de pronúncia, histórico e uso da conta. Você conecta com a sua própria API key do ElevenLabs, e os créditos saem da sua assinatura.

## Base URL

```
https://api.mcp.ai/api/elevenlabs
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/elevenlabs/add/chapter \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"project_id":"...","name":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/elevenlabs/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (148)

#### `elevenlabs_add_chapter`

Create Chapter. Creates a new chapter either as blank or from a URL. _(POST /api/elevenlabs/add/chapter)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `name` | string | Sim | The name of the chapter, used for identification only. |
| `from_url` | string | Não | An optional URL from which we will extract content to initialize the Studio project. If this is set, 'from_url' and 'from_content' must be null. If neither 'from_url', 'from_document', 'from_content' are provided we will initialize the Studio project as blank. |

#### `elevenlabs_add_from_rules`

Add A Pronunciation Dictionary. _(POST /api/elevenlabs/add/from/rules)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `rules` | object[] | Sim | List of pronunciation rules. Rule can be either:     an alias rule: {'string_to_replace': 'a', 'type': 'alias', 'alias': 'b', }     or a phoneme rule: {'string_to_replace': 'a', 'type': 'phoneme', 'phoneme': 'b', 'alphabet': 'ipa' } |
| `name` | string | Sim | The name of the pronunciation dictionary, used for identification only. |
| `description` | string | Não | A description of the pronunciation dictionary, used for identification only. |
| `workspace_access` | string | Não | Should be one of 'admin', 'editor' or 'viewer'. If not provided, defaults to no access. (admin, editor, commenter, viewer) |

#### `elevenlabs_add_member`

Add Member To User Group. Adds a member of your workspace to the specified group. Requires `group_members_manage` permission. _(POST /api/elevenlabs/add/member)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `group_id` | string | Sim | The ID of the target group. |
| `email` | string | Sim | The email of the target workspace member. |

#### `elevenlabs_add_rules`

Add Rules To The Pronunciation Dictionary. _(POST /api/elevenlabs/add/rules)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pronunciation_dictionary_id` | string | Sim | The id of the pronunciation dictionary |
| `rules` | object[] | Sim | List of pronunciation rules. Rule can be either:     an alias rule: {'string_to_replace': 'a', 'type': 'alias', 'alias': 'b', }     or a phoneme rule: {'string_to_replace': 'a', 'type': 'phoneme', 'phoneme': 'b', 'alphabet': 'ipa' } |

#### `elevenlabs_add_sharing_voice`

Add Shared Voice. Add a shared voice to your collection of voices. _(POST /api/elevenlabs/add/sharing/voice)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `public_user_id` | string | Sim | Public user ID used to publicly identify ElevenLabs users. |
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `new_name` | string | Sim | The name that identifies this voice. This will be displayed in the dropdown of the website. |
| `bookmarked` | boolean | Não | Bookmarked |

#### `elevenlabs_audio_native_update_content_from_url`

Update Audio-Native Content From Url. _(POST /api/elevenlabs/audio/native/update/content/from/url)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `url` | string | Sim | URL of the page to extract content from. |
| `author` | string | Não | Author used in the player and inserted at the start of the uploaded article. If not provided, the default author set in the Player settings is used. |
| `title` | string | Não | Title used in the player and inserted at the top of the uploaded article. If not provided, the default title set in the Player settings is used. |

#### `elevenlabs_compose_plan`

Generate Composition Plan. Generate a composition plan from a prompt. _(POST /api/elevenlabs/compose/plan)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `prompt` | string | Sim | A simple text prompt to compose a plan from. |
| `music_length_ms` | integer | Não | The length of the composition plan to generate in milliseconds. Must be between 3000ms and 600000ms. Optional - if not provided, the model will choose a length based on the prompt. |
| `source_composition_plan` | object | Não | An optional composition plan to use as a source for the new composition plan. |
| `model_id` | string | Não | The model to use for the generation. (music_v1, music_v2) |

#### `elevenlabs_convert_chapter_endpoint`

Convert Chapter. Starts conversion of a specific chapter. _(POST /api/elevenlabs/convert/chapter/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |

#### `elevenlabs_convert_project_endpoint`

Convert Studio Project. Starts conversion of a Studio project and all of its chapters. _(POST /api/elevenlabs/convert/project/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_create_auth_connection`

Create Workspace Auth Connection. _(POST /api/elevenlabs/create/auth/connection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `body` | object | Sim | Auth connection to create |

#### `elevenlabs_create_podcast`

Create Podcast. Create and auto-convert a podcast project. Currently, the LLM cost is covered by us but you will still be charged for the audio generation. In the future, you will be charged for both _(POST /api/elevenlabs/create/podcast)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `safety-identifier` | string | Não | Used for moderation. Your workspace must be allowlisted to use this feature. |
| `model_id` | string | Sim | The ID of the model to be used for this Studio project, you can query GET /v1/models to list all available models. |
| `mode` | object | Sim | The type of podcast to generate. Can be 'conversation', an interaction between two voices, or 'bulletin', a monologue. |
| `source` | object|object[] | Sim | The source content for the Podcast. |
| `quality_preset` | string | Não |  (standard, high, ultra, ultra_lossless) |
| `duration_scale` | string | Não | Duration of the generated podcast. Must be one of: short - produces podcasts shorter than 3 minutes. default - produces podcasts roughly between 3-7 minutes. long - produces podcasts longer than 7 minutes.  (short, default, long) |
| `language` | string | Não | An optional language of the Studio project. Two-letter language code (ISO 639-1). |
| `intro` | string | Não | The intro text that will always be added to the beginning of the podcast. |
| `outro` | string | Não | The outro text that will always be added to the end of the podcast. |
| `instructions_prompt` | string | Não | Additional instructions prompt for the podcast generation used to adjust the podcast's style and tone. |
| `highlights` | string[] | Não | A brief summary or highlights of the Studio project's content, providing key points or themes. This should be between 10 and 70 characters. |
| `callback_url` | string | Não |      A url that will be called by our service when the Studio project is converted. Request will contain a json blob containing the status of the conversion     Messages:     1. When project was converted successfully:     {       type: "project_conversion_status",       event_timestamp: 1234567890,       data: {         request_id: "1234567890",         project_id: "21m00Tcm4TlvDq8ikWAM",         conversion_status: "success",         project_snapshot_id: "22m00Tcm4TlvDq8ikMAT",         error_details: None,       }     }     2. When project conversion failed:     {       type: "project_conversion_status",       event_timestamp: 1234567890,       data: {         request_id: "1234567890",         project_id: "21m00Tcm4TlvDq8ikWAM",         conversion_status: "error",         project_snapshot_id: None,         error_details: "Error details if conversion failed"       }     }      3. When chapter was converted successfully:     {       type: "chapter_conversion_status",       event_timestamp: 1234567890,       data: {         request_id: "1234567890",         project_id: "21m00Tcm4TlvDq8ikWAM",         chapter_id: "22m00Tcm4TlvDq8ikMAT",         conversion_status: "success",         chapter_snapshot_id: "23m00Tcm4TlvDq8ikMAV",         error_details: None,       }     }     4. When chapter conversion failed:     {       type: "chapter_conversion_status",       event_timestamp: 1234567890,       data: {         request_id: "1234567890",         project_id: "21m00Tcm4TlvDq8ikWAM",         chapter_id: "22m00Tcm4TlvDq8ikMAT",         conversion_status: "error",         chapter_snapshot_id: None,         error_details: "Error details if conversion failed"       }     }      |
| `apply_text_normalization` | string | Não |      This parameter controls text normalization with four modes: 'auto', 'on', 'apply_english' and 'off'.     When set to 'auto', the system will automatically decide whether to apply text normalization     (e.g., spelling out numbers). With 'on', text normalization will always be applied, while     with 'off', it will be skipped. 'apply_english' is the same as 'on' but will assume that text is in English.      (auto, on, off, apply_english) |

#### `elevenlabs_create_pvc_voice`

Create Pvc Voice. Creates a new PVC voice with metadata but no samples _(POST /api/elevenlabs/create/pvc/voice)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `name` | string | Sim | The name that identifies this voice. This will be displayed in the dropdown of the website. |
| `language` | string | Sim | Language used in the samples. |
| `description` | string | Não | Description to use for the created voice. |
| `labels` | object | Não | Labels for the voice. Keys can be language, accent, gender, or age. |

#### `elevenlabs_create_service_account`

Create Service Account. Create a new service account in the workspace. By default, a workspace can have up to 20 service accounts. Enterprise customers may request an increase to this limit, up to 100 _(POST /api/elevenlabs/create/service/account)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `name` | string | Sim | Name |
| `default_sharing_groups` | object[] | Não | List of groups with their permission levels to share with by default. Each entry should specify a group_id and a permission_level (admin, editor, or viewer). |

#### `elevenlabs_create_service_account_api_key`

Create Service Account Api Key. _(POST /api/elevenlabs/create/service/account/api/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `service_account_user_id` | string | Sim | Service Account User Id |
| `name` | string | Sim | Name |
| `permissions` | string[]|string | Sim | The permissions of the XI API. |
| `character_limit` | integer | Não | The character limit of the XI API key. If provided this will limit the usage of this api key to n characters per month where n is the chosen value. Requests that incur charges will fail after reaching this monthly limit. |
| `allowed_ips` | string[] | Não | List of IP addresses or CIDR ranges allowed to use this API key. Each entry may be a CIDR range (e.g. '10.0.0.0/24') or a bare IP address (normalized to /32 or /128). On create, omit or pass null to allow all IPs. On update, omit to leave the allowlist unchanged, or pass "clear" to remove it. |
| `third_party_disable_allowed` | boolean | Não | Whether the holder of this key may disable it via the self-disable endpoint. On create, omit or pass null to use the workspace's default (enabled for non-Enterprise plans, disabled for Enterprise plans). On update, omit to leave it unchanged, or pass "clear" to reset it to the workspace default. Only honored for workspaces with self-disable access enabled. |

#### `elevenlabs_create_speech_engine`

Create Speech Engine. Create a new Speech Engine resource _(POST /api/elevenlabs/create/speech/engine)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `name` | string | Não | Name of the speech engine |
| `speech_engine` | object | Sim | SpeechEngineConfig |
| `asr` | object | Não | ASRConversationalConfig |
| `tts` | object | Não | TTSConversationalConfig |
| `turn` | object | Não | BaseTurnConfig |
| `vad` | object | Não | VADConfig |
| `conversation` | object | Não | ConversationConfig |
| `privacy` | object | Não | PrivacyConfig |
| `call_limits` | object | Não | AgentCallLimits |
| `language` | string | Não | Language for the speech engine |
| `tags` | string[] | Não | Tags for categorization |
| `overrides` | object | Não | SpeechEngineConversationInitiationClientDataConfig |

#### `elevenlabs_create_voice`

Create A New Voice From Voice Preview. _(POST /api/elevenlabs/create/voice)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_name` | string | Sim | Name to use for the created voice. |
| `voice_description` | string | Sim | Description to use for the created voice. |
| `generated_voice_id` | string | Sim | The generated_voice_id to create; obtain it from POST /v1/text-to-voice/design, POST /v1/text-to-voice/:voice_id/remix, or the response headers when generating previews. |
| `labels` | object | Não | Optional, metadata to add to the created voice. Defaults to None. |
| `played_not_selected_voice_ids` | string[] | Não | List of voice ids that the user has played but not selected. Used for RLHF. |

#### `elevenlabs_create_workspace_webhook_route`

Create Workspace Webhook. Create a new webhook for the workspace with the specified authentication type. _(POST /api/elevenlabs/create/workspace/webhook/route)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `settings` | object | Sim | Settings for creating an HMAC-authenticated webhook |

#### `elevenlabs_delete_audio_isolation_history_item`

Delete Audio Isolation History Item. _(POST /api/elevenlabs/delete/audio/isolation/history/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `history_item_id` | string | Sim | Identifier of the audio isolation history item. |

#### `elevenlabs_delete_auth_connection`

Delete Workspace Auth Connection. _(POST /api/elevenlabs/delete/auth/connection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_connection_id` | string | Sim | Auth Connection Id |

#### `elevenlabs_delete_chapter_endpoint`

Delete Chapter. Deletes a chapter. _(POST /api/elevenlabs/delete/chapter/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |

#### `elevenlabs_delete_dubbing`

Delete Dubbing. Deletes a dubbing project. _(POST /api/elevenlabs/delete/dubbing)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `dubbing_id` | string | Sim | ID of the dubbing project. |

#### `elevenlabs_delete_finetune`

Delete Music Finetune. Delete a music finetune _(POST /api/elevenlabs/delete/finetune)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `finetune_id` | string | Sim | Finetune Id |

#### `elevenlabs_delete_invite`

Delete Existing Invitation. Invalidates an existing email invitation. The invitation will still show up in the inbox it has been delivered to, but activating it to join the workspace won't work. This _(POST /api/elevenlabs/delete/invite)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Sim | The email of the customer |

#### `elevenlabs_delete_project`

Delete Studio Project. Deletes a Studio project. _(POST /api/elevenlabs/delete/project)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_delete_pvc_voice_sample`

Delete Pvc Voice Sample. Delete a sample from a PVC voice. _(POST /api/elevenlabs/delete/pvc/voice/sample)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |

#### `elevenlabs_delete_sample`

Delete Sample. Removes a sample by its ID. _(POST /api/elevenlabs/delete/sample)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used, you can use GET https://api.elevenlabs.io/v1/voices/{voice_id} to list all the available samples for a voice. |

#### `elevenlabs_delete_service_account_api_key`

Delete Service Account Api Key. _(POST /api/elevenlabs/delete/service/account/api/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `service_account_user_id` | string | Sim | Service Account User Id |
| `api_key_id` | string | Sim | Api Key Id |

#### `elevenlabs_delete_speech_engine`

Delete Speech Engine. Delete a Speech Engine resource _(POST /api/elevenlabs/delete/speech/engine)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `speech_engine_id` | string | Sim | The speech engine ID (accepts seng_ or agent_ prefix) |

#### `elevenlabs_delete_speech_history_item`

Delete History Item. Delete a history item by its ID _(POST /api/elevenlabs/delete/speech/history/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `history_item_id` | string | Sim | History item ID to be used, you can use GET https://api.elevenlabs.io/v1/history to receive a list of history items and their IDs. |

#### `elevenlabs_delete_transcript_by_id`

Delete Transcript By Id. Delete a previously generated transcript by its ID. _(POST /api/elevenlabs/delete/transcript/by/id)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transcription_id` | string | Sim | The unique ID of the transcript to delete |

#### `elevenlabs_delete_voice`

Delete Voice. Deletes a voice by its ID. _(POST /api/elevenlabs/delete/voice)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |

#### `elevenlabs_delete_workspace_webhook_route`

Delete Workspace Webhook. Delete the specified workspace webhook _(POST /api/elevenlabs/delete/workspace/webhook/route)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `webhook_id` | string | Sim | The unique ID for the webhook |

#### `elevenlabs_disable`

Disable Api Key. Disable the API key used to authenticate this request. Requires the query parameter `api_key_name=self` as an explicit confirmation. _(POST /api/elevenlabs/disable)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `api_key_name` | string | Sim | Must be set to `self` to disable the API key used to authenticate this request. Required as an explicit confirmation to avoid accidentally disabling the wrong key. |

#### `elevenlabs_download_speech_history_items`

Download History Items. Download one or more history items. If one history item ID is provided, we will return a single audio file. If more than one history item IDs are provided, we will provide the _(POST /api/elevenlabs/download/speech/history/items)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `history_item_ids` | string[] | Sim | A list of history items to download, you can get IDs of history items and other metadata using the GET https://api.elevenlabs.io/v1/history endpoint. |
| `output_format` | string | Não | Output format to transcode the audio file, can be wav or default. |

#### `elevenlabs_dubbing_language_create`

Create Dubbing Language Target. _(POST /api/elevenlabs/dubbing/language/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the parent dubbing project. |
| `target_language` | string | Sim | BCP-47 language tag to dub the project into (e.g. 'fr', 'es-MX'); must be a language the dubbing model supports. A region-qualified tag must be one of the supported dialects. |
| `voice_settings` | object | Não | Voice settings applied to the whole language (e.g. cloning strength). |
| `translations` | object | Não | Enterprise only. Optional translations to use instead of machine translation. A map from each source segment's external_id (or its id, if you supplied none) to the translated text; every source segment must be covered exactly once. At most 20000 entries, totalling at most 4 MiB of text. |

#### `elevenlabs_dubbing_language_delete`

Delete Dubbing Language Target. _(POST /api/elevenlabs/dubbing/language/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the parent dubbing project. |
| `language_id` | string | Sim | Identifier of the language target to delete. |

#### `elevenlabs_dubbing_language_get`

Get Dubbing Language Target. Full language-target detail. _(POST /api/elevenlabs/dubbing/language/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the parent dubbing project. |
| `language_id` | string | Sim | Identifier of the language target to fetch. |

#### `elevenlabs_dubbing_language_list`

List Dubbing Language Targets. _(POST /api/elevenlabs/dubbing/language/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the parent dubbing project. |
| `cursor` | string | Não | Pagination cursor from a previous response's next_cursor. |
| `page_size` | integer | Não | Number of language targets per page (max 100). |
| `status` | string | Não | Filter to targets in this status (queued, processing, completed, stale, failed). |

#### `elevenlabs_dubbing_project_delete`

Delete Dubbing Project. Delete a project and its language targets. _(POST /api/elevenlabs/dubbing/project/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project to delete. |

#### `elevenlabs_dubbing_project_get`

Get Dubbing Project. Full project detail, including its language target ids. _(POST /api/elevenlabs/dubbing/project/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project to fetch. |

#### `elevenlabs_dubbing_project_list`

List Dubbing Projects. List the workspace's dubbing projects (cursor-paginated). _(POST /api/elevenlabs/dubbing/project/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cursor` | string | Não | Pagination cursor from a previous response's next_cursor. |
| `page_size` | integer | Não | Number of projects per page (max 100). |
| `status` | string | Não | Filter to projects in this status (preparing, ready, failed). |
| `sort_direction` | string | Não | Sort by creation time (default 'DESCENDING'). (ASCENDING, DESCENDING) |

#### `elevenlabs_dubbing_target_transcript_get`

Get Dubbing Target Transcript. _(POST /api/elevenlabs/dubbing/target/transcript/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `language_id` | string | Sim | Identifier of the language target. |

#### `elevenlabs_dubbing_target_transcript_regenerate`

Regenerate Dubbing Target. Enterprise only. Re-dub a target from its edited transcript, re-synthesizing only the edited regions (charged like a generation). Conflicts when the target has no edits to a _(POST /api/elevenlabs/dubbing/target/transcript/regenerate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `language_id` | string | Sim | Identifier of the language target. |

#### `elevenlabs_dubbing_target_transcript_segmen_b565e6`

Update Dubbing Target Transcript Segment. _(POST /api/elevenlabs/dubbing/target/transcript/segmen/b565e6)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `language_id` | string | Sim | Identifier of the language target. |
| `segment_id` | string | Sim | Identifier of the segment to edit. |
| `translation` | string | Não | New translated text, or null to mark the segment for re-translation. |

#### `elevenlabs_dubbing_target_transcript_segmen_fa79db`

Update Dubbing Target Transcript Segments. _(POST /api/elevenlabs/dubbing/target/transcript/segmen/fa79db)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `language_id` | string | Sim | Identifier of the language target. |
| `segments` | object | Sim | Map of segment id to the translation edit to apply to that segment. |

#### `elevenlabs_dubbing_transcript_get`

Get Dubbing Transcript. The project's source transcript, as editable segments. _(POST /api/elevenlabs/dubbing/transcript/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |

#### `elevenlabs_dubbing_transcript_segment_add`

Add Dubbing Transcript Segment. _(POST /api/elevenlabs/dubbing/transcript/segment/add)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `text` | string | Sim | The text of the new segment. |
| `speaker_id` | string | Sim | Identifier of the segment's speaker. |
| `start_s` | number | Sim | Start time of the segment, in seconds. |
| `end_s` | number | Sim | End time of the segment, in seconds. |

#### `elevenlabs_dubbing_transcript_segment_delete`

Delete Dubbing Transcript Segment. _(POST /api/elevenlabs/dubbing/transcript/segment/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `segment_id` | string | Sim | Identifier of the segment to remove. |

#### `elevenlabs_dubbing_transcript_segment_update`

Update Dubbing Transcript Segment. _(POST /api/elevenlabs/dubbing/transcript/segment/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `segment_id` | string | Sim | Identifier of the segment to edit. |
| `text` | string | Não | New text for the segment. |
| `speaker_id` | string | Não | New speaker id for the segment. |
| `start_s` | number | Não | New start time, in seconds. |
| `end_s` | number | Não | New end time, in seconds. |

#### `elevenlabs_dubbing_transcript_segments_update`

Update Dubbing Transcript Segments. _(POST /api/elevenlabs/dubbing/transcript/segments/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | Identifier of the dubbing project. |
| `segments` | object | Sim | Map of segment id to the partial update to apply to that segment. |

#### `elevenlabs_edit_chapter`

Update Chapter. Updates a chapter. _(POST /api/elevenlabs/edit/chapter)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |
| `name` | string | Não | The name of the chapter, used for identification only. |
| `content` | object | Não | The chapter content to use. |

#### `elevenlabs_edit_project`

Update Studio Project. Updates the specified Studio project by setting the values of the parameters passed. _(POST /api/elevenlabs/edit/project)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `name` | string | Sim | The name of the Studio project, used for identification only. |
| `default_title_voice_id` | string | Sim | The voice_id that corresponds to the default voice used for new titles. |
| `default_paragraph_voice_id` | string | Sim | The voice_id that corresponds to the default voice used for new paragraphs. |
| `title` | string | Não | An optional name of the author of the Studio project, this will be added as metadata to the mp3 file on Studio project or chapter download. |
| `author` | string | Não | An optional name of the author of the Studio project, this will be added as metadata to the mp3 file on Studio project or chapter download. |
| `isbn_number` | string | Não | An optional ISBN number of the Studio project you want to create, this will be added as metadata to the mp3 file on Studio project or chapter download. |
| `volume_normalization` | boolean | Não | When the Studio project is downloaded, should the returned audio have postprocessing in order to make it compliant with audiobook normalized volume requirements |

#### `elevenlabs_edit_pvc_voice`

Edit Pvc Voice. Edit PVC voice metadata _(POST /api/elevenlabs/edit/pvc/voice)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `name` | string | Não | The name that identifies this voice. This will be displayed in the dropdown of the website. |
| `language` | string | Não | Language used in the samples. |
| `description` | string | Não | Description to use for the created voice. |
| `labels` | object | Não | Labels for the voice. Keys can be language, accent, gender, or age. |

#### `elevenlabs_edit_pvc_voice_sample`

Update Pvc Voice Sample. Update a PVC voice sample - apply noise removal, select speaker, change trim times or file name. _(POST /api/elevenlabs/edit/pvc/voice/sample)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |
| `remove_background_noise` | boolean | Não | If set will remove background noise for voice samples using our audio isolation model. If the samples do not include background noise, it can make the quality worse. |
| `selected_speaker_ids` | string[] | Não | Speaker IDs to be used for PVC training. Make sure you send all the speaker IDs you want to use for PVC training in one request because the last request will override the previous ones. |
| `trim_start_time` | integer | Não | The start time of the audio to be used for PVC training. Time should be in milliseconds |
| `trim_end_time` | integer | Não | The end time of the audio to be used for PVC training. Time should be in milliseconds |
| `file_name` | string | Não | The name of the audio file to be used for PVC training. |

#### `elevenlabs_edit_service_account_api_key`

Edit Service Account Api Key. Update an existing API key for a service account _(POST /api/elevenlabs/edit/service/account/api/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `service_account_user_id` | string | Sim | Service Account User Id |
| `api_key_id` | string | Sim | Api Key Id |
| `is_enabled` | boolean|string | Não | Whether to enable or disable the API key. |
| `name` | string | Não | The name of the XI API key to use (used for identification purposes only). |
| `permissions` | string[]|string | Não | The permissions of the XI API. |
| `character_limit` | integer|string | Não | The character limit of the XI API key. If provided this will limit the usage of this api key to n characters per month where n is the chosen value. Requests that incur charges will fail after reaching this monthly limit. |
| `allowed_ips` | string[]|string | Não | List of IP addresses or CIDR ranges allowed to use this API key. Each entry may be a CIDR range (e.g. '10.0.0.0/24') or a bare IP address (normalized to /32 or /128). On create, omit or pass null to allow all IPs. On update, omit to leave the allowlist unchanged, or pass "clear" to remove it. |
| `third_party_disable_allowed` | boolean|string | Não | Whether the holder of this key may disable it via the self-disable endpoint. On create, omit or pass null to use the workspace's default (enabled for non-Enterprise plans, disabled for Enterprise plans). On update, omit to leave it unchanged, or pass "clear" to reset it to the workspace default. Only honored for workspaces with self-disable access enabled. |

#### `elevenlabs_edit_voice_settings`

Edit Voice Settings. Edit your settings for a specific voice. "similarity_boost" corresponds to "Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in t _(POST /api/elevenlabs/edit/voice/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `stability` | number | Não | Determines how stable the voice is and the randomness between each generation. Lower values introduce broader emotional range for the voice. Higher values can result in a monotonous voice with limited emotion. |
| `use_speaker_boost` | boolean | Não | This setting boosts the similarity to the original speaker. Using this setting requires a slightly higher computational load, which in turn increases latency. |
| `similarity_boost` | number | Não | Determines how closely the AI should adhere to the original voice when attempting to replicate it. |
| `style` | number | Não | Determines the style exaggeration of the voice. This setting attempts to amplify the style of the original speaker. It does consume additional computational resources and might increase latency if set to anything other than 0. |
| `speed` | number | Não | Adjusts the speed of the voice. A value of 1.0 is the default speed, while values less than 1.0 slow down the speech, and values greater than 1.0 speed it up. |

#### `elevenlabs_edit_workspace_webhook_route`

Update Workspace Webhook. Update the specified workspace webhook _(POST /api/elevenlabs/edit/workspace/webhook/route)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `webhook_id` | string | Sim | The unique ID for the webhook |
| `is_disabled` | boolean | Sim | Whether to disable or enable the webhook |
| `name` | string | Sim | The display name of the webhook (used for display purposes only). |
| `retry_enabled` | boolean | Não | Whether to enable automatic retries for transient failures (5xx, 429, timeout) |
| `request_headers` | object | Não | A list of request headers to include with the webhook delivery (optional) |
| `events` | string[] | Não | The complete set of workspace-level events this webhook should be subscribed to. The webhook is added to the events in the list and removed from any not in the list. Omit to leave the current event subscriptions unchanged. (voice_library_removal_notice, speech_to_text, agent_qa) |

#### `elevenlabs_generate`

Compose Music. Compose a song from a prompt or a composition plan. _(POST /api/elevenlabs/generate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. Use "auto" (the default) to let the API pick the best format for the selected model: mp3_44100_128 for v1 models and mp3_48000_192 for v2 models.  (auto, mp3_48000_128, mp3_48000_192, mp3_48000_240, mp3_48000_320, mp3_22050_32, mp3_24000_48, mp3_44100_32, mp3_44100_64, mp3_44100_96, mp3_44100_128, mp3_44100_192, pcm_8000, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, ulaw_8000, alaw_8000, opus_48000_32, opus_48000_64, opus_48000_96, opus_48000_128, opus_48000_192) |
| `prompt` | string | Não | A simple text prompt to generate a song from. Cannot be used in conjunction with `composition_plan`. |
| `generation_mode` | string | Não | Optional generation mode hint for prompt-based music generation. Can only be used with `prompt`. (track, loop, ambience, video_to_music) |
| `music_prompt` | object | Não | A music prompt. Deprecated. Use `composition_plan` instead. |
| `lyrics_text` | string | Não | The lyrics text to use for the generation. |
| `composition_plan` | object | Não | A detailed composition plan to guide music generation. Cannot be used in conjunction with `prompt`. |
| `music_length_ms` | integer | Não | The length of the song to generate in milliseconds. Used only in conjunction with `prompt`. Must be between 3000ms and 600000ms. Optional - if not provided, the model will choose a length based on the prompt. |
| `model_id` | string | Não | The model to use for the generation. (music_v1, music_v2) |
| `seed` | integer | Não | Random seed to initialize the music generation process. Providing the same seed with the same parameters can help achieve more consistent results, but exact reproducibility is not guaranteed and outputs may change across system updates. Cannot be used in conjunction with prompt. |
| `force_instrumental` | boolean | Não | If true, guarantees that the generated song will be instrumental. If false, the song may or may not be instrumental depending on the `prompt`. Can only be used with `prompt`. |
| `finetune_id` | string | Não | The ID of the finetune to use for the generation |
| `finetune_strength` | number | Não | How strongly the finetune influences the generation. Defaults to 1.0 (full strength). Lower values soften the influence of the finetune, leaving more room for prompt-level steering. Only meaningful when `finetune_id` is also provided. |
| `use_phonetic_names` | boolean | Não | If true, proper names in the prompt will be phonetically spelled in the lyrics for better pronunciation by the music model. The original names will be restored in word timestamps. |
| `respect_sections_durations` | boolean | Não | Controls how strictly section durations in the `composition_plan` are enforced. Only used with `composition_plan` and only applies to `music_v1`; for `music_v2` section durations are always enforced and this is ignored. When false for `music_v1`, the model may adjust individual section durations for better quality and latency, while preserving the total song duration from the plan. |
| `store_for_inpainting` | boolean | Não | Whether to store the generated song for inpainting. |
| `sign_with_c2pa` | boolean | Não | Whether to sign the generated song with C2PA. Applicable only for mp3 files. |

#### `elevenlabs_get_audio_from_sample`

Get Audio From Sample. Returns the audio corresponding to a sample attached to a voice. _(POST /api/elevenlabs/get/audio/from/sample)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used, you can use GET https://api.elevenlabs.io/v1/voices/{voice_id} to list all the available samples for a voice. |

#### `elevenlabs_get_audio_full_from_speech_history_item`

Get Audio From History Item. Returns the audio of an history item. _(POST /api/elevenlabs/get/audio/full/from/speech/history/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `history_item_id` | string | Sim | History item ID to be used, you can use GET https://api.elevenlabs.io/v1/history to receive a list of history items and their IDs. |

#### `elevenlabs_get_audio_isolation_history`

Get Audio Isolation History. Returns a list of all your audio isolation generations. _(POST /api/elevenlabs/get/audio/isolation/history)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page_size` | integer | Não | How many history items to return at maximum. Defaults to 100. |
| `page` | integer | Não | Page number for search pagination (1-based). Only used when search is provided. |
| `search` | string | Não | Optional search term used for filtering audio isolation history (title/text). |

#### `elevenlabs_get_audio_native_project_setting_340fd1`

Get Audio Native Project Settings. _(POST /api/elevenlabs/get/audio/native/project/setting/340fd1)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_get_chapter_by_id_endpoint`

Get Chapter. Returns information about a specific chapter. _(POST /api/elevenlabs/get/chapter/by/id/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |

#### `elevenlabs_get_chapter_snapshot_endpoint`

Get Chapter Snapshot. Returns the chapter snapshot. _(POST /api/elevenlabs/get/chapter/snapshot/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |
| `chapter_snapshot_id` | string | Sim | The ID of the chapter snapshot. |

#### `elevenlabs_get_chapter_snapshots`

List Chapter Snapshots. Gets information about all the snapshots of a chapter. Each snapshot can be downloaded as audio. Whenever a chapter is converted a snapshot will automatically be created. _(POST /api/elevenlabs/get/chapter/snapshots)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |

#### `elevenlabs_get_chapters`

List Chapters. Returns a list of a Studio project's chapters. _(POST /api/elevenlabs/get/chapters)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_get_dubbed_file`

Get Dubbed File. Returns dub as a streamed MP3 or MP4 file. If this dub has been edited using Dubbing Studio you need to use the resource render endpoint as this endpoint only returns the original aut _(POST /api/elevenlabs/get/dubbed/file)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `dubbing_id` | string | Sim | ID of the dubbing project. |
| `language_code` | string | Sim | ID of the language. |

#### `elevenlabs_get_dubbed_metadata`

Get Dubbing. Returns metadata about a dubbing project, including whether it's still in progress or not _(POST /api/elevenlabs/get/dubbed/metadata)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `dubbing_id` | string | Sim | ID of the dubbing project. |

#### `elevenlabs_get_dubbing_transcripts`

Retrieve A Transcript. Fetch the transcript for one of the languages in a dub. _(POST /api/elevenlabs/get/dubbing/transcripts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `dubbing_id` | string | Sim | ID of the dubbing project. |
| `language_code` | string | Sim | ISO-693 language code to retrieve the transcript for. Use 'source' to fetch the transcript of the original media. |
| `format_type` | string | Sim | Format to return transcript in. For subtitles use either 'srt' or 'webvtt', and for a full transcript use 'json'. The 'json' format is not yet supported for Dubbing Studio. (srt, webvtt, json) |

#### `elevenlabs_get_finetune`

Get Music Finetune. Get a music finetune. _(POST /api/elevenlabs/get/finetune)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `finetune_id` | string | Sim | Finetune Id |

#### `elevenlabs_get_finetunes`

Get Music Finetunes. List music finetunes accessible to you (your own, workspace-shared, and ElevenLabs-curated), with optional filtering, sorting, and cursor pagination. _(POST /api/elevenlabs/get/finetunes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cursor` | string | Não | Used for fetching the next page. Cursor is returned in the response. |
| `page_size` | integer | Não | How many finetunes to return. Max 100, default 50. |
| `visibility` | string | Não | Filter by visibility. 'private' returns private finetunes; 'workspace' returns workspace-shared finetunes; 'public' returns public finetunes, which are currently ElevenLabs curated finetunes. Omit to return all accessible finetunes. (private, workspace, public) |
| `created_by` | string | Não | Filter by creator. 'self' returns finetunes you created; 'workspace' returns finetunes created by workspace teammates; 'elevenlabs' returns ElevenLabs curated finetunes. Omit to return finetunes from all creators. (self, workspace, elevenlabs) |
| `sort` | string | Não | Sort by field (created_at or name) (created_at, name) |
| `sort_direction` | string | Não | Sort direction (asc or desc) (asc, desc) |

#### `elevenlabs_get_groups_endpoint`

Get All Groups. Get all groups in the workspace _(POST /api/elevenlabs/get/groups/endpoint)_

#### `elevenlabs_get_library_voices`

Get Voices. Retrieves a list of shared voices. _(POST /api/elevenlabs/get/library/voices)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page_size` | integer | Não | How many shared voices to return at maximum. Can not exceed 100, defaults to 30. |
| `category` | string | Não | Voice category used for filtering (professional, famous, high_quality) |
| `gender` | string | Não | Gender used for filtering |
| `age` | string | Não | Age used for filtering |
| `accent` | string | Não | Accent used for filtering |
| `language` | string | Não | Language used for filtering |
| `locale` | string | Não | Locale used for filtering |
| `search` | string | Não | Search term used for filtering |
| `use_cases` | string[] | Não | Use-case used for filtering |
| `descriptives` | string[] | Não | Search term used for filtering |
| `featured` | boolean | Não | Filter featured voices |
| `min_notice_period_days` | integer | Não | Filter voices with a minimum notice period of the given number of days. |
| `include_custom_rates` | boolean | Não | Include/exclude voices with custom rates |
| `include_live_moderated` | boolean | Não | Include/exclude voices that are live moderated |
| `reader_app_enabled` | boolean | Não | Filter voices that are enabled for the reader app |
| `owner_id` | string | Não | Filter voices by public owner ID |
| `sort` | string | Não | Sort criteria. Must be one of: created_date, usage_character_count_1y, trending, cloned_by_count. (created_date, usage_character_count_1y, trending, cloned_by_count) |
| `page` | integer | Não | Page |

#### `elevenlabs_get_models`

Get Models. Gets a list of available models. _(POST /api/elevenlabs/get/models)_

#### `elevenlabs_get_project_by_id`

Get Studio Project. Returns information about a specific Studio project. This endpoint returns more detailed information about a project than `GET /v1/studio`. _(POST /api/elevenlabs/get/project/by/id)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `share_id` | string | Não | The share ID of the project |

#### `elevenlabs_get_project_muted_tracks_endpoint`

Get Project Muted Tracks. Returns a list of chapter IDs that have muted tracks in a project. _(POST /api/elevenlabs/get/project/muted/tracks/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_get_project_snapshot_endpoint`

Get Project Snapshot. Returns the project snapshot. _(POST /api/elevenlabs/get/project/snapshot/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `project_snapshot_id` | string | Sim | The ID of the Studio project snapshot. |

#### `elevenlabs_get_project_snapshots`

List Studio Project Snapshots. _(POST /api/elevenlabs/get/project/snapshots)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |

#### `elevenlabs_get_projects`

List Studio Projects. Returns a list of your Studio projects with metadata. _(POST /api/elevenlabs/get/projects)_

#### `elevenlabs_get_pronunciation_dictionaries_metadata`

Get Pronunciation Dictionaries. _(POST /api/elevenlabs/get/pronunciation/dictionaries/metadata)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cursor` | string | Não | Used for fetching next page. Cursor is returned in the response. |
| `page_size` | integer | Não | How many pronunciation dictionaries to return at maximum. Can not exceed 100, defaults to 30. |
| `sort` | string | Não | Which field to sort by, one of 'created_at_unix' or 'name'. (creation_time_unix, name) |
| `sort_direction` | string | Não | Which direction to sort the voices in. 'ascending' or 'descending'. |
| `include_archived` | boolean | Não | Whether to include archived pronunciation dictionaries in the response. |

#### `elevenlabs_get_pronunciation_dictionary_metadata`

Get Metadata For A Pronunciation Dictionary. _(POST /api/elevenlabs/get/pronunciation/dictionary/metadata)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pronunciation_dictionary_id` | string | Sim | The id of the pronunciation dictionary |

#### `elevenlabs_get_pronunciation_dictionary_ver_45baf2`

Get A Pls File With A Pronunciation Dictionary Version Rules. _(POST /api/elevenlabs/get/pronunciation/dictionary/ver/45baf2)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `dictionary_id` | string | Sim | The id of the pronunciation dictionary |
| `version_id` | string | Sim | The id of the pronunciation dictionary version |

#### `elevenlabs_get_pvc_sample_audio`

Retrieve Voice Sample Audio. Retrieve the first 30 seconds of voice sample audio with or without noise removal. _(POST /api/elevenlabs/get/pvc/sample/audio)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |
| `remove_background_noise` | boolean | Não | If set will remove background noise for voice samples using our audio isolation model. If the samples do not include background noise, it can make the quality worse. |

#### `elevenlabs_get_pvc_sample_speakers`

Retrieve Speaker Separation Status. _(POST /api/elevenlabs/get/pvc/sample/speakers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |

#### `elevenlabs_get_pvc_sample_visual_waveform`

Retrieve Voice Sample Visual Waveform. _(POST /api/elevenlabs/get/pvc/sample/visual/waveform)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |

#### `elevenlabs_get_pvc_voice_captcha`

Get Pvc Voice Captcha. Get captcha for PVC voice verification. _(POST /api/elevenlabs/get/pvc/voice/captcha)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |

#### `elevenlabs_get_resource_metadata`

Get Resource. Gets the metadata of a resource by ID. _(POST /api/elevenlabs/get/resource/metadata)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `resource_id` | string | Sim | The ID of the target resource. |
| `resource_type` | string | Sim | Resource types that can be shared in the workspace. The name always need to match the collection names (voice, voice_collection, pronunciation_dictionary, dubbing, project, convai_agents, convai_knowledge_base_documents, convai_tools, convai_settings, convai_secrets, workspace_auth_connections, convai_phone_numbers, convai_mcp_servers, convai_api_integration_connections, convai_api_integration_trigger_connections, convai_batch_calls, convai_agent_response_tests, convai_test_suite_invocations, convai_crawl_jobs, convai_crawl_tasks, convai_kb_external_sync_jobs, convai_whatsapp_accounts, convai_agent_versions, convai_agent_branches, convai_agent_versions_deployments, convai_memory_entries, convai_coaching_proposals, convai_templates, dashboard, dashboard_configuration, convai_agent_drafts, resource_locators, assets, content_generations, content_templates, songs, transcription_tasks, avatars, avatar_video_generations, resource_collection, studio_projects, convai_analysis_items) |

#### `elevenlabs_get_service_account_api_keys_route`

Get Service Account Api Keys Route. _(POST /api/elevenlabs/get/service/account/api/keys/route)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `service_account_user_id` | string | Sim | Service Account User Id |

#### `elevenlabs_get_single_use_token`

Create Single Use Token. Generate a time limited single-use token with embedded authentication for frontend clients. _(POST /api/elevenlabs/get/single/use/token)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `token_type` | string | Sim | SingleUseTokenType (realtime_scribe, batch_scribe, tts_websocket) |

#### `elevenlabs_get_speaker_audio`

Retrieve Separated Speaker Audio. _(POST /api/elevenlabs/get/speaker/audio)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |
| `speaker_id` | string | Sim | Speaker ID to be used, you can use GET https://api.elevenlabs.io/v1/voices/{voice_id}/samples/{sample_id}/speakers to list all the available speakers for a sample. |

#### `elevenlabs_get_speech_engine`

Get Speech Engine. Retrieve a Speech Engine resource _(POST /api/elevenlabs/get/speech/engine)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `speech_engine_id` | string | Sim | The speech engine ID (accepts seng_ or agent_ prefix) |

#### `elevenlabs_get_speech_history`

List Generated Items. Returns a list of your generated audio (e.g. text to speech, speech to speech, Studio, dubbing). Music and SFX generations are not included and cannot currently be retrieved via _(POST /api/elevenlabs/get/speech/history)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page_size` | integer | Não | How many history items to return at maximum. Can not exceed 1000, defaults to 100. |
| `start_after_history_item_id` | string | Não | After which ID to start fetching, use this parameter to paginate across a large collection of history items. In case this parameter is not provided history items will be fetched starting from the most recently created one ordered descending by their creation date. |
| `voice_id` | string | Não | Voice ID to be filtered for, you can use GET https://api.elevenlabs.io/v1/voices to receive a list of voices and their IDs. |
| `model_id` | string | Não | Model ID to filter history items by. |
| `date_before_unix` | integer | Não | Unix timestamp to filter history items before this date (exclusive). |
| `date_after_unix` | integer | Não | Unix timestamp to filter history items after this date (inclusive). |
| `sort_direction` | string | Não | Sort direction for the results. (asc, desc) |
| `search` | string | Não | search term used for filtering |
| `source` | string | Não | Source of the generated history item (TTS, STS, Flows) |

#### `elevenlabs_get_speech_history_item_by_id`

Get History Item. Retrieves a history item. _(POST /api/elevenlabs/get/speech/history/item/by/id)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `history_item_id` | string | Sim | History item ID to be used, you can use GET https://api.elevenlabs.io/v1/history to receive a list of history items and their IDs. |

#### `elevenlabs_get_transcript_by_id`

Get Transcript By Id. Retrieve a previously generated transcript by its ID. _(POST /api/elevenlabs/get/transcript/by/id)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transcription_id` | string | Sim | The unique ID of the transcript to retrieve |

#### `elevenlabs_get_user_info`

Get User Info. Gets information about the user _(POST /api/elevenlabs/get/user/info)_

#### `elevenlabs_get_user_subscription_info`

Get User Subscription Info. Gets extended information about the users subscription _(POST /api/elevenlabs/get/user/subscription/info)_

#### `elevenlabs_get_user_voices_v2`

Get Voices V2. Gets a list of all available voices for a user with search, filtering and pagination. _(POST /api/elevenlabs/get/user/voices/v2)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `next_page_token` | string | Não | The next page token to use for pagination. Returned from the previous request. Use this in combination with the has_more flag for reliable pagination. |
| `page_size` | integer | Não | How many voices to return at maximum. Can not exceed 100, defaults to 10. Page 0 may include more voices due to default voices being included. |
| `search` | string | Não | Search term to filter voices by. Searches in name, description, labels, category. |
| `sort` | string | Não | Which field to sort by, one of 'created_at_unix' or 'name'. 'created_at_unix' may not be available for older voices. |
| `sort_direction` | string | Não | Which direction to sort the voices in. 'asc' or 'desc'. |
| `voice_type` | string | Não | Type of the voice to filter by. One of 'personal', 'community', 'default', 'workspace', 'non-default', 'non-community', 'saved'. 'non-default' is equal to all but 'default'. 'non-community' is equal to 'personal' and 'workspace' combined (excludes library copies). 'saved' is equal to non-default, but includes default voices if they have been added to a collection. |
| `category` | string | Não | Category of the voice to filter by. One of 'premade', 'cloned', 'generated', 'professional' |
| `fine_tuning_state` | string | Não | State of the voice's fine tuning to filter by. Applicable only to professional voices clones. One of 'draft', 'not_verified', 'not_started', 'queued', 'fine_tuning', 'fine_tuned', 'failed', 'delayed' |
| `collection_id` | string | Não | Collection ID to filter voices by. |
| `gender` | string | Não | Gender used for filtering, based on the voice's 'gender' label. |
| `age` | string | Não | Age used for filtering, based on the voice's 'age' label. |
| `language` | string[] | Não | Languages used for filtering, based on the voice's 'language' label. Voices matching any of the given languages are returned. |
| `accent` | string | Não | Accent used for filtering, based on the voice's 'accent' label. |
| `use_cases` | string[] | Não | Use cases used for filtering, based on the voice's 'use_case' label. Voices matching any of the given use cases are returned. |
| `min_notice_period_days` | integer | Não | Filter to voices whose sharing notice period is at least the given number of days. |
| `include_custom_rates` | boolean | Não | Whether to include voices that have a custom sharing rate. Defaults to including them. |
| `include_live_moderated` | boolean | Não | Whether to include voices that have live moderation enabled. Defaults to including them. |
| `high_quality` | boolean | Não | When true, only return studio-quality voices (those whose category is 'high_quality'). |
| `include_total_count` | boolean | Não | Whether to include the total count of voices found in the response. NOTE: The total_count value is a live snapshot and may change between requests as users create, modify, or delete voices. For pagination, rely on the has_more flag instead. Only enable this when you actually need the total count (e.g., for display purposes), as it incurs a performance cost. |
| `voice_ids` | string[] | Não | Voice IDs to lookup by. Maximum 100 voice IDs. |

#### `elevenlabs_get_voice_accents`

Get Voice Accents. Gets the list of available accents in the shared voice library. _(POST /api/elevenlabs/get/voice/accents)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `language` | string | Não | If provided, only accents for this language code are returned. |
| `model_id` | string | Não | If provided, returns the accents available for this model. Defaults to the most complete accent list when omitted. |

#### `elevenlabs_get_voice_by_id`

Get Voice. Returns metadata about a specific voice. _(POST /api/elevenlabs/get/voice/by/id)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `with_settings` | boolean | Não | This parameter is now deprecated. It is ignored and will be removed in a future version. |

#### `elevenlabs_get_voice_settings`

Get Voice Settings. Returns the settings for a specific voice. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider in t _(POST /api/elevenlabs/get/voice/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |

#### `elevenlabs_get_voice_settings_default`

Get Default Voice Settings.. Gets the default settings for voices. "similarity_boost" corresponds to"Clarity + Similarity Enhancement" in the web app and "stability" corresponds to "Stability" slider _(POST /api/elevenlabs/get/voice/settings/default)_

#### `elevenlabs_get_voices`

List Voices. Returns a list of all available voices for a user. Stops working once the user's workspace exceeds 500 voices. _(POST /api/elevenlabs/get/voices)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `show_legacy` | boolean | Não | If set to true, legacy premade voices will be included in responses from /v1/voices |

#### `elevenlabs_get_workspace_audit_logs`

Get Workspace Audit Logs. Returns the audit log for the workspace. Requires enterprise tier and the audit_log_read permission. _(POST /api/elevenlabs/get/workspace/audit/logs)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `limit` | integer | Não | Maximum number of entries per page |
| `cursor` | string | Não | Cursor for the next page (from previous response) |
| `time_from_unix_ms` | integer | Não | Only include entries at or after this time (ms since epoch) |
| `time_to_unix_ms` | integer | Não | Only include entries at or before this time (ms since epoch) |
| `actor_uid` | string | Não | Filter by actor user ID |
| `class_name` | string | Não | Filter by OCSF event class name (e.g. Account Change) |
| `activity_name` | string | Não | Filter by audit activity name (e.g. Subscription Creation) |

#### `elevenlabs_get_workspace_members`

Get Workspace Members. Gets a list of all members of the workspace, including locked members. Service accounts are excluded. Requires the workspace_members_read permission. _(POST /api/elevenlabs/get/workspace/members)_

#### `elevenlabs_get_workspace_service_accounts`

Get Workspace Service Accounts. _(POST /api/elevenlabs/get/workspace/service/accounts)_

#### `elevenlabs_get_workspace_webhooks_route`

List Workspace Webhooks. List all webhooks for a workspace _(POST /api/elevenlabs/get/workspace/webhooks/route)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `include_usages` | boolean | Não | Whether to include active usages of the webhook, only usable by admins |

#### `elevenlabs_invite_user`

Invite User. Sends an email invitation to join your workspace to the provided email. If the user doesn't have an account they will be prompted to create one. If the user accepts this invite they will _(POST /api/elevenlabs/invite/user)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Sim | The email of the customer |
| `workspace_permission` | string | Não | The workspace permission of the user. This is deprecated, use `seat_type` instead. |
| `seat_type` | string | Não | The seat type of the user (workspace_admin, workspace_member, workspace_lite_member) |
| `group_ids` | string[] | Não | The group ids of the user |
| `usage_limit` | integer | Não | Monthly credit usage limit for the invitee. Omit or set to null for no custom cap. |

#### `elevenlabs_invite_users_bulk`

Invite Multiple Users. Sends email invitations to join your workspace to the provided emails. Requires all email addresses to be part of a verified domain. If the users don't have an account they will _(POST /api/elevenlabs/invite/users/bulk)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `emails` | string[] | Sim | The email of the customer |
| `seat_type` | string | Não | The seat type of the user (workspace_admin, workspace_member, workspace_lite_member) |
| `group_ids` | string[] | Não | The group ids of the user |
| `usage_limit` | integer | Não | Monthly credit usage limit for the invitee. Omit or set to null for no custom cap. |

#### `elevenlabs_list_auth_connections`

Get Workspace Auth Connections. _(POST /api/elevenlabs/list/auth/connections)_

#### `elevenlabs_list_dubs`

List Dubs. List the dubs you have access to. _(POST /api/elevenlabs/list/dubs)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cursor` | string | Não | Used for fetching next page. Cursor is returned in the response. |
| `page_size` | integer | Não | How many dubs to return at maximum. Can not exceed 200, defaults to 100. |
| `dubbing_status` | string | Não | What state the dub is currently in. (dubbing, dubbed, failed) |
| `dubbing_statuses` | string[] | Não | Filter by dubbing status. (queued, preparing, dubbing, dubbed, failed) |
| `dubbing_models` | string[] | Não | Filter by dubbing model generation. (dubbing_v1, dubbing_v2) |
| `target_language_codes` | string[] | Não | Filter by target language code. |
| `creation_sources` | string[] | Não | Filter by dubbing creation source. (flow_node, dubbing_ui, dubbing_api) |
| `filter_by_creator` | string | Não | Filters who created the resources being listed, whether it was the user running the request or someone else that shared the resource with them. (personal, others, all) |
| `order_by` | string | Não | The field to use for ordering results from this query. (created_at, name) |
| `order_direction` | string | Não | The order direction to use for results from this query. (DESCENDING, ASCENDING) |

#### `elevenlabs_list_speech_engines`

List Speech Engines. Returns a paginated list of Speech Engine resources. _(POST /api/elevenlabs/list/speech/engines)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page_size` | integer | Não | How many Speech Engines to return at maximum. Can not exceed 100, defaults to 30. |
| `search` | string | Não | Search term to filter Speech Engines by name |
| `sort_direction` | string | Não | The direction to sort the results (asc, desc) |
| `sort_by` | string | Não | The field to sort the results by (name, created_at, call_count_7d) |
| `cursor` | string | Não | Used for fetching next page. Cursor is returned in the response. |

#### `elevenlabs_patch_pronunciation_dictionary`

Update Pronunciation Dictionary. _(POST /api/elevenlabs/patch/pronunciation/dictionary)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pronunciation_dictionary_id` | string | Sim | The id of the pronunciation dictionary |
| `archived` | boolean | Não | Whether to archive the pronunciation dictionary. |
| `name` | string | Não | The name of the pronunciation dictionary, used for identification only. |

#### `elevenlabs_public_create_order`

Create Order. Creates a new Productions order in the workspace. The order starts in the open state and can be configured with items before submission. _(POST /api/elevenlabs/public/create/order)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `body` | object | Não | Corpo JSON da requisição. |

#### `elevenlabs_public_get_available_languages`

Get Available Languages. Returns the available languages for a given order item kind. _(POST /api/elevenlabs/public/get/available/languages)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_item_kind` | string | Sim | The kind of order item. (dub, subtitles, transcription) |

#### `elevenlabs_public_get_media_info`

Get Media Info. Retrieves metadata and a time-limited download URL for a previously uploaded media file. _(POST /api/elevenlabs/public/get/media/info)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |
| `media_id` | string | Sim | The ID of the media file. |

#### `elevenlabs_public_get_order`

Get Order. Retrieves full details for a Productions order. _(POST /api/elevenlabs/public/get/order)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |

#### `elevenlabs_public_get_order_deliverables`

Get Order Deliverables. Retrieves the delivered files for a completed order. Returns an empty list if the order is not yet completed. _(POST /api/elevenlabs/public/get/order/deliverables)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |

#### `elevenlabs_public_list_orders`

List Orders. Lists Productions orders in the workspace. Supports filtering by status and date range, with pagination. _(POST /api/elevenlabs/public/list/orders)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page_size` | integer | Não | Maximum number of orders to return per page. |
| `offset` | integer | Não | Number of orders to skip for pagination. |
| `status` | string[] | Não | Filter orders by one or more statuses. (open, submitted, paid, accepted, rejected, done, cancelling, cancelled, expired) |
| `start_date` | string | Não | Filter orders created on or after this date. |
| `end_date` | string | Não | Filter orders created on or before this date. |

#### `elevenlabs_public_remove_order_item`

Remove Order Item. Removes an order item from an open order. _(POST /api/elevenlabs/public/remove/order/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |
| `item_id` | string | Sim | The ID of the order item. |

#### `elevenlabs_public_submit_order`

Submit Order. Submits an open order for processing. The order must have at least one item. Once submitted, items can no longer be modified. _(POST /api/elevenlabs/public/submit/order)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |

#### `elevenlabs_public_update_order`

Update Order. Updates an open order. _(POST /api/elevenlabs/public/update/order)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |
| `request` | object | Sim | UpdateOrderRequest |

#### `elevenlabs_public_upsert_order_item`

Upsert Order Item. Adds or updates an order item on an open order. Returns the item ID and the quoted price. _(POST /api/elevenlabs/public/upsert/order/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Sim | The ID of the order. |
| `request` | object | Sim | UpsertOrderItemRequest |

#### `elevenlabs_redirect_to_mintlify`

Redirect To Mintlify _(POST /api/elevenlabs/redirect/to/mintlify)_

#### `elevenlabs_remove_member`

Delete Member From User Group. _(POST /api/elevenlabs/remove/member)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `group_id` | string | Sim | The ID of the target group. |
| `email` | string | Sim | The email of the target workspace member. |

#### `elevenlabs_remove_rules`

Remove Rules From The Pronunciation Dictionary. _(POST /api/elevenlabs/remove/rules)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pronunciation_dictionary_id` | string | Sim | The id of the pronunciation dictionary |
| `rule_strings` | string[] | Sim | List of strings to remove from the pronunciation dictionary. |

#### `elevenlabs_replicate_voice_to_isolated_environment`

Replicate Voice To Isolated Environment. _(POST /api/elevenlabs/replicate/voice/to/isolated/environment)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `target_workspace_id` | string | Sim | ID of the workspace to replicate the voice into. It must belong to the same consolidated billing group as the calling workspace; the target's data residency is derived from that link. |
| `preserve_voice_id` | boolean | Não | When true (default) the replicated voice keeps the same voice ID in the target residency; set to false to assign a new voice ID. |

#### `elevenlabs_requests_list`

List Api Requests. Returns a list of API requests. Supports filtering by time range, column filters, and search terms. At least one of start_time or end_time must be provided. An optional sort paramet _(POST /api/elevenlabs/requests/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_time` | integer | Não | Start of the time range as a Unix timestamp in milliseconds. |
| `end_time` | integer | Não | End of the time range as a Unix timestamp in milliseconds. |
| `limit` | integer | Não | Limit |
| `sort` | string | Não | Optional timestamp sort direction. If omitted, defaults to desc when end_time is provided, otherwise asc. (asc, desc) |
| `filters` | object[] | Não | Filters |
| `search` | string | Não | Search |

#### `elevenlabs_run_pvc_voice_training`

Run Pvc Training. Start PVC training process for a voice. _(POST /api/elevenlabs/run/pvc/voice/training)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `model_id` | string | Não | The model ID to use for the conversion. |

#### `elevenlabs_search_groups`

Search User Groups. Searches for user groups in the workspace. Multiple or no groups may be returned. _(POST /api/elevenlabs/search/groups)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `name` | string | Sim | Name of the target group. |

#### `elevenlabs_set_rules`

Set Rules On The Pronunciation Dictionary. _(POST /api/elevenlabs/set/rules)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `pronunciation_dictionary_id` | string | Sim | The id of the pronunciation dictionary |
| `rules` | object[] | Sim | List of pronunciation rules. Rule can be either:     an alias rule: {'string_to_replace': 'a', 'type': 'alias', 'alias': 'b', }     or a phoneme rule: {'string_to_replace': 'a', 'type': 'phoneme', 'phoneme': 'b', 'alphabet': 'ipa' } |

#### `elevenlabs_set_third_party_disabling_policy`

Set Workspace Third-Party Disabling Policy. _(POST /api/elevenlabs/set/third/party/disabling/policy)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `third_party_disable_allowed` | boolean | Não | `true` forces every key in the workspace to be disable-able by its holder; `false` forbids it for every key; `null` clears the override (per-key values and the plan default apply). |

#### `elevenlabs_share_resource_endpoint`

Share Workspace Resource. Grants a role (one of 'admin', 'editor', 'commenter', or 'viewer') on a workspace resource to a user, group, or workspace (service account) API key. This overrides any existi _(POST /api/elevenlabs/share/resource/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `resource_id` | string | Sim | The ID of the target resource. |
| `role` | string | Sim | Role to grant to the target: one of 'admin', 'editor', 'commenter', or 'viewer'. (admin, editor, commenter, viewer) |
| `resource_type` | string | Sim | Resource types that can be shared in the workspace. The name always need to match the collection names (voice, voice_collection, pronunciation_dictionary, dubbing, project, convai_agents, convai_knowledge_base_documents, convai_tools, convai_settings, convai_secrets, workspace_auth_connections, convai_phone_numbers, convai_mcp_servers, convai_api_integration_connections, convai_api_integration_trigger_connections, convai_batch_calls, convai_agent_response_tests, convai_test_suite_invocations, convai_crawl_jobs, convai_crawl_tasks, convai_kb_external_sync_jobs, convai_whatsapp_accounts, convai_agent_versions, convai_agent_branches, convai_agent_versions_deployments, convai_memory_entries, convai_coaching_proposals, convai_templates, dashboard, dashboard_configuration, convai_agent_drafts, resource_locators, assets, content_generations, content_templates, songs, transcription_tasks, avatars, avatar_video_generations, resource_collection, studio_projects, convai_analysis_items) |
| `user_email` | string | Não | The email of the user or service account. |
| `group_id` | string | Não | The ID of the target group. Use 'default' to set the resource's baseline role — every workspace member receives this role unless they hold a higher one through a direct user grant, group membership, or workspace (service account) API key. |
| `workspace_api_key_id` | string | Não | The ID of the target workspace (service account) API key. This is not the API key string itself that you pass in the header for authentication — it is the key's ID, which workspace admins can find under Developers → Service Accounts. |

#### `elevenlabs_sound_generation`

Sound Generation. Turn text into sound effects for your videos, voice-overs or video games using the most advanced sound effects models in the world. _(POST /api/elevenlabs/sound/generation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. So an mp3 with 22.05kHz sample rate at 32kbs is represented as mp3_22050_32. MP3 with 192kbps bitrate requires you to be subscribed to Creator tier or above. PCM with 44.1kHz sample rate requires you to be subscribed to Pro tier or above. Note that the μ-law format (sometimes written mu-law, often approximated as u-law) is commonly used for Twilio audio inputs. (mp3_22050_32, mp3_24000_48, mp3_44100_32, mp3_44100_64, mp3_44100_96, mp3_44100_128, mp3_44100_192, pcm_8000, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, ulaw_8000, alaw_8000, opus_48000_32, opus_48000_64, opus_48000_96, opus_48000_128, opus_48000_192) |
| `text` | string | Sim | The text that will get converted into a sound effect. |
| `loop` | boolean | Não | Whether to create a sound effect that loops smoothly. Only available for the 'eleven_text_to_sound_v2 model'. |
| `duration_seconds` | number | Não | The duration of the sound which will be generated in seconds. Must be at least 0.5 and at most 30. If set to None we will guess the optimal duration using the prompt. Defaults to None. |
| `prompt_influence` | number | Não | A higher prompt influence makes your generation follow the prompt more closely while also making generations less variable. Must be a value between 0 and 1. Defaults to 0.3. |
| `model_id` | string | Não | SFXModelId (eleven_text_to_sound_v2) |

#### `elevenlabs_start_speaker_separation`

Start Speaker Separation. Start speaker separation process for a sample _(POST /api/elevenlabs/start/speaker/separation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `sample_id` | string | Sim | Sample ID to be used |

#### `elevenlabs_stream_chapter_snapshot_audio`

Stream Chapter Audio. Stream the audio from a chapter snapshot. Use `GET /v1/studio/projects/{project_id}/chapters/{chapter_id}/snapshots` to return the snapshots of a chapter. _(POST /api/elevenlabs/stream/chapter/snapshot/audio)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `chapter_id` | string | Sim | The ID of the chapter. |
| `chapter_snapshot_id` | string | Sim | The ID of the chapter snapshot. |
| `convert_to_mpeg` | boolean | Não | Whether to convert the audio to mpeg format. |

#### `elevenlabs_stream_project_snapshot_archive_60141b`

Stream Archive With Studio Project Audio. _(POST /api/elevenlabs/stream/project/snapshot/archive/60141b)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `project_snapshot_id` | string | Sim | The ID of the Studio project snapshot. |

#### `elevenlabs_text_to_dialogue`

Text To Dialogue (Multi-Voice). _(POST /api/elevenlabs/text/to/dialogue)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. So an mp3 with 22.05kHz sample rate at 32kbs is represented as mp3_22050_32. MP3 with 192kbps bitrate requires you to be subscribed to Creator tier or above. PCM and WAV formats with 44.1kHz sample rate requires you to be subscribed to Pro tier or above. Note that the μ-law format (sometimes written mu-law, often approximated as u-law) is commonly used for Twilio audio inputs. (alaw_8000, mp3_22050_32, mp3_24000_48, mp3_44100_128, mp3_44100_192, mp3_44100_32, mp3_44100_64, mp3_44100_96, opus_48000_128, opus_48000_192, opus_48000_32, opus_48000_64, opus_48000_96, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, pcm_8000, ulaw_8000, wav_16000, wav_22050, wav_24000, wav_32000, wav_44100, wav_48000, wav_8000) |
| `enable_logging` | boolean | Não | When enable_logging is set to false zero retention mode will be used for the request. This will mean history features are unavailable for this request, including request stitching. Zero retention mode may only be used by enterprise customers. |
| `inputs` | object[] | Sim | A list of dialogue inputs, each containing text and a voice ID which will be converted into speech. The maximum number of unique voice IDs is 10. For reliable generation, keep the total character count across all `inputs[].text` values at or below 2,000 characters per request. Longer requests can terminate early in streaming responses or return a validation error. |
| `model_id` | string | Não | Identifier of the model that will be used, you can query them using GET /v1/models. The model needs to have support for text to speech, you can check this using the can_do_text_to_speech property. |
| `language_code` | string | Não | Language code (ISO 639-1) used to enforce a language for the model and text normalization. If the model does not support the provided language code, it will be ignored. This parameter is not supported for multilingual_v2 models. |
| `settings` | object | Não | Settings controlling the dialogue generation. |
| `pronunciation_dictionary_locators` | object[] | Não | A list of pronunciation dictionary locators (id, version_id) to be applied to the text. They will be applied in order. You may have up to 3 locators per request |
| `seed` | integer | Não | If specified, our system will make a best effort to sample deterministically, such that repeated requests with the same seed and parameters should return the same result. Determinism is not guaranteed. Must be integer between 0 and 4294967295. |
| `apply_text_normalization` | string | Não | This parameter controls text normalization with three modes: 'auto', 'on', and 'off'. When set to 'auto', the system will automatically decide whether to apply text normalization (e.g., spelling out numbers). With 'on', text normalization will always be applied, while with 'off', it will be skipped. (auto, on, off) |

#### `elevenlabs_text_to_speech_full`

Text To Speech. Converts text into speech using a voice of your choice and returns audio. _(POST /api/elevenlabs/text/to/speech/full)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `enable_logging` | boolean | Não | When enable_logging is set to false zero retention mode will be used for the request. This will mean history features are unavailable for this request, including request stitching. Zero retention mode may only be used by enterprise customers. |
| `optimize_streaming_latency` | integer | Não | You can turn on latency optimizations at some cost of quality. The best possible final latency varies by model. Possible values: 0 - default mode (no latency optimizations) 1 - normal latency optimizations (about 50% of possible latency improvement of option 3) 2 - strong latency optimizations (about 75% of possible latency improvement of option 3) 3 - max latency optimizations 4 - max latency optimizations, but also with text normalizer turned off for even more latency savings (best latency, but can mispronounce eg numbers and dates).  Defaults to None.  |
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. So an mp3 with 22.05kHz sample rate at 32kbs is represented as mp3_22050_32. MP3 with 192kbps bitrate requires you to be subscribed to Creator tier or above. PCM and WAV formats with 44.1kHz sample rate requires you to be subscribed to Pro tier or above. Note that the μ-law format (sometimes written mu-law, often approximated as u-law) is commonly used for Twilio audio inputs. (alaw_8000, mp3_22050_32, mp3_24000_48, mp3_44100_128, mp3_44100_192, mp3_44100_32, mp3_44100_64, mp3_44100_96, opus_48000_128, opus_48000_192, opus_48000_32, opus_48000_64, opus_48000_96, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, pcm_8000, ulaw_8000, wav_16000, wav_22050, wav_24000, wav_32000, wav_44100, wav_48000, wav_8000) |
| `text` | string | Sim | The text that will get converted into speech. |
| `model_id` | string | Não | Identifier of the model that will be used, you can query them using GET /v1/models. The model needs to have support for text to speech, you can check this using the can_do_text_to_speech property. |
| `language_code` | string | Não | Language code (ISO 639-1) used to enforce a language for the model and text normalization. If the model does not support the provided language code, it will be ignored. This parameter is not supported for multilingual_v2 models. |
| `voice_settings` | object | Não | Voice settings overriding stored settings for the given voice. They are applied only on the given request. |
| `pronunciation_dictionary_locators` | object[] | Não | A list of pronunciation dictionary locators (id, version_id) to be applied to the text. They will be applied in order. You may have up to 3 locators per request |
| `seed` | integer | Não | If specified, our system will make a best effort to sample deterministically, such that repeated requests with the same seed and parameters should return the same result. Determinism is not guaranteed. Must be integer between 0 and 4294967295. |
| `previous_text` | string | Não | The text that came before the text of the current request. Can be used to improve the speech's continuity when concatenating together multiple generations or to influence the speech's continuity in the current generation. |
| `next_text` | string | Não | The text that comes after the text of the current request. Can be used to improve the speech's continuity when concatenating together multiple generations or to influence the speech's continuity in the current generation. |
| `previous_request_ids` | string[] | Não | A list of request_id of the samples that were generated before this generation. Can be used to improve the speech's continuity when splitting up a large task into multiple requests. The results will be best when the same model is used across the generations. In case both previous_text and previous_request_ids is send, previous_text will be ignored. A maximum of 3 request_ids can be send. |
| `next_request_ids` | string[] | Não | A list of request_id of the samples that come after this generation. next_request_ids is especially useful for maintaining the speech's continuity when regenerating a sample that has had some audio quality issues. For example, if you have generated 3 speech clips, and you want to improve clip 2, passing the request id of clip 3 as a next_request_id (and that of clip 1 as a previous_request_id) will help maintain natural flow in the combined speech. The results will be best when the same model is used across the generations. In case both next_text and next_request_ids is send, next_text will be ignored. A maximum of 3 request_ids can be send. |
| `use_pvc_as_ivc` | boolean | Não | If true, we won't use PVC version of the voice for the generation but the IVC version. This is a temporary workaround for higher latency in PVC versions. |
| `apply_text_normalization` | string | Não | This parameter controls text normalization with three modes: 'auto', 'on', and 'off'. When set to 'auto', the system will automatically decide whether to apply text normalization (e.g., spelling out numbers). With 'on', text normalization will always be applied, while with 'off', it will be skipped. (auto, on, off) |
| `apply_language_text_normalization` | boolean | Não | This parameter controls language text normalization. This helps with proper pronunciation of text in some supported languages. WARNING: This parameter can heavily increase the latency of the request. Currently only supported for Japanese. |

#### `elevenlabs_text_to_voice_design`

Design A Voice.. Design a voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To create a voi _(POST /api/elevenlabs/text/to/voice/design)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. So an mp3 with 22.05kHz sample rate at 32kbs is represented as mp3_22050_32. MP3 with 192kbps bitrate requires you to be subscribed to Creator tier or above. PCM with 44.1kHz sample rate requires you to be subscribed to Pro tier or above. Note that the μ-law format (sometimes written mu-law, often approximated as u-law) is commonly used for Twilio audio inputs. (mp3_22050_32, mp3_24000_48, mp3_44100_32, mp3_44100_64, mp3_44100_96, mp3_44100_128, mp3_44100_192, pcm_8000, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, ulaw_8000, alaw_8000, opus_48000_32, opus_48000_64, opus_48000_96, opus_48000_128, opus_48000_192) |
| `voice_description` | string | Sim | Description to use for the created voice. |
| `model_id` | string | Não | Model to use for the voice generation. Possible values: eleven_multilingual_ttv_v2, eleven_ttv_v3. (eleven_multilingual_ttv_v2, eleven_ttv_v3) |
| `text` | string | Não | Text to generate, text length has to be between 100 and 1000. |
| `auto_generate_text` | boolean | Não | Whether to automatically generate a text suitable for the voice description. |
| `loudness` | number | Não | Controls the volume level of the generated voice. -1 is quietest, 1 is loudest, 0 corresponds to roughly -24 LUFS. |
| `seed` | integer | Não | Random number that controls the voice generation. Same seed with same inputs produces same voice. |
| `guidance_scale` | number | Não | Controls how closely the AI follows the prompt. Lower numbers give the AI more freedom to be creative, while higher numbers force it to stick more to the prompt. High numbers can cause voice to sound artificial or robotic. We recommend to use longer, more detailed prompts at lower Guidance Scale. |
| `stream_previews` | boolean | Não | Determines whether the Text to Voice previews should be included in the response. If true, only the generated IDs will be returned which can then be streamed via the /v1/text-to-voice/:generated_voice_id/stream endpoint. |
| `should_enhance` | boolean | Não | Whether to enhance the voice description using AI to add more detail and improve voice generation quality. When enabled, the system will automatically expand simple prompts into more detailed voice descriptions. Defaults to False |
| `remixing_session_id` | string | Não | The remixing session id. |
| `remixing_session_iteration_id` | string | Não | The id of the remixing session iteration where these generations should be attached to. If not provided, a new iteration will be created. |
| `quality` | number | Não | Higher quality results in better voice output but less variety. |
| `reference_audio_base64` | string | Não | Reference audio to use for the voice generation. The audio should be base64 encoded. Only supported when using the  eleven_ttv_v3 model. |
| `prompt_strength` | number | Não | Controls the balance of prompt versus reference audio when generating voice samples. 0 means almost no prompt influence, 1 means almost no reference audio influence. Only supported when using the eleven_ttv_v3 model. |

#### `elevenlabs_text_to_voice_preview_stream`

Text To Voice Preview Streaming. _(POST /api/elevenlabs/text/to/voice/preview/stream)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `generated_voice_id` | string | Sim | The generated_voice_id to stream. |

#### `elevenlabs_text_to_voice_remix`

Remix A Voice.. Remix an existing voice via a prompt. This method returns a list of voice previews. Each preview has a generated_voice_id and a sample of the voice as base64 encoded mp3 audio. To crea _(POST /api/elevenlabs/text/to/voice/remix)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `voice_id` | string | Sim | Voice ID to be used, you can use https://api.elevenlabs.io/v1/voices to list all the available voices. |
| `output_format` | string | Não | Output format of the generated audio. Formatted as codec_sample_rate_bitrate. So an mp3 with 22.05kHz sample rate at 32kbs is represented as mp3_22050_32. MP3 with 192kbps bitrate requires you to be subscribed to Creator tier or above. PCM with 44.1kHz sample rate requires you to be subscribed to Pro tier or above. Note that the μ-law format (sometimes written mu-law, often approximated as u-law) is commonly used for Twilio audio inputs. (mp3_22050_32, mp3_24000_48, mp3_44100_32, mp3_44100_64, mp3_44100_96, mp3_44100_128, mp3_44100_192, pcm_8000, pcm_16000, pcm_22050, pcm_24000, pcm_32000, pcm_44100, pcm_48000, ulaw_8000, alaw_8000, opus_48000_32, opus_48000_64, opus_48000_96, opus_48000_128, opus_48000_192) |
| `voice_description` | string | Sim | Description of the changes to make to the voice. |
| `text` | string | Não | Text to generate, text length has to be between 100 and 1000. |
| `auto_generate_text` | boolean | Não | Whether to automatically generate a text suitable for the voice description. |
| `loudness` | number | Não | Controls the volume level of the generated voice. -1 is quietest, 1 is loudest, 0 corresponds to roughly -24 LUFS. |
| `seed` | integer | Não | Random number that controls the voice generation. Same seed with same inputs produces same voice. |
| `guidance_scale` | number | Não | Controls how closely the AI follows the prompt. Lower numbers give the AI more freedom to be creative, while higher numbers force it to stick more to the prompt. High numbers can cause voice to sound artificial or robotic. We recommend to use longer, more detailed prompts at lower Guidance Scale. |
| `stream_previews` | boolean | Não | Determines whether the Text to Voice previews should be included in the response. If true, only the generated IDs will be returned which can then be streamed via the /v1/text-to-voice/:generated_voice_id/stream endpoint. |
| `remixing_session_id` | string | Não | The remixing session id. |
| `remixing_session_iteration_id` | string | Não | The id of the remixing session iteration where these generations should be attached to. If not provided, a new iteration will be created. |
| `prompt_strength` | number | Não | Controls the balance of prompt versus reference audio when generating voice samples. 0 means almost no prompt influence, 1 means almost no reference audio influence. Only supported when using the eleven_ttv_v3 model. |

#### `elevenlabs_unshare_resource_endpoint`

Unshare Workspace Resource. Removes any existing role on a workspace resource from a user, group, or workspace (service account) API key. To target a user or service account, pass only the user email; _(POST /api/elevenlabs/unshare/resource/endpoint)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `resource_id` | string | Sim | The ID of the target resource. |
| `resource_type` | string | Sim | Resource types that can be shared in the workspace. The name always need to match the collection names (voice, voice_collection, pronunciation_dictionary, dubbing, project, convai_agents, convai_knowledge_base_documents, convai_tools, convai_settings, convai_secrets, workspace_auth_connections, convai_phone_numbers, convai_mcp_servers, convai_api_integration_connections, convai_api_integration_trigger_connections, convai_batch_calls, convai_agent_response_tests, convai_test_suite_invocations, convai_crawl_jobs, convai_crawl_tasks, convai_kb_external_sync_jobs, convai_whatsapp_accounts, convai_agent_versions, convai_agent_branches, convai_agent_versions_deployments, convai_memory_entries, convai_coaching_proposals, convai_templates, dashboard, dashboard_configuration, convai_agent_drafts, resource_locators, assets, content_generations, content_templates, songs, transcription_tasks, avatars, avatar_video_generations, resource_collection, studio_projects, convai_analysis_items) |
| `user_email` | string | Não | The email of the user or service account. |
| `group_id` | string | Não | The ID of the target group. Use 'default' to set the resource's baseline role — every workspace member receives this role unless they hold a higher one through a direct user grant, group membership, or workspace (service account) API key. |
| `workspace_api_key_id` | string | Não | The ID of the target workspace (service account) API key. This is not the API key string itself that you pass in the header for authentication — it is the key's ID, which workspace admins can find under Developers → Service Accounts. |

#### `elevenlabs_update_auth_connection`

Update Workspace Auth Connection. _(POST /api/elevenlabs/update/auth/connection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `auth_connection_id` | string | Sim | Auth Connection Id |
| `body` | object | Sim | Updated auth connection fields |

#### `elevenlabs_update_finetune`

Update Music Finetune. Update a music finetune. _(POST /api/elevenlabs/update/finetune)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `finetune_id` | string | Sim | Finetune Id |
| `name` | string | Não | Updated name for the finetune. |
| `tags` | string[] | Não | Replacement set of tags. |
| `primary_genre` | string | Não | Updated primary musical genre. |
| `visibility` | string | Não | Finetune visibility. Only 'private' and 'workspace' can be set. (private, workspace) |

#### `elevenlabs_update_pronunciation_dictionaries`

Create Pronunciation Dictionaries. _(POST /api/elevenlabs/update/pronunciation/dictionaries)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `project_id` | string | Sim | The ID of the Studio project. |
| `pronunciation_dictionary_locators` | object[] | Sim | A list of pronunciation dictionary locators (pronunciation_dictionary_id, version_id) encoded as a list of JSON strings for pronunciation dictionaries to be applied to the text. A list of json encoded strings is required as adding projects may occur through formData as opposed to jsonBody. To specify multiple dictionaries use multiple --form lines in your curl, such as --form 'pronunciation_dictionary_locators="{\"pronunciation_dictionary_id\":\"Vmd4Zor6fplcA7WrINey\",\"version_id\":\"hRPaxjlTdR7wFMhV4w0b\"}"' --form 'pronunciation_dictionary_locators="{\"pronunciation_dictionary_id\":\"JzWtcGQMJ6bnlWwyMo7e\",\"version_id\":\"lbmwxiLu4q6txYxgdZqn\"}"'. |
| `invalidate_affected_text` | boolean | Não | This will automatically mark text in this project for reconversion when the new dictionary applies or the old one no longer does. |

#### `elevenlabs_update_speech_engine`

Update Speech Engine. Update a Speech Engine resource (partial update) _(POST /api/elevenlabs/update/speech/engine)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `speech_engine_id` | string | Sim | The speech engine ID (accepts seng_ or agent_ prefix) |
| `name` | string | Não | Name |
| `speech_engine` | object | Não |  |
| `asr` | object | Não |  |
| `tts` | object | Não |  |
| `turn` | object | Não |  |
| `vad` | object | Não |  |
| `conversation` | object | Não |  |
| `privacy` | object | Não |  |
| `call_limits` | object | Não |  |
| `language` | string | Não | Language |
| `tags` | string[] | Não | Tags |
| `overrides` | object | Não |  |

#### `elevenlabs_update_workspace_member`

Update Member. Updates attributes of a workspace member. Apart from the email identifier, all parameters will remain unchanged unless specified. This endpoint may only be called by workspace administr _(POST /api/elevenlabs/update/workspace/member)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Sim | Email of the target user. |
| `is_locked` | boolean | Não | Whether to lock or unlock the user account. |
| `workspace_role` | string | Não | The workspace role of the user. This is deprecated, use `workspace_seat_type` instead. (workspace_admin, workspace_member, workspace_lite_member) |
| `workspace_seat_type` | string | Não | The workspace seat type (workspace_admin, workspace_member, workspace_lite_member) |

#### `elevenlabs_usage_by_product_over_time`

Get Workspace Usage. Returns credit usage broken down by product type over time. The response is a tabular structure with columns, column_types, column_units, and rows. _(POST /api/elevenlabs/usage/by/product/over/time)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_time` | integer | Sim | Start of the time range as a Unix timestamp in milliseconds. Must be at least 2020-01-01. |
| `end_time` | integer | Sim | End of the time range as a Unix timestamp in milliseconds. Must be at least 2020-01-01. |
| `interval_seconds` | integer | Não | Bucket size in seconds. Each row in the response covers this many seconds of the selected time range. For example, pass 3600 for hourly buckets or 86400 for daily buckets. Whether `time_zone` shifts bucket boundaries depends on this value: whole-day multiples (e.g. 86400) align to local midnight; whole-hour multiples up to 24 hours (e.g. 3600, 14400) align to local hour boundaries from midnight; sub-hour values and other sizes remain UTC-anchored regardless of `time_zone`. |
| `group_by` | string[] | Não | Group By (product_type, model, voice_id, user_id, fiat_currency, fiat_charge_type, region, reporting_workspace_id, request_source, resource_id, subresource_id, request_queue_type, voice_multiplier, hashed_xi_api_key, billing_group_id, surface, actor) |
| `filters` | object[] | Não | Filters |
| `time_zone` | string | Não | IANA time zone identifier (e.g. 'America/New_York', 'Europe/London', 'UTC') used to align bucket boundaries for eligible `interval_seconds` values. Whole-day multiples start at local midnight; whole-hour multiples up to 24 hours align to local hour boundaries from midnight. Sub-hour intervals and other bucket sizes remain UTC-anchored regardless of this setting. Defaults to UTC. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_elevenlabs` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
