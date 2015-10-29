# Lab-Simulation
This simulation contains a MUX router running BIRD with two client and two peers exchanging BGP routes via MUX.

Topology:
==========

|Host_1|-----|M|-----|Peer_1|
             |U|-----------------|Route_Server|
|Host_2|-----|X|-----|Peer_2|


Below Test Cases has been covered in this Simulation:

1) AS-Path Filtering
2) Prefix-Filtering
3) Community-Filtering

AS-Path & Prefix Filtering:
===========================
1) We are using AS range as [47065, 61574, 61575, 61576, 263842, 263843, and 263844] from which the prefixes will be originated.
2) Any prefix originated by AS other than the above will be rejected by MUX and will not be advertised to any of the direct 
Peers or Route_server.
3) We are using prefix range as [184.164.224.0/19, 138.185.228.0/22, 204.9.168.0/22]
4) Any prefixes other than the above will be rejected by MUX at BGP peering with Host.
function rt_import(int set peer_asns)
{
 if (bgp_path.last ~ peer_asns) then return true;
 return false;
}

function rt_import(int set peer_asns)
{
 if (bgp_path.last ~ peer_asns) then return true;
 return false;
}

filter bgp_block_test
{
 if (rt_import([ 61574..61576, 263842..263844]) && net ~ [184.164.224.0/19+,138.185.228.0/22+,204.9.168.0/22+]) then
 {    bgp_path.delete([64512..65535]);
      accept;
 }
 if (rt_import([64512..65535]) && net ~ [184.164.224.0/19+,138.185.228.0/22+,204.9.168.0/22+]) then
 {    bgp_path.delete([64512..65535]);
      accept;
 }
 reject;
}
