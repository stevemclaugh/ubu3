### [Setup guide](Setup.md) | [Sample torrent file](https://github.com/stevemclaugh/preservation-torrent/blob/master/DataRefuge_001_test.torrent?raw=true)

# Guidelines for torrent-based preservation


### Each torrent should contain a bundle of datasets, totaling 10–20 gigabytes per torrent.

- Very few participants will bother to seed hundreds of small, separate torrents. Many have storage and bandwidth to spare, but screen space is limited and managing long lists of files is tedious.

- Issuing bundles (rather than creating one torrent per dataset) decreases the odds that less in-demand items will slip through the cracks and no longer be seeded.

- The point of bundling is that these torrents are aimed at preservation, not everyday use. If someone has limited disk space, it is still possible to download individual files from within a torrent.


### Torrents should be issued in a numbered series, with periodic additions to include the latest datasets.

```
📄 Ubu_001.torrent
📄 Ubu_002.torrent
📄 Ubu_003.torrent
📄 Ubu_004.torrent
📄 Ubu_005.torrent
📄 ...
```


### Each torrent points to a single directory containing several (perhaps several dozen or several hundred) datasets and their metadata.

```
📂 Ubu_001/
    📄 _checksums.md5
    📄 dataset-uuid-123.zip
    📄 dataset-uuid-123.json
    📄 dataset-uuid-xyz.zip
    📄 dataset-uuid-xyz.json
    📄 ...
    📄 README.txt

📂 Ubu_002/
    📄 _checksums.md5
    📄 dataset-uuid-456.zip
    📄 dataset-uuid-456.json
    📄 dataset-uuid-abc.zip
    📄 dataset-uuid-abc.json
    📄 ...
    📄 README.txt

📂 Ubu_003/
    📄 ...

📂 Ubu_004/
    📄 ...

📂 Ubu_005/
    📄 ...
```



### The fewer files in a torrent, the better.

- Each torrent should contain no more than 400–500 individual files. If a single torrent points to too many files, participants' clients may lag or crash.


### Items need not be bundled thematically.

- Because you can't add files to an existing torrent, thematically organized collections become unmanageable over time. Instead, assign datasets to torrent bundles in roughly chronological order.


### Metadata for all datasets, along with checksums, torrent files, and magnet links, should be available from a trusted source.

- It should be possible to download all metadata in a single package, whether through an API or from a periodically updated static file.


### It isn't necessary to include extensive metadata in each torrent.

- Using UUIDs instead of human-readable filenames is a light form of obfuscation.

- The complete metadata collection will be a fairly small document, so it may be less of a preservation risk than the 


### If a dataset must be retracted/updated, the trusted organization can post a replacement torrent.

- Assiduous collectors will occasionally check their files against the master checksum list and download updated torrents as needed.

- The swarm of seeders for a discarded torrent will die out over time.

- Reissuing a torrent should be reserved for exceptional cases.


## Benefits of torrent-based preservation

- Individuals can participate in the preservation effort without the expertise or disk space required to run a full mirror. Downloading and seeding just one or two torrents is a real contribution.

- By issuing a series of sequentially numbered bundles, the goal is to stir a desire for completeness in the brains of collectors. Distributing the collection in dozens of torrents instead of hundreds will make bulk copying more manageable.

- With a trusted organization issuing torrent files and metadata, the system is centralized enough to keep people on the same page. If that organization ceases to operate, collaboration among collectors may allow the data to continue circulating in a coherent form.

&nbsp;

#### [*>> Setup guide: Creating and seeding a torrent on a VPS*](Running_Transmission_on_a_VPS.md)

&nbsp;

## *Further reading*

Cabanac, Guillaume. “Bibliogifts in LibGen? Study of a Text-Sharing Platform Driven by Biblioleaks and Crowdsourcing.” *Journal of the Association for Information Science and Technology*, March 27, 2015. doi:10.1002/asi.23445. [ftp://ftp.irit.fr/IRIT/SIG/2015_JASIST_C.pdf](ftp://ftp.irit.fr/IRIT/SIG/2015_JASIST_C.pdf).

Martin, John. “Piracy, Public Access, and Preservation: An Exploration of Sustainable Accessibility in a Public Torrent Index.” ASIS&T Annual Meeting, 2016. [https://osf.io/preprints/socarxiv/hzp6r/download?format=pdf](https://osf.io/preprints/socarxiv/hzp6r/download?format=pdf).

Tenen, Dennis, and Maxwell Foxman. “Book Piracy as Peer Preservation.” *Computational Culture*, November 9, 2014. [http://computationalculture.net/article/book-piracy-as-peer-preservation](http://computationalculture.net/article/book-piracy-as-peer-preservation).



&nbsp;

<p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
</p>
