# uniency-cewp-adapter

Private AGPL-3.0 adapter between the uniency Universal SDK core and CEWP/CIRIS.

**Status:** no adapter source has been written yet. This repository holds the licence and a description of the intended role so the process boundary is documented before code lands. This repository is private and is not a public release.

## Licence

[GNU Affero General Public License v3.0](LICENSE) (AGPL-3.0).

The SDK core (`uniency-sdk`) is separately licensed Apache-2.0 OR MIT and must not depend on this adapter, or on any `ciris-*` / `cewp-*` crate, at build or link time.

## Role

This adapter is a **separate AGPL service** that sits behind an **IPC process boundary**. The permissive SDK core talks to it only over that boundary (for example a local socket or stdin/stdout protocol). CIRIS and CEWP types, crates, and wire codecs live only on this side of the wall.

## CIRISVerify pin

When the adapter is implemented, it pins CIRISVerify at:

- **rev `cbcd9576`** (tag **v22.0.0**)

That pin applies only to this adapter, not to the SDK core. Later Verify / Edge / Server revisions used for research notes do not automatically move this pin.

## Intended work (not yet present)

- Translate between the SDK's own wire and signature formats and CIRIS/CEWP formats
- Interop tests in both directions, plus a round-trip test for each translation
- The bound-hybrid CIRIS construction stays in this process; the core keeps its own clean-room implementation and formats
- Licence policy on this side is AGPL; do not re-licence or vendor this tree into `uniency-sdk`

## Related private repositories

- `uniency-sdk` — permissive Rust core (docs only in the current snapshot)
- `uniency-business` — claims ledger and unanswered CIRIS questions (draft, nothing sent)
