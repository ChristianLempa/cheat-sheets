# Proxmox API Authentication

## Create an API Token on Proxmox

To create a new API Token for your `user` in Proxmox, follow these steps:

1. Open the Proxmox Web UI and navigate to the **'Datacenter'** in the **'Server View'** menu.
2. Select **'API Token'** in the **'Permissions'** menu.
3. Click on **'Add'**.
4. Select the `user`, and add a **'Token ID'**.
5. (Optional) Disable `Privilege Separation`, and set an `Expire` date.
6. Click on **'Add'**.

## Check the API Token

To test the API Token, you can use the following command:

```sh
curl -H "Authorization: PVEAPIToken=root@pam!monitoring=aaaaaaaaa-bbb-cccc-dddd-ef0123456789" https://your-proxmox-url:8006/api2/json/
```
