# Tekton Pipeline using Snyk task

## Steps

1. Install OpenShift Pipelines operator
1. Git clone repo

    ```bash
    git clone https://github.com/odrodrig/nodejs-goof.git
    cd nodejs-goof/pipeline
    ```

1. Create a new OpenShift Project

    ```bash
    oc new-project goof
    ```

1. Install the Tekton tasks

    1. Install git-clone task

        ```bash
        oc apply -f https://raw.githubusercontent.com/tektoncd/catalog/v1beta1/git/git-clone.yaml
        ```

    1. Install snyk-node task

        ```bash
        oc apply -f https://raw.githubusercontent.com/garethr/snyk-tekton/master/node/node.yaml
        ```
    
1. Get an API key from Snyk
    - This is where I got mine:

    ![snyk token](../images/snykToken.png)

1. Run the following command, replacing `abcd1234` with the token you got from Snyk

    ```bash
    oc create secret generic snyk --from-literal=token=abcd1234
    ```

1. Apply the pipeline

    ```bash
    oc apply -f pipeline.yaml
    ```

1. Create a PVC for pipeline to use

    ```bash
    oc apply -f snyk-pvc.yaml
    ```

1. Run the Pipeline

    ```bash
    oc create -f pipeline-run.yaml
    ```

1. Navigate to your openshift cluster console and find the Pipelines section on the left navigation menu, and select Pipelines.
1. From the Pipelines page select the tab that says Pipeline Runs.

    ![pipeline page](../images/pipelinePage.png)

1. You will then be able to see the status of the build process using the pipeline.
    - There are 2 steps:
        - clone the code and store it in the PVC that was created
        - scan the code with Snyk

1. If you view the output of the `code-analysis` step you can see the output of the Snyk scan.

    ![scan results](../images/scanResults.png)
