# ghost-hex

Invisible Unicode encoder/decoder built on Variation Selectors (VS17-VS144).

Ghost-hex maps ASCII bytes (0x00-0x7F) onto VS17 (U+E0100) through VS144
(U+E017F). The encoded payload is appended as trailing variation selectors
after the last character of the carrier text. No other wrappers or markers
are used.

## Web UI

Open `index.html` in a browser and use the Encode / Decode panels.

- Carrier text and payload text are editable inputs.
- Payload must be ASCII (0x00-0x7F).
- Encoded output is carrier + invisible payload (VS17-VS144).

## Python CLI

Encode:

```
python ghost_hex.py encode --carrier "cover text" --payload "secret"
```

Decode:

```
python ghost_hex.py decode --text "<encoded text>"
```

## Notes

- Variation selectors attach to the final carrier character. If the carrier
  is empty, the payload may be dropped by some renderers.
- Decoding only reads trailing VS17-VS144 characters.
