<p align="center">
  <img src="https://avatars.githubusercontent.com/u/43526139?s=400&u=4355b45dd52b19a45a83f86b7f90ef5ad6ecc2cb&v=4" />  
<p align="center">


## Create a Khulnasoft Branch 🚀
This GitHub action creates a new Khulnasoft branch.

Here is an example of how to use it:

```yml
name: Create Khulnasoft Branch with GitHub Actions Demo
run-name: Create a Khulnasoft Branch 🚀
jobs:
  Create-Khulnasoft-Branch:
    uses: khulnasoft/create-branch-action@v5
    with:
      project_id: rapid-haze-373089
      # optional (defaults to your primary branch)
      parent: dev
      # optional (defaults to neondb)
      database: my-database
      branch_name: from_action_reusable
      username: db_user_for_url
      api_key: ${{ secrets.KHULNASOFT_API_KEY }}
    id: create-branch
  - run: echo db_url ${{ steps.create-branch.outputs.db_url }}
  - run: echo host ${{ steps.create-branch.outputs.host }}
  - run: echo branch_id ${{ steps.create-branch.outputs.branch_id }}
```

The full list of supported parameters can be seen in the [_action.yml_](/action.yml) file.

## Outputs
```yml
outputs:
  db_url:
    description: 'New branch DATABASE_URL'
    value: ${{ steps.create-branch.outputs.db_url }}
  db_url_with_pooler:
    description: 'New branch DATABASE_URL with pooling enabled'
    value: ${{ steps.create-branch.outputs.db_url_with_pooler }}
  host:
    description: 'New branch host'
    value: ${{ steps.create-branch.outputs.host }}
  host_with_pooler:
    description: 'New branch host with pooling enabled'
    value: ${{ steps.create-branch.outputs.host_with_pooler }}
  branch_id:
    description: 'New branch id'
    value: ${{ steps.create-branch.outputs.branch_id }}
  password:
    description: 'Password for connecting to the new branch database with the input username'
    value: ${{ steps.create-branch.outputs.password }}
```

## How to set up the KHULNASOFT_API_KEY
Navigate to you the Account page on your Khulnasoft console. In the Developer Settings, Generate a new API key if you don't have one already. 
It's important not to share the API key or expose it in your actions or code. This is why you need to add the API key to a new GitHub secret.  

In your GitHub repo, go to `Settings` and locate `Secrets` at the bottom of the left sidebar. Click on `Actions` and then on the `New repository secret` button to create a new secret.
Name the secret `KHULNASOFT_API_KEY` and paste the API key generated on the Khulnasoft console in the `Secret*` field, then press `Add secret` button.
