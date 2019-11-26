# DipperCache

A cache for publicly availalabile files ingested by the  
Monarch Initatiaves's Data Ingest Pipeline (Dipper).

Provides a number of benifits
  - A single location we control from which ingests to fetch files
  	- so missing http header timestamps are on us
  	- sources which we can't tell if they are updated save by comparison can be processed more carefully and made to only appear updated when they actualy are.

  - Monarch only polls the various locations once per interval (day|week)
    - Many ingests may	pull from the cache w/o being a load on source.

  - Different ingests may pull a shared  file (they do not now)
  
  - Files that require renaming to avoid conflicts can be handled here.

  - Files that benifit from preprocessing can be served preprocessed. 


Keeping the cache web fetch oriented allows the existing scripts to 
function as they are and migrate to using the cache  at will.

Development can mix and match source & cache as needed

We may be able to change almost nothing and transparently fetch files from the cache if they are avalable.

We can better test when we know the files we are testing __are__ the files that will go to production.

We can take snapshots of the subset of public files we fetch.

## Implementation 

It is a Gnu Makefile.  

That it for now, we could consider making a 'bin/' dir for scripts or something but so far haven't felt the need.

 