Gnip-Python-PowerTrack-Rules
============================

Gnip PowerTrack rules management library and utilities.

Edit the sample_config.cfg file with your credentials and your favorite stream rule management
url. Copy or move to .gnip.

Utilities will check the local directory for .gnip. If you want to use a different location
try:

export GNIP_CONFIG_FILE=... in your environment.


EXAMPLES:
=========

$ ./list_rules.py -h
Usage: list_rules.py [options]

Options:
  -h, --help            show this help message and exit
  -u URL, --url=URL     Input url
  -p, --pretty-print    Prettier printing of output.
  -m PATTERN, --match-pattern=PATTERN
                        List only rules matching pattern (Python REs)
  -t MATCHTAG, --match-tag=MATCHTAG
                        List only rules with tags matching pattern (Python
                        REs)

> ./list_rules.py 
{"rules": [{"tag": "musician", "value": "bieber"}, {"tag": "musician", "value": "gaga "}, {"tag": "candidate", "value": "obama"}, {"tag": "candidate", "value": "romney "}, {"tag": null, "value": "dog"}, {"tag": null, "value": "cat -mouse -mice -rat"}]}


$ ./list_rules.py -p
{
   "rules": [
      {
         "tag": null, 
         "value": "obama"
      }, 
      {
         "tag": null, 
         "value": "romney"
      }, 
      {
         "tag": "musician", 
         "value": "bieber"
      }, 
      {
         "tag": "musician", 
         "value": "gaga "
      }, 
      {
         "tag": null, 
         "value": "dog"
      }, 
      {
         "tag": null, 
         "value": "cat -mouse -mice -rat"
      }
   ]
}

$ ./delete_rules.py -h
Usage: delete_rules.py [options]

Options:
  -h, --help            show this help message and exit
  -u URL, --url=URL     Input url
  -m PATTERN, --match-rule=PATTERN
                        List only rules matching pattern (Python REs)
  -t MATCHTAG, --match-tag=MATCHTAG
                        List only rules with tags matching pattern (Python
                        REs)
  -d, --delete          Set this flag to delete, without -d, prospective
                        changes are shown but not executed.


$ ./delete_rules.py 
=== Proposed rule deletions shown but not executed ===
{"rules": [{"tag": null, "value": "obama"}, {"tag": null, "value": "romney"}, {"tag": "musician", "value": "bieber"}, {"tag": "musician", "value": "gaga "}, {"tag": null, "value": "dog"}, {"tag": null, "value": "cat -mouse -mice -rat"}]}

> ./create_rules.py -h
Usage: create_rules.py [options]

Options:
  -h, --help          show this help message and exit
  -u URL, --url=URL   Input url
  -j, --json          Interpret input stream is JSON rules
  -d, --delete-rules  Delete existing rules before creating new.

> cat powertrack.rules | ./create_rules.py 
OK - 6 rules created

> cat powertrack.json | ./create_rules.py -dj
OK - 6 rules created

==
Gnip-Python-PowerTrack-Rule by Scott Hendrickson see LICENSE.txt for details.