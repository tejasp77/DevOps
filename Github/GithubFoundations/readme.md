# Version control
- VCS is set of program or set of programs that track changes to collection of files.
- VCS is software configuration management (SCM) system.
- Git is fast, highly scalable, free, open source VCS. Primary author is Linux Torvalds, the creator of Linux.
- Example of VCS includes Subversion (SVN), Perforce used centralized server to store project's history. This centralization means that one server was potentially single point of failure.

# Distributed Version Control
-  Git is _distributed_, which means project's complete history is stored both on client and on the server.
-  It allows to edit files without a network connection, check them in locally, and sync with the server when a connection becomes available. If a server goes down, you still have a local copy of the project. 

# Git Terminology
- Working tree
- Repo
- Hash - 160 bits long
- Object
  - Blob - contains ordinary file
  - Tree - represents directory
  - Commit - represents specific version of working tree
  - Tag - name attached to a commit
- Commit - to make commit objects
- Branch -  series of linked commits
- Remote - a named reference to another git repository. Git creates remote name origin that is default remote for push or pull operation
