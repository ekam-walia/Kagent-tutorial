# Installing kagent 

Set the Gemini API key as an environment variable.

```bash
export GEMINI_API_KEY="your-api-key-here"
```

Download the kagent CLI. By default, the latest version 0.10.2 of kagent is installed.

```bash
brew install kagent
```

For default agents use this command

```bash
kagent install --profile demo
```

Create a Secret for Gemini First 

```bash
kubectl create secret generic gemini-api-key \
  -n kagent \
  --from-literal=GOOGLE_API_KEY="$GEMINI_API_KEY"
```

Configure Gemini as the model provider 

```yaml
apiVersion: kagent.dev/v1alpha2
kind: ModelConfig
metadata:
  name: gemini
  namespace: kagent
spec:
  provider: Gemini
  model: gemini-3.5-flash
  apiKeySecret: gemini-api-key
  apiKeySecretKey: GOOGLE_API_KEY
  gemini: {}
```
```bash
kubectl apply -f gemini-modelconfig.yaml
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
