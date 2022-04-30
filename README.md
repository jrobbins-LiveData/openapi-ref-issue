# prefcards_api

auto-generate PREFcards API from `livedata-openapi.yaml` (OpenAPI 3.0.1 Schema) via https://github.com/openapi-generators/openapi-python-client

## new version from PREFcards or rebuild

```cmd
.venv\scripts\activate
rd /q /s prefcards-api-client
python materialize_parameters.py
generate.cmd
 ```
## NOTE

fix prefcards-api-client\prefcards_api_client\client.py

change:

```python
        return {"Authorization": f"Bearer {self.token}", **self.headers}
```
to:

```python
        return {"Auth": f"{self.token}", **self.headers}
```

Update `prefcards_api_client/pyproject.toml` version to track .yaml version


```cmd
cd prefcards-api-client
poetry shell
poetry update
poetry install
poetry build
poetry publish -r ld

git push
 ```
