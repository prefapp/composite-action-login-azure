# composite-action-login-azure

This repository stores a [composite action](https://github.blog/changelog/2021-08-25-github-actions-reduce-duplication-with-action-composition/) used to set up azure login in order to release a helm chart using helmfile.

You can use this composite action as a step in your workflow like:
```
- id: azure-login
        if: ${{ steps.set-cloud-info.outputs.result == 'azure' }}
        uses: prefapp/composite-action-login-azure@v1
        with:
          creds: ${{ env.AZURE_CREDENTIALS }}
          resource-group: ${{ env.AKS_RESOURCE_GROUP }}
          cluster-name: ${{ env.CLUSTER_NAME }}
          repository-name: ${{ env.IMAGE_REPOSITORY_NAME }}

# ${{ steps.azure-login.outputs.helmfile-creds }}
```