# Tech Context

## Technologies Used

*   **Languages:** TypeScript
*   **Frameworks/Libraries:** Node.js, React (via Ink), Commander.js, Anthropic SDK, OpenAI SDK, MCP SDK
*   **Databases:** N/A (Stateless CLI, configuration stored locally)
*   **Infrastructure:** N/A (Runs locally on user's machine)
*   **Key APIs/Services:** OpenAI-compatible AI model APIs (e.g., Anthropic Claude, OpenAI GPT, Bedrock, Vertex)

## Development Setup

*   **Prerequisites:** Node.js >= 18.0.0 (as per `package.json`), `pnpm` (implied by `pnpm i` command in README)
*   **Installation Steps:** `pnpm i`
*   **Running the Application (Dev):** `pnpm run dev` or `NODE_ENV=development pnpm run dev --verbose --debug` for more logs.
*   **Building for Production:** `pnpm run build` (creates `cli.mjs`)
*   **Testing:** No specific test script defined in `package.json` (`test` script missing).

## Technical Constraints

*   Requires Node.js >= 18.
*   Relies on external AI provider APIs and user-provided API keys/endpoints.
*   Terminal environment limitations for UI rendering (handled by Ink).

## Dependencies

*   **Package Manager:** `pnpm` (based on README dev instructions)
*   **Key Dependencies:**
    *   `@anthropic-ai/sdk`, `@anthropic-ai/bedrock-sdk`, `@anthropic-ai/vertex-sdk`, `openai`: AI model clients
    *   `ink`, `@inkjs/ui`, `react`: Terminal UI rendering
    *   `commander`: CLI argument parsing
    *   `@modelcontextprotocol/sdk`: MCP integration
    *   `typescript`, `tsx`: Language and execution
    *   `zod`: Schema validation (likely for configurations or API responses)
    *   `diff`: Calculating text differences (likely for file editing tools)
    *   `glob`, `chalk`, `figures`, `cli-highlight`, `marked`: CLI utilities and formatting

## Tool Usage Patterns

*   **Linters/Formatters:** `prettier` (`pnpm run format`, `pnpm run format:check`)
*   **Build Tools:** `bun build` (specified in `build` script)
*   **Version Control:** Git (Repository hosted on GitHub)
*   **Debugging:** `debug` library (suggested by `NODE_ENV=development ... --debug` command)
