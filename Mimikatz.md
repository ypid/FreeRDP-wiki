"http://blog.gentilkiwi.com/mimikatz":Mimikatz is shell for various modules. Here is simple example how to export RDP and/or HyperV certificates with private keys for debugging of RDP session in Wireshark.

Run mimikatz alpha x64, then execute following commands:

    mimikatz # 
    # Enable "debug" privilege to be able to patch CNG service
    privilege::debug
    # Patch CNG service, lasts until next reboot
    crypto::cng
    # Patch CAPI library in memory of this process
    crypto::capi
    
    # Export Remote Desktop certificate(s)
    crypto::certificates  -systemstore:CERT_SYSTEM_STORE_LOCAL_MACHINE -store:"Remote Desktop" /export
    
    # Export HyperV certificate(s)
    crypto::certificates  -systemstore:CERT_SYSTEM_STORE_SERVICES -store:vmms\My -export
