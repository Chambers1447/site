### Listing pools

```
zpool list
zfs list
```

### Listing snapshots

```
zfs list -t snapshot
```

### Showing status of scrubs

```
zpool status
```

### Read smart status

```
smartctl -H /dev/sd*
```

### Read all smart information

```
smartctl -a /dev/sd*
```

### Look for:

```
* Short self-test routine
* recommended polling time:
```

```
* Extended self-test routine
* recommended polling time:
```

```
* Conveyance self-test routine
* recommended polling time:
```

```
* SMART Self-test log structure revision number 1
```

---

[Scrubbing](https://www.ixsystems.com/community/threads/scrub-and-smart-testing-schedules.20108/)
