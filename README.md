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


TODO:

    * Test it in real environment


