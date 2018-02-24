# Goals
Scan a directory for changes and identify files of interest for further processing.

Further processing includes:
- moving/copying while ignoring unwanted files
- renaming
- keeping track of processed files both in source and destination in order to:
    - preserve a history of already procssed files to avoid redoing work
    - providing an interface to processed files in case they should be renamed again

Design:
- flexibility
- safety
- log to stdout
- configurable through environment

# Out of scope:
Monitoring with e.g. inotify, instead provide a trigger to delegate that to other tools.

# Unclear

- Pre-/Post-Hooks for e.g. unpacking?
- Umask -> cross platform?
- ? Let directory stabilze

# Rough Process

1. Scan source, save entries
    - Name
    - Size
    - Last Modified
    - ? more
2. Compare with last scan to identify new stuff
3. Process
    - Where ?
    - Identify type
        - Static
        - Through 'hints' (SXXEXX, must be tv)
    - Do type specific processing
4. Save result
    - Source name + file tree
    - Destination

# Dependencies

- https://github.com/go-chi/chi
- https://github.com/kelseyhightower/envconfig
- https://github.com/coreos/bbolt