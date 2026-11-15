# ce-net demos

Fifteen demos of things a network of ordinary devices can do together: render one frame on several machines, survive a
killed server without losing a write, hand a stranger a key that does exactly one thing, and more. Each one is its own
repo, Apache-2.0, built from reusable ce-net cells, with its recorded proof in the repo.

Browse them as a page: https://ce-net.github.io/demos/ (also at [ce-net.com/demos](https://ce-net.com/demos/)).

**Works** means we re-ran it from a fresh clone and it reproduced the numbers in its README.
**Partly** means the code and the recorded proof are public, and the note says which part you cannot reproduce from
outside yet.

## Works

- [Render across devices](https://github.com/ce-net/demo-render-compute): One image, rendered by several machines at
  once. The result is pixel-identical to a single-machine render.
- [Kill a node, keep the data](https://github.com/ce-net/demo-self-healing): Kill the server holding the data, live.
  Every saved write survives, and the page proves it with a hash chain.
- [An engineering result you can re-check](https://github.com/ce-net/demo-verified-result): A physics result that comes
  with a certificate. Re-check it in your own browser: same code, same inputs, same answer.
- [Print only through the guard](https://github.com/ce-net/demo-printer-guard): Send a print job straight to the printer and it is
  refused. Send it through the guard, which checks bounds, temperatures, material and time: the 300 C job is rejected,
  the safe one prints, and a replay of the forwarded call is refused.
- [Every call leaves a receipt](https://github.com/ce-net/demo-demo-signed-receipts): Run 200 calls across four cells, download the receipts, and check them
  on any machine with no network. Edit one and the verifier names it; drop one and the chain shows the gap.
- [Shared with my devices, nobody else's](https://github.com/ce-net/demo-demo-own-devices-only): Enroll your laptop, phone and desktop with a pairing code; each gets a key
  bound to that device. A copied key file is refused, and a lost phone is revoked from the laptop while the other two
  keep working.
- [A factory line you can audit](https://github.com/ce-net/demo-demo-line-twin): A three-station line runs as a twin and drill becomes the bottleneck. Download the signed event log: your browser checks every signature and recomputes the numbers. Edit one timestamp and it names the event that broke.

## Partly

- **Partly.** [One prompt, many devices](https://github.com/ce-net/demo-inference): Ask a question and see which device
  answers. When one device drops out, the answer keeps streaming from another.
  *The recorded run is in the repo; the live two-device page is not public yet.*
- **Partly.** [Follow-me cell](https://github.com/ce-net/demo-follow-me): A service that moves to whichever machine is
  closest to you, and keeps answering by the same name while it moves.
  *The restart on one device is recorded; a move between two devices is not recorded yet.*
- **Partly.** [Playground: deploy a cell in your browser](https://github.com/ce-net/demo-playground): Write a cell in
  your browser, deploy it to a real network, and call it from three languages, all within a minute.
  *Code and tests are public; the hosted playground is not live yet.*
- **Partly.** [A stranger gets exactly one action](https://github.com/ce-net/demo-one-pinned-action): We give you a key
  that does exactly one thing. Try to make it do more. Every attempt is refused, and the page shows you the rule that
  refused it. *The build needs a protocol crate that is not published yet.*
- **Partly.** [Same data, browser and terminal, live](https://github.com/ce-net/demo-live-typed-data): Change a value in
  your browser and see it change in a terminal and on a 3D factory map at the same moment. One schema, no server code.
  *Recorded logs are in the repo; not yet re-run from a fresh clone.*
- **Partly.** [Search everything you are allowed to see](https://github.com/ce-net/demo-mesh-search): One search box
  across many machines. You only get back what your key allows, and the rest never leaves the machine it lives on.
  *The recorded report is in the repo; the build needs crates that are not published yet.*
- **Partly.** [Any program becomes a mesh service in one command](https://github.com/ce-net/demo-wrap-anything): Turn
  any open-source program into a network service with one command. Then use it from your browser: same output, byte for
  byte. *Tests pass locally; parity across machines is not re-checked here, and one dependency is not public yet.*

## Advanced

Large distributed systems on the cell network: many cell instances, each with its own identity, spread over the
real machines we have, and built to take more machines with no config change.

- **Partly.** [Sharded search: one leader per shard, rebalanced live](https://github.com/ce-net/demo-sharded-search): 4.6 million Wikipedia abstracts in 32 shards with 3 replicas each, one leader per shard. Kill a machine under a query loop that never stops: new leaders within one lease, replicas back to three, recall unchanged.
  *Recorded run: 96 instances, 7 leaders lost with machine-c, new leaders within 3.65 s, all shards back to 3 replicas in 6.57 s, 0 failed queries, recall@10 0.9202 before and after. All machines are processes on one server; the ce-net crates it was designed around are replaced by public stand-ins.* [Page](https://ce-net.github.io/demo-sharded-search/)

The same list as data, for tools and search: [demos.json](demos.json).

New to ce-net? Start with the [starter packs](https://github.com/ce-net/starters).

## License

Apache-2.0. See [LICENSE](LICENSE).
