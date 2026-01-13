# eYAML

A very thin YAML wrapper over [eJSON](https://github.com/Shopify/ejson).

eYAML lets you use eJSON with YAML files instead of JSON.

It converts YAML to JSON, runs ejson, and converts back.

### Dependencies

- [ejson](https://github.com/Shopify/ejson)
- [yq](https://github.com/mikefarah/yq) (Mike Farah's implementation)

### Usage

All subcommands, flags, options, and arguments are proxied to the `ejson` command, the behavior is identical except for working on YAML files:

```bash
eyaml encrypt secrets.eyml
eyaml decrypt secrets.eyml
```

Use `.eyml` or `.eyaml` file extensions.

### Example

Create `secrets.eyml`:
```yaml
_public_key: 85d47d85be8...

database:
  host: localhost
  password: supersecret
```

After `eyaml encrypt secrets.eyml`:
```yaml
_public_key: 85d47d85be8...

database:
  host: "EJ[1:AbC12x...]"
  password: "EJ[1:KP3wLB...]"
```

The `decrypt` command outputs decrypted YAML to stdout.

### See Also

See [ejson](https://github.com/Shopify/ejson) for key generation, key management, encryption details, and file format rules.
