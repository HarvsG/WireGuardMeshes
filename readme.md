# Compare WireGuard Mesh Tools
[WireGuard](https://wireguard.com/) is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography and supports mesh networking. However by default it requires manual configuration. As such adding a new client to the network would require the admin to update O(n<sup>2</sup>) client configurations each time they add a new client. [wg-dynamic](https://git.zx2c4.com/wg-dynamic/about/docs/idea.md) was a proposed WireGuard-native tool that would help with autoconfiguration, unfortunately development of this has gone stale. So here is a list of alternative tools instead.

## Table
| Feature\Software | Open source | Free | Full Mesh | Auto conf | Devices | Supports Users | Allows full tunnel | Subnet Access | NAT traversal | Linux | Windows | MacOS | Android | iOS | OpenWRT | Custom DNS |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [Vanilla WireGuard](https://www.wireguard.com/repositories/) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | Unlimited | :x: | :white_check_mark: | :white_check_mark: | :x: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :white_check_mark: |
| [Tailscale](https://github.com/tailscale/tailscale) | :white_check_mark:[:exclamation:<sup>0<sup>](#tsexplain1) | :x::free: | :white_check_mark: | :white_check_mark: | Unlimited :one::zero::zero: | :white_check_mark: :three: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians::lock_with_ink_pen: | :globe_with_meridians::lock_with_ink_pen: | :globe_with_meridians: | :globe_with_meridians::lock_with_ink_pen: | :white_check_mark: | :white_check_mark: [:exclamation:<sup>3<sup>](#tsexplain2) |
| [Headscale](https://github.com/juanfont/headscale) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians:[:exclamation:<sup>2<sup>](#hsexplain1) | :globe_with_meridians::lock_with_ink_pen:[:exclamation:<sup>2<sup>](#hsexplain1) | :white_check_mark: | :white_check_mark: |
| [Netmaker](https://github.com/gravitl/netmaker) | :white_check_mark:[:exclamation:<sup>1<sup>](#nmexplain1) | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians: | :eight_pointed_black_star::snowflake: | :eight_pointed_black_star::snowflake: | :white_check_mark: | :white_check_mark: |
| [WGSD](https://github.com/jwhited/wgsd) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | Unlimited | :x: | :white_check_mark: | :x: | :white_check_mark: | :white_check_mark: | :x: | :x: | :x: | :x: | :white_check_mark: | :x: |
| [Innernet](https://github.com/tonarino/innernet ) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | Unlimited | :white_check_mark: | :white_check_mark: | :x: | :white_check_mark: | :white_check_mark: | :x: | :white_check_mark: | :x: | :x: | :x: |  |
| [Wesher](https://github.com/costela/wesher) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: |  |  |  | :white_check_mark: | :x: | :x: | :x: | :x: | :x: | :x: |
| [Netbird](https://github.com/netbirdio/netbird) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited :two::zero: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | :x: | :white_check_mark: | :white_check_mark: |
| [wgmesh](https://github.com/aschmidt75/wgmesh) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: | :white_check_mark: | :x: | :x: | :globe_with_meridians: | :x: | :x: | :x: | :x: | :x: | :x: |
| [wiresmith](https://github.com/svenstaro/wiresmith) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: | :x: | :x: | :x: | :globe_with_meridians: | :x: | :x: | :x: | :x: | :x: | :x: |
| [webmesh](https://github.com/webmeshproj/webmesh) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians: | :soon: | :soon: | :soon: | :white_check_mark: |
| [NordVPN Meshnet](https://github.com/NordSecurity/libtelio) | :white_check_mark: [:exclamation:<sup>4<sup>](#nvmexplain1) | :white_check_mark: | :white_check_mark: | :white_check_mark: | Internal :one::zero: External :five::zero: [:exclamation:<sup>5<sup>](#nvmexplain2) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: :lock_with_ink_pen: | :globe_with_meridians: :lock_with_ink_pen: | :globe_with_meridians: :lock_with_ink_pen: | :globe_with_meridians: :lock_with_ink_pen: | :soon: | :white_check_mark: |
  
 <sup>0</sup><a name="tsexplain1">Tailscale's client code is open source. Tailscale's control server code is entirely closed source (It's a SaaS product).</a>  
  
 <sup>1</sup><a name="nmexplain1">Netmaker uses the SSPL license, which is not an "official" open source license occording to the OSI.</a>  
  
 <sup>2</sup><a name="hsexplain1">Headscale uses the tailscale mobile clients. <a href="https://github.com/juanfont/headscale/blob/main/docs/android-client.md">Andriod nstructions</a></a>. <a href="https://github.com/juanfont/headscale/blob/main/docs/iOS-client.md">iOS</a></a>
  
 <sup>3</sup><a name="tsexplain2">When routing all traffic through an exit node tailscale ignores custom DNS. <a href="https://github.com/tailscale/tailscale/issues/8237">Issue</a></a>

 <sup>4</sup><a name="nvmexplain1">Open source parts: `libtelio` - multiplatform meshnet library, `nordvpn-linux` - vpn client app for linux with integrated meshnet feature, `libdrop` - multiplatform file-sharing-over-meshnet library.</a>

 <sup>5</sup><a name="nvmexplain2">Internal - peers with own user devices. External - peers with other users' devices.</a>
 
## Legend
- :free: Has free tier
- :three: Limited amount on free tier (e.g 3)
- :lock_with_ink_pen: This software version is closed source
- :credit_card: Paid version only
- :globe_with_meridians: Client can join as member of the full mesh
- :eight_pointed_black_star: Client can join as a 'spoke' off a node/gateway on the mesh
- :snowflake: Client can join the network but updates to the network are not automatically propgated to the client
- :soon: Developer claims the feature is coming soon
- [:exclamation:<sup>0<sup>](https://github.com/HarvsG/WireGuardMeshes/blob/main/readme.md#legend) Significant exception to the feature (should link to explanation)

## Disclaimers
- [WireGuard](https://wireguard.com/) is a registered trademark of Jason A. Donenfeld.
- I do not independently verify each of the features and generally rely on the honesty of contributors please open an issue if you find any mistakes.

## Changes
Please help update this table by using [issues](https://github.com/HarvsG/WireGuardMeshes/issues) or [pull requests](https://github.com/HarvsG/WireGuardMeshes/pulls). You may find https://www.tablesgenerator.com/markdown_tables helpful (File -> paste table data)

## Columns
| Column | Description |
|---|---|
| Feature\Software | The name and hyperlink to the project's main repository or website. |
| Open source | Is the project open source. |
| Free | Is the project entirely free to download, install and use. |
| Full Mesh | Does the project allow every peer to communicate with every other peer directly. Relying on `AllowedIPs` to route traffic via a central peer in a hub and spoke model does not count. |
| Auto conf | When a new peer is added to the mesh, are all other peers update automatically. Usually a requirement to be featured in this repo |
| Devices | How many devices can the mesh support. |
| Supports Users | Does the project allow users to be configured, usually for user access control. |
| Allows full tunnel | Is the project capable of tunnelling all external traffic over at least one of the peers. |
| Subnet Access | Can a device 'expose' the devices on its subnet to peers, usually using wiregaurd's `AllowedIPs`. This could allow you to access resources on your home network if your router was connected to the mesh, for example. |
| NAT traversal | Can two peers that are each behind a separate NAT communicate with one another. This usually requires some other non-NATed central peer to update each NATed peer with the other's IP and port. Sometimes called NAT hole-punching |
| Linux | Can the project be set up on a Linux machine e.g Ubuntu |
| Windows | Can the project be installed on a Windows machine. |
| MacOS | Can the project be installed on a MacOS machine. |
| Android | Is there an Android App and can it connect to every other peer. |
| iOS | Is there an iOS App and can it connect to every other peer. |
| OpenWRT | Can the project be installed on an OpenWRT router. Useful if you want everything on your network to be able to access the devices on the mesh |
| Custom DNS | Can the DNS provider used by all peers be configured centrally. |
