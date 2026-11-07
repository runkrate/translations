# KRATE Translations

Shared localization catalogs for **zen / zenfw (CLI)** and **HarmonyUI (web)**.

Installed on a KRATE host as:

```text
/opt/Krate/share/translations/{lang}/{cli|web}/{domain}.yaml
```

## Layout

```text
en/
  cli/
    messages.yaml              # zenfw::intl (flat dotted keys, {arg0} placeholders)
  web/
    messages+intl-icu.yaml     # Symfony ICU domain
    validators.yaml
    security.yaml
    ResetPasswordBundle.yaml
    VerifyEmailBundle.yaml
    AutocompleteBundle.yaml
fr/
  …
```

- Locale is the **directory** name (`en`, `fr`, …).
- Surface is `cli` or `web`.
- Domain is the YAML basename (no locale suffix).

## Adding a language

1. Copy `en/` to `{code}/`.
2. Translate values (keep keys identical).
3. Ship via a KRATE release; zen and HarmonyUI discover languages from this tree.

## Consumers

| Surface | Path used at runtime |
| --- | --- |
| zen / zenfw | `{KRATE_HOME}/share/translations/{lang}/cli/messages.yaml` |
| HarmonyUI | `{KRATE_HOME}/share/translations/{lang}/web/*.yaml` |

Override root with `KRATE_TRANSLATIONS_DIR` when developing against a local checkout.

## Development

Clone next to `console` / `web`:

```text
runkrate/
  translations/   # this repo
  cli/console/
  web/
```

Release packaging clones this repository and stages it under `/opt/Krate/share/translations/`.
