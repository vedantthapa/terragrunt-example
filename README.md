# terragrunt-example
Example to demo terragrunt plan output discrepancy when [migratinng from root `terragrunt.hcl`.](https://terragrunt.gruntwork.io/docs/migrate/migrating-from-root-terragrunt-hcl/)

## Setup
Assuming all necessary tools are installed, run the following command to generate a plan -

```sh
terragrunt plan --log-level=debug --summary-disable --all -lock=false -out=tfplan
```
This creates a plan file called `tfplan` in the root of the repo.

<details>

<summary>Click to expand log for the above command</summary>

```sh
> terragrunt plan --log-level=debug --summary-disable --all -lock=false -out=tfplan
18:47:44.295 DEBUG  Terragrunt Version: 0.89.3
18:47:44.295 DEBUG  Running command: terraform -version
18:47:44.295 DEBUG  Engine is not enabled, running command directly in .
18:47:44.355 DEBUG  terraform version: 1.13.3
18:47:44.355 DEBUG  Auto provider cache dir setup failed: auto provider cache dir requires OpenTofu, but detected terraform
18:47:44.355 DEBUG  Searching for stack files in .
18:47:44.356 INFO   Using runner pool for stack .
18:47:44.359 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.359 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.359 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.360 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.360 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.360 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.361 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:47:44.361 DEBUG  [bar] Setting download directory for unit ./bar to ./bar/.terragrunt-cache
18:47:44.361 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:47:44.362 DEBUG  [foo] Setting download directory for unit ./foo to ./foo/.terragrunt-cache
18:47:44.362 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.362 DEBUG  Setting download directory for unit . to ./.terragrunt-cache
18:47:44.363 DEBUG  Stack at ../debug-tg:
  => Unit . (excluded: false, assume applied: false, dependencies: [])
  => Unit ./bar (excluded: false, assume applied: false, dependencies: [])
  => Unit ./foo (excluded: false, assume applied: false, dependencies: [])
18:47:44.363 INFO   The runner-pool runner at . will be processed in the following order for command plan:
- Unit .
- Unit ./bar
- Unit ./foo

18:47:44.363 DEBUG  Runner Pool Controller: starting with 3 tasks, concurrency 2147483647
18:47:44.363 DEBUG  Runner Pool Controller: found 3 readyEntries tasks
18:47:44.363 DEBUG  Runner Pool Controller: running .
18:47:44.363 DEBUG  Runner Pool Controller: running ./bar
18:47:44.363 DEBUG  Runner Pool Controller: running ./foo
18:47:44.363 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
18:47:44.363 DEBUG  Running .
18:47:44.363 DEBUG  [bar] Running ./bar
18:47:44.363 DEBUG  [foo] Running ./foo
18:47:44.364 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.364 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:47:44.364 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:47:44.364 DEBUG  using cache key for version files: r01AJjVD7VSXCQk1ORuh_no_NRY
18:47:44.364 DEBUG  [bar] using cache key for version files: r01AJjVD7VSXCQk1ORuh_no_NRY
18:47:44.364 DEBUG  Running command: terraform -version
18:47:44.364 DEBUG  [bar] Running command: terraform -version
18:47:44.364 DEBUG  [bar] Engine is not enabled, running command directly in ./bar
18:47:44.364 DEBUG  Engine is not enabled, running command directly in .
18:47:44.364 DEBUG  [foo] using cache key for version files: r01AJjVD7VSXCQk1ORuh_no_NRY
18:47:44.365 DEBUG  [foo] Running command: terraform -version
18:47:44.365 DEBUG  [foo] Engine is not enabled, running command directly in ./foo
18:47:44.416 DEBUG  [bar] terraform version: 1.13.3
18:47:44.416 DEBUG  [foo] terraform version: 1.13.3
18:47:44.416 DEBUG  [foo] Reading Terragrunt config file at ./foo/terragrunt.hcl
18:47:44.416 DEBUG  [bar] Reading Terragrunt config file at ./bar/terragrunt.hcl
18:47:44.416 DEBUG  terraform version: 1.13.3
18:47:44.417 DEBUG  Reading Terragrunt config file at ./terragrunt.hcl
18:47:44.417 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:47:44.417 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:47:44.417 DEBUG  Did not find any locals block: skipping evaluation.
18:47:44.418 DEBUG  [bar] Running command: terraform plan -input=false -lock=false -out=tfplan
18:47:44.418 DEBUG  [bar] Engine is not enabled, running command directly in ./bar
18:47:44.418 DEBUG  [foo] Running command: terraform plan -input=false -lock=false -out=tfplan
18:47:44.418 DEBUG  [foo] Engine is not enabled, running command directly in ./foo
18:47:44.419 DEBUG  Running command: terraform init
18:47:44.419 DEBUG  Engine is not enabled, running command directly in .
18:47:44.467 INFO   terraform: Initializing the backend...
18:47:44.467 INFO   terraform: Initializing provider plugins...
18:47:44.467 INFO   terraform: Terraform has been successfully initialized!
18:47:44.467 INFO   terraform:
18:47:44.467 INFO   terraform: You may now begin working with Terraform. Try running "terraform plan" to see
18:47:44.467 INFO   terraform: any changes that are required for your infrastructure. All Terraform commands
18:47:44.467 INFO   terraform: should now work.
18:47:44.467 INFO   terraform: If you ever set or change modules or backend configuration for Terraform,
18:47:44.467 INFO   terraform: rerun this command to reinitialize your working directory. If you forget, other
18:47:44.467 INFO   terraform: commands will detect it and remind you to do so if necessary.
18:47:44.473 DEBUG  Running command: terraform plan -input=false -lock=false -out=tfplan
18:47:44.473 DEBUG  Engine is not enabled, running command directly in .
18:47:44.527 STDOUT terraform: No changes. Your infrastructure matches the configuration.
18:47:44.527 STDOUT terraform: Terraform has compared your real infrastructure against your configuration
18:47:44.527 STDOUT terraform: and found no differences, so no changes are needed.
18:47:44.531 DEBUG  Runner Pool Controller: . succeeded
18:47:44.531 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
18:47:44.617 STDOUT [foo] terraform: Terraform used the selected providers to generate the following execution
18:47:44.617 STDOUT [foo] terraform: plan. Resource actions are indicated with the following symbols:
18:47:44.617 STDOUT [foo] terraform:   + create
18:47:44.617 STDOUT [foo] terraform: Terraform will perform the following actions:
18:47:44.617 STDOUT [foo] terraform:   # null_resource.foo will be created
18:47:44.617 STDOUT [foo] terraform:   + resource "null_resource" "foo" {
18:47:44.617 STDOUT [foo] terraform:       + id = (known after apply)
18:47:44.617 STDOUT [foo] terraform:     }
18:47:44.617 STDOUT [foo] terraform: Plan: 1 to add, 0 to change, 0 to destroy.
18:47:44.617 STDOUT [foo] terraform:
18:47:44.617 STDOUT [foo] terraform: ─────────────────────────────────────────────────────────────────────────────
18:47:44.617 STDOUT [foo] terraform: Saved the plan to: tfplan
18:47:44.617 STDOUT [foo] terraform: To perform exactly these actions, run the following command to apply:
18:47:44.617 STDOUT [foo] terraform:     terraform apply "tfplan"
18:47:44.619 STDOUT [bar] terraform: Terraform used the selected providers to generate the following execution
18:47:44.619 STDOUT [bar] terraform: plan. Resource actions are indicated with the following symbols:
18:47:44.619 STDOUT [bar] terraform:   + create
18:47:44.619 STDOUT [bar] terraform: Terraform will perform the following actions:
18:47:44.619 STDOUT [bar] terraform:   # null_resource.bar will be created
18:47:44.619 STDOUT [bar] terraform:   + resource "null_resource" "bar" {
18:47:44.619 STDOUT [bar] terraform:       + id = (known after apply)
18:47:44.619 STDOUT [bar] terraform:     }
18:47:44.620 STDOUT [bar] terraform: Plan: 1 to add, 0 to change, 0 to destroy.
18:47:44.620 STDOUT [bar] terraform:
18:47:44.620 STDOUT [bar] terraform: ─────────────────────────────────────────────────────────────────────────────
18:47:44.620 STDOUT [bar] terraform: Saved the plan to: tfplan
18:47:44.620 STDOUT [bar] terraform: To perform exactly these actions, run the following command to apply:
18:47:44.620 STDOUT [bar] terraform:     terraform apply "tfplan"
18:47:44.622 DEBUG  Runner Pool Controller: ./foo succeeded
18:47:44.622 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
18:47:44.622 DEBUG  Runner Pool Controller: ./bar succeeded
18:47:44.622 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
```

</details>

Now, rename the `terragrunt.hcl` file to `root.hcl` as directed and run the previou command again with a different name for the plan file like so -

```sh
terragrunt plan --log-level=debug --summary-disable --all -lock=false -out=tfplan-root
```
This only outputs a plan in the respective `.terragrunt-cache` directory and **not** at the root of the repo.

<details>

<summary>Click to expand log for the above command</summary>

```sh
> terragrunt plan --log-level=debug --summary-disable --all -lock=false -out=tfplan-root
18:49:16.040 DEBUG  Terragrunt Version: 0.89.3
18:49:16.040 DEBUG  Running command: terraform -version
18:49:16.040 DEBUG  Engine is not enabled, running command directly in .
18:49:16.104 DEBUG  terraform version: 1.13.3
18:49:16.104 DEBUG  Auto provider cache dir setup failed: auto provider cache dir requires OpenTofu, but detected terraform
18:49:16.105 DEBUG  Searching for stack files in .
18:49:16.107 INFO   Using runner pool for stack .
18:49:16.108 DEBUG  Did not find any locals block: skipping evaluation.
18:49:16.108 DEBUG  Did not find any locals block: skipping evaluation.
18:49:16.109 DEBUG  Did not find any locals block: skipping evaluation.
18:49:16.109 DEBUG  Did not find any locals block: skipping evaluation.
18:49:16.110 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:49:16.110 DEBUG  [foo] Setting download directory for unit ./foo to ./foo/.terragrunt-cache
18:49:16.110 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:49:16.110 DEBUG  [bar] Setting download directory for unit ./bar to ./bar/.terragrunt-cache
18:49:16.111 DEBUG  Stack at ../debug-tg:
  => Unit ./bar (excluded: false, assume applied: false, dependencies: [])
  => Unit ./foo (excluded: false, assume applied: false, dependencies: [])
18:49:16.111 INFO   The runner-pool runner at . will be processed in the following order for command plan:
- Unit ./bar
- Unit ./foo

18:49:16.111 DEBUG  Runner Pool Controller: starting with 2 tasks, concurrency 2147483647
18:49:16.111 DEBUG  Runner Pool Controller: found 2 readyEntries tasks
18:49:16.111 DEBUG  Runner Pool Controller: running ./bar
18:49:16.111 DEBUG  Runner Pool Controller: running ./foo
18:49:16.111 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
18:49:16.111 DEBUG  [foo] Running ./foo
18:49:16.111 DEBUG  [bar] Running ./bar
18:49:16.111 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:49:16.111 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:49:16.111 DEBUG  [foo] using cache key for version files: r01AJjVD7VSXCQk1ORuh_no_NRY
18:49:16.112 DEBUG  [bar] using cache key for version files: r01AJjVD7VSXCQk1ORuh_no_NRY
18:49:16.112 DEBUG  [foo] Running command: terraform -version
18:49:16.112 DEBUG  [foo] Engine is not enabled, running command directly in ./foo
18:49:16.112 DEBUG  [bar] Running command: terraform -version
18:49:16.112 DEBUG  [bar] Engine is not enabled, running command directly in ./bar
18:49:16.168 DEBUG  [foo] terraform version: 1.13.3
18:49:16.169 DEBUG  [foo] Reading Terragrunt config file at ./foo/terragrunt.hcl
18:49:16.169 DEBUG  [bar] terraform version: 1.13.3
18:49:16.169 DEBUG  [bar] Reading Terragrunt config file at ./bar/terragrunt.hcl
18:49:16.169 DEBUG  [foo] Did not find any locals block: skipping evaluation.
18:49:16.169 DEBUG  [bar] Did not find any locals block: skipping evaluation.
18:49:16.170 DEBUG  [foo] Running command: terraform plan -input=false -lock=false -out=tfplan-root
18:49:16.170 DEBUG  [foo] Engine is not enabled, running command directly in ./foo
18:49:16.170 DEBUG  [bar] Running command: terraform plan -input=false -lock=false -out=tfplan-root
18:49:16.170 DEBUG  [bar] Engine is not enabled, running command directly in ./bar
18:49:16.358 STDOUT [foo] terraform: Terraform used the selected providers to generate the following execution
18:49:16.358 STDOUT [foo] terraform: plan. Resource actions are indicated with the following symbols:
18:49:16.358 STDOUT [foo] terraform:   + create
18:49:16.358 STDOUT [foo] terraform: Terraform will perform the following actions:
18:49:16.358 STDOUT [foo] terraform:   # null_resource.foo will be created
18:49:16.358 STDOUT [bar] terraform: Terraform used the selected providers to generate the following execution
18:49:16.359 STDOUT [bar] terraform: plan. Resource actions are indicated with the following symbols:
18:49:16.359 STDOUT [bar] terraform:   + create
18:49:16.358 STDOUT [foo] terraform:   + resource "null_resource" "foo" {
18:49:16.359 STDOUT [foo] terraform:       + id = (known after apply)
18:49:16.359 STDOUT [foo] terraform:     }
18:49:16.359 STDOUT [foo] terraform: Plan: 1 to add, 0 to change, 0 to destroy.
18:49:16.359 STDOUT [foo] terraform:
18:49:16.359 STDOUT [bar] terraform: Terraform will perform the following actions:
18:49:16.359 STDOUT [foo] terraform: ─────────────────────────────────────────────────────────────────────────────
18:49:16.359 STDOUT [bar] terraform:   # null_resource.bar will be created
18:49:16.359 STDOUT [bar] terraform:   + resource "null_resource" "bar" {
18:49:16.359 STDOUT [foo] terraform: Saved the plan to: tfplan-root
18:49:16.359 STDOUT [bar] terraform:       + id = (known after apply)
18:49:16.359 STDOUT [bar] terraform:     }
18:49:16.359 STDOUT [foo] terraform: To perform exactly these actions, run the following command to apply:
18:49:16.359 STDOUT [bar] terraform: Plan: 1 to add, 0 to change, 0 to destroy.
18:49:16.359 STDOUT [bar] terraform:
18:49:16.359 STDOUT [bar] terraform: ─────────────────────────────────────────────────────────────────────────────
18:49:16.360 STDOUT [bar] terraform: Saved the plan to: tfplan-root
18:49:16.360 STDOUT [bar] terraform: To perform exactly these actions, run the following command to apply:
18:49:16.360 STDOUT [bar] terraform:     terraform apply "tfplan-root"
18:49:16.359 STDOUT [foo] terraform:     terraform apply "tfplan-root"
18:49:16.363 DEBUG  Runner Pool Controller: ./foo succeeded
18:49:16.364 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
18:49:16.364 DEBUG  Runner Pool Controller: ./bar succeeded
18:49:16.364 DEBUG  Runner Pool Controller: found 0 readyEntries tasks
```
</details>

test-change
