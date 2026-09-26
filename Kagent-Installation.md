# Installing kagent 

Set the Gemini API key as an environment variable.

```bash
export GEMINI_API_KEY="your-api-key-here"
```

Download the kagent CRDs. By default, the latest version 0.10.2 of kagent is installed.

```bash
helm install kagent-crds \
  oci://ghcr.io/kagent-dev/kagent/helm/kagent-crds \
  --version 0.10.2 \
  --namespace kagent \
  --create-namespace \
  --wait
```

Install Kagent with Gemini 3.5 Flash

```bash
helm install kagent \
  oci://ghcr.io/kagent-dev/kagent/helm/kagent \
  --version 0.10.2 \
  --namespace kagent \
  --wait \
  --set providers.default=gemini \
  --set providers.gemini.apiKey="$GEMINI_API_KEY" \
  --set providers.gemini.model="gemini-3.5-flash"
```

Accessing the kagent dashboard (UI) 
To open the kagent dashboard, run the dashboard command from the CLI. The CLI sets up the port-forward to the UI service running inside the cluster and opens the dashboard.

```bash
kagent dashboard
```

```text
kagent dashboard is available at http://localhost:8082
Press Enter to stop the port-forward...
```
