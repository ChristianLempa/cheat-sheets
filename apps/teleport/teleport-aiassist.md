# Teleport Assist

**'Teleport Assist'** is an artificial intelligence feature, that utilizes facts about your infrastructure to help answer questions, generate command line scripts, and help you perform routine tasks on target nodes. At the moment only SSH and bash are supported. Support for SQL, AWS API and Kubernetes is planned for the near future.

> **'Teleport Assist'** is currently experimental, available starting from Teleport v12.4 for Teleport Community Edition.

## Prerequisites

- You will need an active OpenAI account with GPT-4 API access as Teleport Assist relies on OpenAI services.
  
## Configuration

Copy the GPT-4 API key into the file `/etc/teleport/openai_key`, and set read-only permissions and change the file owner to the user that the Teleport Proxy Service uses by running the following commands:

```sh
chmod 400 /etc/teleport/openai_key
chown teleport:teleport /etc/teleport/openai_key
```

To enable Teleport Assist, you need to provide your OpenAI API key. On each Proxy and Auth Service host, perform the following actions.

If the host is running the Auth Service, add the following section:

```yaml
auth_service:
  assist:
    openai:
      api_token_path: /etc/teleport/openai_key
```

If the host is running the Proxy Service, add the following section:

```yaml
proxy_service:
  assist:
    openai:
      api_token_path: /etc/teleport/openai_key
```

Restart Teleport for the changes to take effect.

Make sure that your Teleport user has the `assistant` permission. By default, users with built-in `access` and `editor` roles have this permission. You can also add it to a custom role. Here is an example:

```yaml
kind: role
version: v6
metadata:
  name: assist
spec:
  allow:
    rules:
    - resources:
      - assistant
      verbs:
      - list
      - create
      - read
      - update
      - delete
```

## Usage

Now that you have Teleport Assist enabled, you can start using it, by click on the **'Assist'** button in the Teleport UI.
