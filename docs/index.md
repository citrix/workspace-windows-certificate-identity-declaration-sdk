# Certificate Identity Declaration SDK for Citrix Workspace app for Windows

The Certificate Identity Declaration (CID) SDK lets developers create a plug-in that lets Citrix Workspace app authenticate to the StoreFront server by using the certificate installed on the client machine. CID declares the user's smart card identity to a StoreFront server without performing a smart card-based authentication.

CID helps in speeding up connections that use old smart cards. The CID protocol bypasses the crypto authentication done by the smart card.

Using CID, Citrix Workspace app sends the public client certificate to the StoreFront server to identify the user. This approach allows significantly faster connections.

In creating your own plug-in, you must conform to the `CitrixAuthManagerCustomProtocolSDK.h` header file, which is available in the `include` folder.

To use this feature, the CID extension has to be installed and the protocol enabled on the StoreFront site.

> **Note:**
>
> The CID SDK is not supported with StoreFront servers configured with the Citrix Gateway URL.

## Setting up Citrix Identity Declaration SDK

You can configure the CID SDK using the Registry Editor.

To enable the fix, set the following registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Citrix\AuthManager`

-  Name: CustomProtocolDLL
-  Type: DWORD
-  Path: C:\Program Files (x86)\Citrix\Auth   Manager\Plugins\CertificateIdentityDeclaration.dll
-  Enabled: True
-  FallbackOnError: UnsuitableProtocol

The name of the protocol specified in the **ProtocolOrder** key must match the name of the corresponding node under **Protocols**. For more information, see the registry file published with the SDK in the [Downloads](https://www.citrix.com/downloads/workspace-app/) page.

For clarity, in this example, only Certificate Identity Declaration has been specified in the list of protocols.