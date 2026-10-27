# Running AI Job Search Locally

To set up this repository locally, I have reviewed the dependencies and documentation (`SETUP.md`).

Here is a summarized list of what you need to do to get it running locally. The codebase utilizes `bun` for job search tooling, `latex` for rendering PDFs (Cover Letters & CVs), and `claude-code` for executing the AI agent.

### Prerequisites you need to install / ensure:
1. **Python 3.10+**: Run `python3 --version` to ensure you have Python 3.10+ installed. This is required for the salary lookup tool.
2. **Bun**: Run `curl -fsSL https://bun.sh/install | bash` to install Bun (on macOS/Linux), or use `winget install Oven-sh.Bun` on Windows. Bun runs the job search CLIs.
3. **LaTeX Distribution**: You need a LaTeX distribution to compile the generated `.tex` files.
   - **Linux**: `sudo apt install texlive-full`
   - **macOS**: Install MacTeX (`brew install --cask mactex`)
   - **Windows**: Install MiKTeX.
   *(Note: The `texlive-full` and `poppler-utils` packages are currently installing in the background on this sandbox environment, but you will need to install them locally).*
4. **Claude Code**: You need the Anthropic CLI installed and authenticated.
   - Run `npm install -g @anthropic-ai/claude-code`
   - You need an Anthropic API key or Claude Pro/Team subscription. Follow [Claude Code's docs](https://docs.anthropic.com/en/docs/claude-code) to configure your authentication.

### Local Setup Steps:

1. **Install Portal CLI Dependencies**:
   Run the following command from the repository root:
   ```bash
   python3 tools/install_portal_clis.py
   ```
   *(Note: I have already executed this in the sandbox environment, and it successfully installed dependencies for 6 portal CLIs).*

2. **Run the Setup Interview**:
   Start Claude Code and initiate the setup:
   ```bash
   claude
   /setup
   ```
   This will walk you through setting up your profile, documents, and preferences. Note: This setup will write your personal data into tracked files, so it is highly recommended to follow the advice in `SETUP.md` (Section 2) regarding using a private fork or committing locally without pushing.

3. **Search for Jobs**:
   Run the scrape command inside Claude Code:
   ```bash
   /scrape
   ```

4. **Apply to a Job**:
   Once you find a job, apply to it using its URL or text:
   ```bash
   /apply <job_url>
   ```

This is all you need to start using the framework. For more detailed instructions, fallback options, and advanced customizations (like setting up custom templates or salary data), refer to the full `SETUP.md` document in this repository.
