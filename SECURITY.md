# Security & Data Handling

## Organization Plans (Team / Enterprise)

If you're using Claude through your organization's Team or Enterprise plan, your data is handled according to your organization's agreement with Anthropic. Conversations and uploaded files stay within your organization's boundary.

## Individual Plans (Pro / Free)

If you're using a personal Claude account, be mindful that diagnostic bundles may contain sensitive information such as IP addresses, cluster names, index names, and configuration details. Review and mask sensitive data before uploading if needed.

The `support-diagnostics` tool includes a separate sanitization utility (`scrub.sh` / `scrub.bat`) that automatically obfuscates all node IDs, node names, IPv4, IPv6, and MAC addresses. You can also configure additional tokens in `scrub.yml` to mask custom strings like cluster names or index names. Run it against a diagnostic archive before sharing:

```bash
./scrub.sh -i /path/to/diagnostics-20250401-120000.zip
```

This produces a new archive prefixed with `scrubbed-` containing the sanitized data.

For ECE, ECK, and Elastic Agent diagnostics, you can also use the sanitization utility (`scrub.sh` / `scrub.bat`), but you must unzip the bundle first, scrub the extracted directory, then zip it back up.

## For Contributors

- Never include real customer data, credentials, or PII in issues, PRs, or examples
- Sanitize all identifiable information in example analyses
- Do not commit diagnostic bundle files to this repository

## Disclaimer

This is not an official Elastic product. Analysis results are AI-generated and may contain inaccuracies. Always review and validate recommendations with qualified engineers before applying changes to production systems.
