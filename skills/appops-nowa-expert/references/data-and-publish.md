# Data and publishing

## Data
- **REST APIs** (APIs tab): paste a cURL, or import Swagger/Postman; Nowa generates models with `fromJson` (missing fields fall back to defaults since 3.14.1). Keep base URLs and keys out of the UI package: secrets belong on the server; per-environment values via the developer plugin's config.
- **Supabase**: URL + anon key; Nowa writes `supabase_service.dart` in the integrations folder; Nowa AI turns on RLS for tables it creates. Never paste the service-role key.
- **Firebase / Firestore**: Data panel → Firestore tab; Firebase Auth panel handles SHA-1.
- **Shared state across screens**: Nowa's data features suit prototypes; for an app with a real data layer (Riverpod, offline sync), keep data in code and pass plain values into Nowa widgets.
- **Translations**: board Language picker; Nowa writes ARB files and `l10n.yaml` and regenerates `AppLocalizations` (3.16.2+).

## Publishing (needs the user's yes each time)
| Target | How | Plan |
|---|---|---|
| Web | One click to `yourapp.nowa.dev`, custom domain, or download the web build and host it yourself (for example Cloudflare Pages) | Launch+ (12 h test links on all plans) |
| Android | Cloud build → AAB + APK with the user's keys or Nowa-generated ones | Launch+ |
| iOS | Cloud build → TestFlight, no Mac needed | Launch+ |
| Windows / macOS / Linux desktop | Not a Nowa cloud target in the docs reviewed: build from code with the developer plugin (`flutter build windows`) | — |
Store fees: Google $25 once, Apple $99/year. Plan names and prices: check the user's account page (the public pricing page and older docs disagree).
