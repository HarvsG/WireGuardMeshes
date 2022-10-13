# Compare WireGuard Mesh Tools
[WireGuard](https://wireguard.com/) is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography and supports mesh networking. However by default it requires manual configuartion. As such adding a new client to the network would require the admin to update O(n<sup>2</sup>) client configurations each time they add a new client. [wg-dynamic](https://git.zx2c4.com/wg-dynamic/about/docs/idea.md) was a proposed WireGuard-native tool that would help with autoconfiguration, unfortunately development of this has gone stale. So here is a list of alternative tools instead.

## Table
| Feature\Software | Open source | Free | Full Mesh | Auto conf | Devices | Supports Users | Allows full tunnel | Subnet Access | NAT traversal | Linux | Windows | MacOS | Android | iOS | OpenWRT | Custom DNS |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [Vanilla WireGuard](https://www.wireguard.com/repositories/) | :white_check_mark: | :white_check_mark: | :x: | :x: | Unlimited | :x: | :white_check_mark: | :white_check_mark: | :x: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :eight_pointed_black_star: | :white_check_mark: |
| [Tailscale](https://github.com/tailscale/tailscale) | :white_check_mark:[:exclamation:<sup>0<sup>](#tsexplain1) | :x::free: | :white_check_mark: | :white_check_mark: | Unlimited :two::zero: | :white_check_mark: :one: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians::lock_with_ink_pen: | :globe_with_meridians::lock_with_ink_pen: | :globe_with_meridians::lock_with_ink_pen: | :globe_with_meridians::lock_with_ink_pen: | :white_check_mark: | :white_check_mark: |
| [Headscale](https://github.com/juanfont/headscale) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians:[:exclamation:<sup>0<sup>](#hsexplain1) | :x: | :white_check_mark: | :white_check_mark: |
| [Netmaker](https://github.com/gravitl/netmaker) | :white_check_mark:[:exclamation:<sup>0<sup>](#nmexplain1) | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :globe_with_meridians: | :globe_with_meridians: | :globe_with_meridians: | :eight_pointed_black_star::snowflake: | :eight_pointed_black_star::snowflake: | :white_check_mark: | :white_check_mark: |
| [WGSD](https://github.com/jwhited/wgsd) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | Unlimited | :x: | :white_check_mark: | :x: | :white_check_mark: | :white_check_mark: | :x: | :x: | :x: | :x: | :x: | :x: |
| [Innernet](https://github.com/tonarino/innernet ) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | Unlimited | :white_check_mark: | :white_check_mark: | :x: | :white_check_mark: | :white_check_mark: | :x: | :white_check_mark: | :x: | :x: | :x: |  |
| [Wesher](https://github.com/costela/wesher) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: |  |  |  | :white_check_mark: | :x: | :x: | :x: | :x: | :x: | :x: |
| [VxWireguard](https://github.com/m13253/VxWireguard-Generator) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| [RAIT](https://gitlab.com/NickCao/RAIT) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| [Netbird](https://github.com/netbirdio/netbird) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited :two::zero: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | :x: | :white_check_mark: | :soon: |
| [wgmesh](https://github.com/aschmidt75/wgmesh) | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: | Unlimited | :x: | :white_check_mark: | :x: | :x: | :globe_with_meridians: | :x: | :x: | :x: | :x: | :x: | :x: |
  
 <sup>0</sup><a name="tsexplain1">Tailscale's client code is open source. Tailscale's control server code is entirely closed source (It's a SaaS product).</a>  
 <sup>1</sup><a name="nmexplain1">Netmaker uses the SSPL license, which is not an "official" open source license occording to the OSI.</a>  
 <sup>2</sup><a name="hsexplain1">Headscale uses the tailscale android client. <a href="https://github.com/juanfont/headscale/blob/main/docs/android-client.md">Instructions</a></a>
 
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

## Disclaimer
 [WireGuard](https://wireguard.com/) is a registered trademark of Jason A. Donenfeld.
 
## Changes
Please help update this table by using [issues](https://github.com/HarvsG/WireGuardMeshes/issues) or [pull requests](https://github.com/HarvsG/WireGuardMeshes/pulls). You may find https://www.tablesgenerator.com/markdown_tables helpful (File -> paste table data)

