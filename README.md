ODS-KSK-rollover-DLV
====================

KSK automatic rollover for OpenDNSSEC to publish in DLV registry

Little bash script to automatically sync the KSK rollover in DLV registry

* Change your NIC aka login name, Password, Path to save the DLV cookie, ods-signer script/program, CONF of ods-ksmutil
  save the variable to the .config file

* update your kasp.xml config file with 
  <Enforcer>
     [...]
     <RolloverNotification>P14D</RolloverNotification>  <!-- get notification 14D about the rollover --!>
     <DelegationSignerSubmitCommand>/PATH/TO/SCRIPT/opendnssec-updateDS</DelegationSignerSubmitCommand>
  </Enforcer>

* For each domain $D; (remplace $D with the domain name)
  include in DNS unsigned zonefile for $D the line

  $INCLUDE /Path/to/save/the/DLV/cookie/dlv.$D.dns

* auto-remove-recheck-key:
  * enum all DNSSEC domain in OpenDNSSEC and remove old KEY from DLV
  * re-create DLV cookies in DNS and ask for re-check

TODO:
 * timeout on ods-ksmutil in case on lock 
   + specially on crontab
 * put a lock on the crontab to disable execute in case of process already started



