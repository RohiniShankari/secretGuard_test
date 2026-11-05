# SecretGuard Test Repository

A tiny repository containing deliberately synthetic credential-shaped strings for testing a local secret scanner.

## Important
- All values in this repository are fake test data.
- Do not replace them with real credentials.
- This project is intentionally small and contains no executable build requirements.

## Expected detections

Your current SecretGuard rules should find:
1. An AWS access-key-shaped value in `config/aws.properties`.
2. A GitHub-token-shaped value in `config/github.properties`.

The placeholder examples in `config/example.properties` should not match your current regex rules.

## How to test

1. Create a new **public test repository** on GitHub.
2. Upload the contents of this folder (not the ZIP file itself).
3. Copy the repository URL, for example `https://github.com/YOUR-USERNAME/secretguard-test-project`.
4. Send it to `POST http://localhost:8080/api/github-scan` as:
   ```json
   {
     "repositoryUrl": "https://github.com/YOUR-USERNAME/secretguard-test-project"
   }
   ```

Expected: at least two findings, one `AWS_ACCESS_KEY` and one `GITHUB_TOKEN`.
