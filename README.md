# tag-version-action

## overview:

action meant to help with changing a tag in a remote gitops repo

e.g. in case ones gitops is a helm styled argocd - and you just want to change the image tag in "values"

## usage:
```yaml
    steps:
      - uses: actions/checkout@v3

      - name: build and pushsomething
        run: |
        ...

      - name: use our private action
        uses: daniel-habib/tag-version-action@main
        with: 
          the_version: ${{ github.sha }}
          file: envs/dev/namespace/test-app1.yaml
          commit_name: someone
          commit_email: someone@someplace.co
          commit_message: set test-app1.yaml tag to ${{ github.sha }}
          target_branch: main
          remote_repository: https://github.com/daniel-habib/test-gitops
          token: ${{ secrets.TOKEN }}
```

## credits

heavily inspired by https://github.com/GuillaumeFalourd/git-commit-push