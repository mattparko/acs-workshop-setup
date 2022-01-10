## Set up a Red Hat Advanced Cluster Security demo/workshop

### Prereqs
1. Deploy the "Openshift 4 Advanced Cluster Security 3" catalog offering in RHPDS (under Multi-Product Demo)
2. Deploy an "AWS Blank Open Environment" in RHPDS (under Red Hat Open Environments)
3. Log in to your cluster (as an admin user) with `oc login`
4. Export the following environment variables (add your credentials and update region if desired)
    ```
    export AWS_ACCESS_KEY_ID=myaccesskeyid
    export AWS_SECRET_ACCESS_KEY=mysecretaccesskey
    export AWS_REGION=ap-southeast-2
    ```
5. Install Ansible dependencies on control node
   - Ansible 2.9
   - python3-boto
   - python3-boto3
   - python3-kubernetes
6. Install Ansible collections
   ```
   ansible-galaxy install -r requirements.yml
   ```
7. Ensure you have a public ssh key located at `~/.ssh/id_rsa.pub`

### Deploy
1. Execute `ansible-playbook site.yml`
2. Playbook will output required information
3. Be sure to add `ROX_API_TOKEN` to your environment variables (or store it for later)

### Notes
1. If you need to re-run this playbook multiple times, you can skip downloading the exploit server archive with `ansible-playbook site.yml --skip-tags="download_jndi"`
