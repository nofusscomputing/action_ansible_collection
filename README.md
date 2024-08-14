## No Fuss Computing - GH Action / Workflow for Ansible Collections

using the workflow requires a file be created at path `.github/workflow/ci.yaml`

``` yaml

---
name: 'CI'


on:
  push:


jobs:

  collection:
    name: 'Ansible Collection'
    uses: nofusscomputing/action_ansible_collection/.github/workflows/reusable_ansible_collection.yaml@development
    inputs:
      ANSIBLE_COLLECTION_MARK_RELEASE_LIVE: true
      ANSIBLE_GALAXY_NAMESPACE: "${{ github.repository_owner }}"
      ANSIBLE_GALAXY_PACKAGE_NAME: "${{ github.event.repository.name }}"
      ANSIBLE_LINTING_MUST_PASS: true
    secrets:
      ANSIBLE_GALAXY_UPLOAD_TOKEN: ${{ secrets.ANSIBLE_GALAXY_UPLOAD_TOKEN }}

```
