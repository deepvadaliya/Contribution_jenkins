## Imporove the disk usage
- sudo fallocate -l 7G /tmp/disk_fill_test

=> Once alarm triggers and email arrives
- sudo rm /tmp/disk_fill_test
- sudo sync

