# UI foundations and starter boundaries

Choose one primary foundation. Record version, keyboard behavior, accessibility, tokens, and theming. Combining several libraries by default increases integration work without an established benefit.

Approximate stars and observed activity below are as of 2026-10-25.

| Reference / stars | License / activity | Read first | Selection reason and caveat |
|---|---|---|---|
| [shadcn/ui](https://github.com/shadcn-ui/ui), 126.5k | MIT; 2026-10-25 | `apps`, `packages` | Active adopted source-ownership model; inspect registry/CLI and primitive behavior |
| [Mantine](https://github.com/mantinedev/mantine), 31.9k | MIT; 2026-10-25 | `packages`, `apps` | Active integrated widgets/forms/hooks for application UIs; verify component tests |
| [Chakra](https://github.com/chakra-ui/chakra-ui), 40.7k | MIT; 2026-10-22 | `packages`, `apps` | Active token/recipe/composition foundation; APIs depend on version |
| [next-forge](https://github.com/haydenbleasel/next-forge), 7.7k | MIT, Vercel copyright; 2026-05-28 | `apps`, `packages`, `turbo/generators`, `skills/next-forge` | Opinionated monorepo narrowly within six months; remove unused vendors and inspect billing/privacy costs |
| [SaaS UI](https://github.com/saas-js/saas-ui), 1.7k | MIT OSS; Pro separate; 2026-10-15 | `packages`, `apps` | Active niche forms/layouts; paid product rights are distinct |

Taxonomy, create-t3-app, and Tremor Raw failed the maintenance gate and were moved to [superseded.md](superseded.md).

Test loading, error, empty, validation, keyboard-focus, and narrow-screen states. A happy-path screenshot is not accessibility or usability evidence. Review nested assets/licenses before copying source.

## Pending: not yet inspected

- [Supastarter](https://supastarter.dev/): product page updated 2026-10-09, but substantive starter source was inaccessible as of 2026-10-25. No source or licence audit and no redistribution grant; not an admitted implementation recommendation.
