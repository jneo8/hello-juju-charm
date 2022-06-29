# Implement functional test with zaza

## Requirement 

* juju
* lxd

## QA

### Why are OS functional tests in separate repository?

## Build charm with openstack template

### Add require files

Templates: https://github.com/openstack-charmers/release-tools/tree/master/global

**tox.ini**

```bash
wget https://raw.githubusercontent.com/openstack-charmers/release-tools/master/global/classic-zaza/tox.ini .

cat tox.ini
```

Add **pip.sh** **build-requirements.txt** **rename.sh**

```bash
wget https://raw.githubusercontent.com/openstack-charmers/release-tools/master/global/classic-zaza/pip.sh .

wget https://raw.githubusercontent.com/openstack-charmers/release-tools/master/global/classic-zaza/build-requirements.txt .

wget https://raw.githubusercontent.com/openstack-charmers/release-tools/master/global/classic-zaza/rename.sh .

chmod u+x rename.sh
chmod u+x pip.sh
```

**./requirements.txt**

Resolved dependency issue, update requirements.txt.

```
ops >= 1.4.0
ops-lib-pgsql==1.4
GitPython==3.1.14
markupsafe==2.0.1
Jinja2==2.10.1
```

**./osci.yaml**


```yaml
- project:
    vars:
      needs_charm_build: true
      charm_build_name: hello-juju
      build_type: charmcraft
```


Finally, build charm with tox

```bash
tox -e build
```
