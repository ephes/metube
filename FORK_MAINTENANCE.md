# Maintained deployment source

This fork retains upstream `alexta69/metube` at
`f02f2ac0252563df13286cd1643fac9ca1bc08d9`. The application and frontend are
unchanged. Its deployment branch corrects only the locked certifi release from
2026.7.22 to 2026.10.19, using the published PyPI source/wheel URLs and hashes.
This retains the trust repair already installed in the native service and
prevents a frozen dependency sync from reverting it.

Native deployments pin the immutable reviewed fork commit. The selected Python,
Node.js and uv versions remain operator deployment inputs. Sync upstream
separately after reviewing application changes; retain this narrow lock correction
until upstream's lock meets the deployment trust floor. Do not refresh unrelated
packages as part of that correction.

Validate with `uv lock --check` and a clean `uv sync --frozen --no-dev`, then
verify the installed certifi version and CA bundle through the deployment trust
check. Compare package identities against the upstream lock: only certifi may
differ. The normal frontend/backend checks remain those in `CONTRIBUTING.md`.
