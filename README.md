##Lab-Simulation
This simulation contains a MUX router running BIRD with two client and two peers exchanging BGP routes via MUX.

####Topology:
==========
<ol>
<li>|Host_1|-----|M|-----|Peer_1|</li>
<li>             |U|-----------------|Route Server|</li>
<li>|Host_2|-----|X|-----|Peer_2|</li>
</ol>


Below Test Cases has been covered in this Simulation:
<ol start="1">
  <li>AS-Path Filtering</li>
  <li>Prefix-Filtering</li>
  <li>Community-Filtering</li>
</ol>

####AS-Path & Prefix Filtering:
<ol start="1">
<li>We are using AS range as [47065, 61574, 61575, 61576, 263842, 263843, and 263844] from which the prefixes will be originated.</li>
<li>Any prefix originated by AS other than the above will be rejected by MUX and will not be advertised to any of the direct
Peers or Route Server.</li>
<li>We are using prefix range as [184.164.224.0/19, 138.185.228.0/22, 204.9.168.0/22]</li>
<li>Any prefixes other than the above will be rejected by MUX at BGP peering with Host.</li>
</ol>

####Community-Filtering:
<ol start="1">
<li>We have configured the MUX to allow the prefix advertisements to direct peers or Route_Server using communities.
   <ol>
   <li>BGP community list with 6777:* or 0:* will be advertized to only Router Server.</li>
   <li>BGP community list with 47065:peerAs will be advertised to only direct peer with AS no. peerAs.</li>
   <li>Prefixes with no BGP community will not be advertised to any Peer or Route Server.</li>
   <li>BGP community list with both the communities as in point 1 & 2, will be advertised to direct peers based on peerAS number and to Route Server.</li>
   </ol>
   </li>
</ol>
