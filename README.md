##Lab-Simulation
This simulation contains a MUX router running BIRD with two client and two peers exchanging BGP routes via MUX.

####Topology:
==========

|Host_1|-----|M|-----|Peer_1|
             |U|-----------------|Route_Server|
|Host_2|-----|X|-----|Peer_2|


Below Test Cases has been covered in this Simulation:
<ol start="1">
  <li>AS-Path Filtering</li>
  <li>Prefix-Filtering</li>
  <li>Community-Filtering</li>
</ol>

####AS-Path & Prefix Filtering:
===========================
<ol start="1">
<li>We are using AS range as [47065, 61574, 61575, 61576, 263842, 263843, and 263844] from which the prefixes will be originated.</li>
<li>Any prefix originated by AS other than the above will be rejected by MUX and will not be advertised to any of the direct
Peers or Route_server.</li>
<li>We are using prefix range as [184.164.224.0/19, 138.185.228.0/22, 204.9.168.0/22]</li>
<li>Any prefixes other than the above will be rejected by MUX at BGP peering with Host.</li>
