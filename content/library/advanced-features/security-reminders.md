---
title: Security reminders
slug: /library/advanced-features/security-reminders
---

# Security reminders

## Protect your secrets

Never save usernames, passwords, or security keys directly in your code or commit them to your repository.

### Use environment variables

Avoid putting sensitve information in your code by using environment variables. Be sure to check out [`st.secrets`](/library/advanced-features/secrets-management). Research any platform you use to follow their security best practices. If you use Streamlit Community Cloud, [Secrets management](/streamlit-community-cloud/deploy-your-app/secrets-management) allows you save environment variables and store secrets outside of your code.

### Keep `.gitignore` updated

If you use any sensitive or private information during development, make sure that information is saved in separate files from your code. Ensure `.gitginore` is properly configured to prevent saving private information to your repository.

## Pickle warning

Streamlit's [`st.cache_data`](/library/advanced-features/caching#stcache_data) and [`st.session_state`](/library/advanced-features/session-state#serializable-session-state) implicitly use the `pickle` module, which is known to be insecure. It is possible to construct malicious pickle data that will execute arbitrary code during unpickling. Never load data that could have come from an untrusted source in an unsafe mode or that could have been tampered with. **Only load data you trust**.

- When using `st.cache_data`, anything your function returns is pickled and stored, then unpickled on retrieval. Ensure your cached functions return trusted values. This warning also applies to [`st.cache`](/library/api-reference/performance/st.cache) (deprecated).
- When the `runner.enforceSerializableSessionState` [configuration option](<(/library/advanced-features/configuration#runner)>) is set to `true`, ensure all data saved and retrieved from Session State is trusted.
