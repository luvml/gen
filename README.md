# gen

**The code generator that produces luvml's machine-generated DSL classes — `luvml.E` (HTML elements) and `luvml.A` (HTML attributes) — from a maintained specification, using JavaPoet.**

```xml
<dependency>
    <groupId>io.github.luvml</groupId>
    <artifactId>gen</artifactId>
    <version>2.0</version>
</dependency>
```

**Requires:** JDK 21+ · depends on [luvx-base](https://github.com/luvml/luvx-base) and [luvml](https://github.com/luvml/luvml)

## What it does

`luvml`'s element and attribute factory methods (`div()`, `href()`, and hundreds more) are not hand-written — they're generated from tables of HTML element/attribute metadata (content categories, display types, allowed contexts, etc.), so the whole surface can be regenerated consistently rather than maintained by hand one method at a time.

- **`HtmlElementsGenerator`** — generates `luvml.E`, one static factory method per HTML element.
- **`HtmlAttributesGenerator`** — generates `luvml.A`, one static factory method per HTML attribute.
- **`CodeGenerator`** — runs both and writes the result into the `luvml` module's source tree.

## Running it

This is a development tool for maintaining luvml itself, not a runtime dependency of anything built with luvml.

```bash
mvn compile exec:java -Dexec.mainClass=luvml.gen.CodeGenerator
```

By default it writes into `../luvml/src/main/java/luvml`, i.e. it expects to be run from a checkout laid out as a sibling of the `luvml` module (as in the [luvml org](https://github.com/luvml)'s repo layout).

## Related Projects

- **[luvml](https://github.com/luvml/luvml)** — the library whose `E`/`A` classes this generates
- **[luvjfx-gen](https://github.com/luvml/luvjfx-gen)** — the equivalent generator for [luvjfx](https://github.com/luvml/luvjfx), reflecting over the JavaFX API instead of a hand-maintained HTML spec

## License

Apache License 2.0 — see [LICENSE](LICENSE).
