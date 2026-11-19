# Evidence for #4529

## Settings › Plugins › VM options demo
`after-settings-plugins.png` — installed plugin shows `java.agent` description with exact JVM options, jar label, and JVM options line (`-XX:+AllowEnhancedClassRedefinition (jetbrains)`).

## Tests
```
cargo test -p ide-run --lib java_agent
cargo test -p ide-host --lib plugins::java_agents
cargo test -p ide-host --test plugins java_agent
cargo test -p ide-plugin --test api_compat -- wit_package_engine_and_api_versions_agree shipped_components the_version_check
pnpm vitest run src/features/plugins/__tests__/plugins.test.tsx src/platform/locales/textCatalog.test.ts
pnpm gen:bindings
plugins/build.sh
```
