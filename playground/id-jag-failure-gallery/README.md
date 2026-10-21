# ID-JAG Failure Gallery

**Thesis: learn the hard way, teach the easy way.**

This is the zero-setup intuition layer for the Identity Assertion JWT
Authorization Grant (ID-JAG) — the new OAuth grant that lets AI agents act on
a user's behalf without consent-screen hell (Okta's XAA model).

Five interactive scenarios. Pick one, hit **▶ Run it**, watch the animation
step through the actors, and read where the denial lands:

1. **The expired assertion** — grant presented 10 min after issuance (valid 5) → dies on `exp`
2. **The wrong audience** — minted for the calendar API, presented to the docs API → dies on `aud`
3. **The overreach** — agent asks `admin:write`, policy allows `docs:read` → dies *before a token ever exists* (IdP refuses to issue)
4. **The tampered signature** — attacker flips a scope claim mid-flight → dies on signature verification against the IdP's keys
5. **The replay** — valid grant captured and played twice → dies on single-use `jti` tracking

The pattern that matters: enforcement lives in **two** places — the IdP at
issuance (policy decisions) and the resource server at exchange
(cryptographic validation). Most "why did my flow fail" sessions end the
moment you internalize that split.

## Run it

Open `index.html` in a browser. That's it — static page, vanilla JS, zero
dependencies, zero setup. Everything is honestly labeled as simulated.

## Go deeper

- Live happy-path flow: [xaa.dev](https://xaa.dev)
- Real infrastructure, learn through intentional failures:
  [ID-JAG The Hard Way](https://github.com/athenz-community/id-jag-the-hard-way)
- The spec itself:
  [draft-ietf-oauth-identity-assertion-authz-grant-02](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-identity-assertion-authz-grant-02)

## Roadmap

- **v1** (done): the Failure Gallery — five break-it scenarios
- **v2**: agent attacker view — compromised-agent scenarios (prompt injection
  steering a tool call, the confused deputy, blast radius with and without
  identity-centric controls)
- **v3**: the why-layer — consent fatigue visualized, shadow-IT sprawl map
- **Foundation track** (parallel): OIDC/PKCE visualizer, WebAuthn ceremonies,
  JWT inspector — the classic flows the agentic stuff stands on

## Study path

Work through [id-jag-the-hard-way](https://github.com/athenz-community/id-jag-the-hard-way)
module by module; each failure personally caused on real infrastructure makes
the corresponding gallery scenario authoritative instead of illustrative.
