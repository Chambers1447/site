# ZFS

## Listing pools
```sh
zpool list
zfs list
```

## Listing snapshots
```sh
zfs list -t snapshot
```

## Showing status of scrubs
```sh
zpool status
```

## Read smart status
```sh
smartctl -H /dev/sd*
```

## Read all smart information
```sh
smartctl -a /dev/sd*
```

## Look for:
```sh
* Short self-test routine
* recommended polling time:
```

```sh
* Extended self-test routine
* recommended polling time:
```

```sh
* Conveyance self-test routine
* recommended polling time:
```

```sh
* SMART Self-test log structure revision number 1
```

[Scrubbing](https://www.ixsystems.com/community/threads/scrub-and-smart-testing-schedules.20108/)
