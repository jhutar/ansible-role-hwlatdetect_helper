# ansible-role-hwlatdetect_helper

**Install and run hwlatdetect test.**


## Installation

To install the role, create `requirements.yaml` with this content:

    - name: hwlatdetect_helper
      src: https://github.com/jhutar/ansible-role-hwlatdetect_helper.git
      version: origin/main

and then to install the role:

    ansible-galaxy install -r requirements.yaml --roles-path roles/

Now the role is available in `roles/hwlatdetect_helper/`.

Check `hwlatdetect_example.yaml` for example on how to use the role in the playbook.


## Configuration

* `hwlatdetect_helper_store_local_logs_dir` is an ansible controller local
  directory to fetch raw hwlatdetect output to. If empty, no logs are fetched.
* `hwlatdetect_helper_test_duration` is a timeout after which hwlatdetect
  will stop even if you do not use `tierdown.yaml`. It is used for tools
  `--duration` option.
* `hwlatdetect_helper_test_threshold` maps to `--threshold` option
* `hwlatdetect_helper_test_window` maps to `--window` option
* `hwlatdetect_helper_test_width` maps to `--width` option


### Default variables

```
# By default, do not collect logs
hwlatdetect_helper_store_local_logs_dir: ''

# Maximum time for hwlatdetect to run in a form accepted by the tool
# (your workload need to finish before that)
hwlatdetect_helper_test_duration: 1d

# Other variables directly papped to tool's options
hwlatdetect_helper_test_threshold: 10us
hwlatdetect_helper_test_window: 1000000us
hwlatdetect_helper_test_width: 950000us
```


## References

1. Basic info about the tool: https://github.com/jlelli/rt-tests/blob/master/src/hwlatdetect/hwlat.txt
2. Related kernel inteface: https://www.kernel.org/doc/html/latest/trace/hwlat_detector.html
