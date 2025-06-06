# InSpec GCP Helper Resource Pack

Resource pack containing helper functions and classes for Inspec-gcp profiles.

## Required Disclaimer

This is not an officially supported Google product. This code is intended to help users assess their security posture on the Google Cloud against the CIS Benchmark. This code is not certified by CIS.

### Create a profile 

For example, using InSpec

```sh
inspec init profile myprofile --platform gcp
```

### Update the inspec.yml file

This should be updated to point here instead of directly to the InSpec GCP resource pack:

```yaml
depends:
- name: inspec-gcp-helpers
  url: https://github.com/lxndrblz/inspec-gcp-helpers/archive/master.tar.gz
```

### Use the helper functions

Now we can edit the controls to include lines such as:

```rb
gcp_project_id = attribute('gcp_project_id')

gke_cache = GKECache(project: gcp_project_id, gke_locations: ['us-central1-a'])
p gke_cache.gke_clusters_cache

gce_cache = GCECache(project: gcp_project_id, gce_zones: ['us-central1-a'])
p gce_cache.gce_instances_cache
```

and directly use these methods in downstream profiles. 