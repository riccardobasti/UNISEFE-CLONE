# UNISEFE-CLONE
WP PLUGIN

**Version:** 0.0.1  
**Platform:** WordPress  
**Type:** Admin utility / content duplication  
**Architecture:** Single-file plugin  
**JavaScript:** None  
**AJAX:** None  
**License:** MIT  

---

UNISEFE Clone is a minimal WordPress plugin for duplicating posts, pages and custom post types directly from the native WordPress admin interface.

The plugin follows a simple rule:

> Use WordPress before replacing WordPress.

No custom interface is added.  
No JavaScript is loaded.  
No AJAX layer is introduced.  
No framework is required.

The entire runtime lives in a single PHP file.

---

## Main Features

- Clone posts directly from the native WordPress row actions.
- Works with posts, pages and supported custom post types.
- Creates the duplicated content as a draft.
- Copies title, content and excerpt.
- Copies parent, menu order and password.
- Copies taxonomies and assigned terms.
- Copies custom fields and post metadata.
- Opens the cloned item directly in the WordPress editor.
- Uses native WordPress permissions and nonce verification.
- No settings page.
- No JavaScript.
- No AJAX.
- No external dependencies.

---

## Native WordPress Flow

```text
Posts / Pages / Custom Post Types
                │
                ▼
             Clone
                │
                ▼
        Nonce verification
                │
                ▼
      Capability verification
                │
                ▼
        wp_insert_post()
                │
         ┌──────┴──────┐
         ▼             ▼
      Metadata      Taxonomies
         │             │
         └──────┬──────┘
                ▼
          New draft
                │
                ▼
      WordPress editor
```

UNISEFE Clone does not create a parallel administration system.

It extends the workflow WordPress already provides.

---

## Architecture

The plugin is intentionally implemented as a single-file WordPress runtime.

```text
unisefe-clone/
│
├── unisefe-clone.php
├── README.md
└── LICENSE
```

Runtime:

```text
unisefe-clone.php
```

There are no frontend assets, package managers, build systems or external runtime dependencies.

---

## What Is Cloned

| Data | Cloned |
|---|---:|
| Post title | Yes |
| Post content | Yes |
| Post excerpt | Yes |
| Post parent | Yes |
| Menu order | Yes |
| Post password | Yes |
| Taxonomies | Yes |
| Terms | Yes |
| Custom fields | Yes |
| Post metadata | Yes |
| `_edit_lock` | No |
| `_edit_last` | No |

The duplicated item receives a new WordPress post ID and is created as a draft.

---

## Native WordPress Integration

The plugin relies on WordPress core APIs and admin hooks.

```php
post_row_actions
page_row_actions
admin_action_unisefe_clone
wp_nonce_url()
check_admin_referer()
current_user_can()
wp_insert_post()
get_post_meta()
add_post_meta()
wp_get_object_terms()
wp_set_object_terms()
wp_safe_redirect()
```

No custom router is required.

No client-side action layer is required.

No asynchronous request layer is required.

---

## Security

Every clone request is validated through the native WordPress security model:

- capability verification;
- nonce verification;
- valid source-post verification;
- safe admin redirects.

The plugin does not expose a public cloning endpoint.

---

## Design Principle

UNISEFE plugins follow a deliberately small architecture.

```text
WordPress first
PHP first
Native admin first
Single file when possible
Vanilla JavaScript only when necessary
AJAX only when technically necessary
No unnecessary dependencies
```

The objective is not to reduce code at any cost.

The objective is to avoid building a second system when WordPress already provides the required mechanism.

---

## Why No JavaScript?

Cloning is a server-side operation.

WordPress already provides:

- authenticated admin requests;
- row actions;
- nonces;
- capability checks;
- redirects;
- the native editor.

Adding JavaScript would not improve the operation.

```text
JavaScript = 0
AJAX       = 0
```

---

## Installation

1. Download the plugin.
2. Upload the `unisefe-clone` folder to:

```text
/wp-content/plugins/
```

3. Activate **UNISEFE Clone** from the WordPress Plugins screen.
4. Open Posts, Pages or a supported custom post type.
5. Click **Clone** below the content you want to duplicate.

The new copy is created as a draft and opened in the native WordPress editor.

---

## Project Status

**0.0.1 — Initial UNISEFE release**

The plugin intentionally performs one operation:

```text
CLONE
```

No settings panel is included.

No additional interface is included.

Additional code should be introduced only when a real requirement exists.

---

## UNISEFE Philosophy

```text
one task
one native workflow
one small plugin
one file when possible
```

A WordPress plugin should use WordPress before attempting to replace it.

---

## Author

**Riccardo Bastillo**  
UNISEFE

---

## License

MIT License
