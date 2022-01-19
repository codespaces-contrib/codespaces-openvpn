# Using the OpenVPN client from GitHub Codespaces

GitHub Codespaces provides a useful environment for development that is separated from your local machine. This provides some nice security benefits due to the fact that the codespace has no direct route to your machine or the network it is sitting in. However, you may have a resource you need to access that is in a private network. This sample illustrates how to set up the OpenVPN (v2) client in a codespace to connect into a OpenVPN capable VPN gateway.

# Using the sample

1. Your VPN admistrator should be able to provide you with an OpenVPN configuration file. This particular sample is assuming you are using certificate based authentication to access the VPN. We'll call this file `vpnconfig.ovpn`.
2. Work with your administrator to place any needed certificates or keys in the `vpnconfig.ovpn` file. You can tell if the certificates and keys are in the file by looking for the following:

    ```
    <ca>
    -----BEGIN CERTIFICATE-----
    uQltvbIPFv69jSPNotypuUQqRAyLC+gBTVDxN3zC3WPeKMR6vJTh0lxC6GPhkHC
    ...
    -----END CERTIFICATE-----
    </ca>

    <cert>
    -----BEGIN CERTIFICATE-----
    uQltvbIPFv69jSPNotypuUQqRAyLC+gBTVDxN3zC3WPeKMR6vJTh0lxC6GPhkHC
    ...
    -----END CERTIFICATE-----
    </cert>

    <key>
    -----BEGIN CERTIFICATE-----
    uQltvbIPFv69jSPNotypuUQqRAyLC+gBTVDxN3zC3WPeKMR6vJTh0lxC6GPhkHC
    ...
    -----END CERTIFICATE-----
    </key>

    ```
    
    For example, see [here](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-openvpn-clients#linux) for information on setting up config file for a connection to an Azure VPN Gateway. You can skip the steps that install the client and use the GUI.
3. Create a Codespaces user secret called `OPENVPN_CONFIG` and place the contents of the file in it.
4. Assign this secret to either this repository or your own fork of it.
5. Create a codespace - after its started, you should be connected to your VPN. If you aren't you can manually run `.devcontainer/start-openvpn.sh` to try again and logs can be found in `.devcontainer/openvpn-tmp/openvpn.log`.



