# Gitlab

## Gitlab Runner

If you want to add a GitLab runner, go to your Runner Configuration (/admin/runners) in Gitlab and replace the registration inside the [script](./gitlab-runner-register.sh)

Execute the script:

```sh
# Maybe you missed the right to execute it
chmod +x gitlab-runner-register.sh
# Run script
./gitlab-runner-register.sh
```
