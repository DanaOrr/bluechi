<!-- markdownlint-disable-file MD041 -->
# D-Bus API bindings

Hirte provides for its public API
[introspection data](https://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format) in the
[data directory](https://github.com/containers/hirte/tree/main/data). These XML files can be used as input to code
generation tools to create clients for using the described D-Bus API in various programming languages.
For example:

- `C`: [gdbus-codegen](https://developer-old.gnome.org/gio/stable/gdbus-codegen.html)
- `Go`: [dbus-codegen-go](https://github.com/amenzhinsky/dbus-codegen-go)
- `Rust`: [dbus-codegen-rust](https://crates.io/crates/dbus-codegen)
- and many more

## pyhirte

For `python`, the dynamically generated proxies (e.g. from [dasbus](https://github.com/rhinstaller/dasbus)) don't
require such a generation and work well on their own. These proxies, however, don't provide type hints. Because of that
the hirte project provides `pyhirte` - auto-generated, typed python bindings.

### Installation

Install `pyhirte` via:

```bash
# from rpm package
dnf install python3-pyhirte

# or from PyPI
pip install pyhirte
```

### Usage

The following code snippets showcase how `pyhirte` can be used:

```python
# starting a systemd unit
--8<-- "pyhirte-examples/StartUnit:5"

# and stopping it again
--8<-- "pyhirte-examples/StopUnit:7"
```

```python
# enabling a systemd unit to be executed on startup
--8<-- "pyhirte-examples/EnableUnit:5"

# and disabling it again
--8<-- "pyhirte-examples/DisableUnit:7"
```

```python
# listing all nodes
--8<-- "pyhirte-examples/ListAllNodes:5"
```

```python
# listing all units on all nodes
--8<-- "pyhirte-examples/ListNodeUnits:5"


# or easily filter them and only display active services
--8<-- "pyhirte-examples/ListActiveServices:5"
```

```python
# getting properties from systemd units
# e.g. the CPUWeight
--8<-- "pyhirte-examples/CPUWeight:5"

# and setting values for them
--8<-- "pyhirte-examples/SetCPUWeight:5"
```