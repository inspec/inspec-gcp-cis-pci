# InSpec GCP CIS PCI Helper Resource Pack

Resource pack containing helper functions for profiles using https://github.com/GoogleCloudPlatform/inspec-gcp-cis-benchmark. 

## Sample usage

### Create a profile 

For example, using InSpec e.g.

```
inspec init profile myprofile --platform gcp
```

### Update the inspec.yml file

This should be updated to point here instead of directly to the InSpec GCP resource pack:

```
depends:
- name: inspec-gcp-cis-pci
  url: https://github.com/inspec/inspec-gcp-cis-pci/archive/master.tar.gz
```

### Use the helper functions

Now we could edit the controls to include lines such as:

```
gcp_project_id = attribute('gcp_project_id')
helper = gcp_helpers(project: gcp_project_id)
p helper.get_all_gcp_locations
p helper.collect_gke_clusters_by_location(['europe-west2'])
p helper.get_gce_instances(['europe-west2-a'])
```

and directly use these methods in downstream profiles. 

### Other notes

This approach and much of the code in the helper resource originated because of the PR here: https://github.com/inspec/inspec-gcp/pull/245/files and the issue of helper modules with InSpec discussed https://github.com/inspec/inspec/issues/4948.  
