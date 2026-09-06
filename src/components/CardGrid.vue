<script setup>
import { ref } from 'vue'
import Card from './Card.vue'

const colors = [
  'rose-700', 'fuchsia-600', 'lime-700', 'indigo-600', 'amber-700',
  'teal-600', 'orange-600', 'cyan-700', 'purple-600', 'emerald-700',
  'sky-600', 'red-600', 'teal-700', 'green-600', 'violet-600',
  'pink-600', 'blue-600', 'lime-600', 'orange-700',
  'cyan-600', 'rose-600', 'emerald-600', 'amber-600',
  'yellow-600'
]

const cards = ref([
  {
    id: 1,
    title: 'Network Interfaces',
    color: colors[0],
    items: [
      { cmd: 'ip -br addr', desc: 'Show IP addresses' },
      { cmd: 'ip link', desc: 'List interfaces' },
      { cmd: 'ip -s link', desc: 'Interface stats' },
      { cmd: 'ethtool eth0', desc: 'Link info' },
      { cmd: 'cat /proc/net/dev', desc: 'Traffic stats' },
      { cmd: 'ip -br link', desc: 'Compact interface list' },
      { cmd: 'ls /sys/class/net', desc: 'List all interfaces' }
    ]
  },
  {
    id: 2,
    title: 'IP Addresses',
    color: colors[1],
    items: [
      { cmd: 'ip addr', desc: 'All IPs' },
      { cmd: 'ip -4 addr', desc: 'IPv4 only' },
      { cmd: 'ip addr add 192.168.1.50/24 dev eth0', desc: 'Add IP' },
      { cmd: 'ip addr del 192.168.1.50/24 dev eth0', desc: 'Remove IP' },
      { cmd: 'hostname -I', desc: 'Host IPs' }
    ]
  },
  {
    id: 3,
    title: 'Routing',
    color: colors[2],
    items: [
      { cmd: 'ip route', desc: 'Show routes' },
      { cmd: 'ip route get 8.8.8.8', desc: 'Route for IP' },
      { cmd: 'ip route add default via 192.168.1.1', desc: 'Add default' },
      { cmd: 'ip route del default', desc: 'Remove default' },
      { cmd: 'ip route add 10.10.0.0/16 via 192.168.1.1', desc: 'Add route' }
    ]
  },
  {
    id: 4,
    title: 'Connectivity',
    color: colors[3],
    items: [
      { cmd: 'ping 8.8.8.8', desc: 'Test IP connectivity' },
      { cmd: 'ping -c 4 8.8.8.8', desc: '4 pings' },
      { cmd: 'traceroute example.com', desc: 'Path to host' },
      { cmd: 'mtr example.com', desc: 'Ping + traceroute' },
      { cmd: 'tracepath example.com', desc: 'Path + MTU' },
      { cmd: 'ping -W 2 8.8.8.8', desc: 'Ping with timeout' },
      { cmd: 'ip route get 8.8.8.8', desc: 'Test routing' }
    ]
  },
  {
    id: 5,
    title: 'DNS',
    color: colors[4],
    items: [
      { cmd: 'dig example.com', desc: 'DNS query' },
      { cmd: 'dig +short example.com', desc: 'Short answer' },
      { cmd: 'dig A example.com', desc: 'IPv4 query' },
      { cmd: 'dig AAAA example.com', desc: 'IPv6 query' },
      { cmd: 'resolvectl status', desc: 'DNS config' },
      { cmd: 'host example.com', desc: 'Simple DNS lookup' },
      { cmd: 'nslookup example.com', desc: 'DNS lookup' }
    ]
  },
  {
    id: 6,
    title: 'TCP/UDP Ports',
    color: colors[5],
    items: [
      { cmd: 'ss -tuln', desc: 'Listening ports' },
      { cmd: 'ss -tulpn', desc: 'Ports with processes' },
      { cmd: 'ss -tan', desc: 'All TCP connections' },
      { cmd: 'ss -ltnp', desc: 'TCP ports with PIDs' },
      { cmd: 'ss -s', desc: 'Socket stats' },
      { cmd: 'ss -uan', desc: 'All UDP sockets' },
    ]
  },
  {
    id: 7,
    title: 'Port Testing',
    color: colors[6],
    items: [
      { cmd: 'nc -vz 192.168.1.10 22', desc: 'Test TCP port' },
      { cmd: 'nc -zv 192.168.1.10 20-25', desc: 'Scan ports' },
      { cmd: 'nc -u -vz 192.168.1.10 53', desc: 'Test UDP port' },
      { cmd: 'telnet example.com 80', desc: 'Manual TCP test' },
      { cmd: 'curl telnet://example.com:25', desc: 'TCP test' },
    ]
  },
  {
    id: 8,
    title: 'HTTP/HTTPS',
    color: colors[7],
    items: [
      { cmd: 'curl https://example.com', desc: 'HTTP request' },
      { cmd: 'curl -I https://example.com', desc: 'Headers only' },
      { cmd: 'curl -v https://example.com', desc: 'Verbose' },
      { cmd: 'curl -L https://example.com', desc: 'Follow redirects' },
      { cmd: "curl -w '%{http_code}\\n' URL", desc: 'Status code' }
    ]
  },
  {
    id: 9,
    title: 'ARP',
    color: colors[8],
    items: [
      { cmd: 'ip neigh', desc: 'ARP table' },
      { cmd: 'ip neigh show dev eth0', desc: 'Interface ARP' },
      { cmd: 'ip neigh flush all', desc: 'Clear ARP' },
      { cmd: 'arp -n', desc: 'Legacy ARP' },
      { cmd: 'arping 192.168.1.1', desc: 'L2 reachability' },
      { cmd: 'ip -6 neigh', desc: 'IPv6 neighbors' },
    ]
  },
  {
    id: 10,
    title: 'NetworkManager',
    color: colors[9],
    items: [
      { cmd: 'nmcli device status', desc: 'Device state' },
      { cmd: 'nmcli connection show', desc: 'Connections' },
      { cmd: 'nmcli device wifi list', desc: 'Wi-Fi networks' },
      { cmd: 'nmcli device wifi connect SSID', desc: 'Connect Wi-Fi' },
      { cmd: 'nmcli radio wifi', desc: 'Wi-Fi state' },
      { cmd: 'nmcli general status', desc: 'NM status' }
    ]
  },
  {
    id: 11,
    title: 'DHCP',
    color: colors[10],
    items: [
      { cmd: 'dhclient', desc: 'Request IP' },
      { cmd: 'dhclient -v eth0', desc: 'Verbose DHCP' },
      { cmd: 'dhclient -r eth0', desc: 'Release lease' },
      { cmd: 'nmcli device reapply eth0', desc: 'Reapply config' },
      { cmd: 'journalctl -u NetworkManager', desc: 'NM logs' },
    ]
  },
  {
    id: 12,
    title: 'Packet Capture',
    color: colors[11],
    items: [
      { cmd: 'tcpdump -i eth0', desc: 'Capture on eth0' },
      { cmd: 'tcpdump -i any', desc: 'Capture all' },
      { cmd: 'tcpdump -nn -i eth0', desc: 'No resolve' },
      { cmd: 'tcpdump -i eth0 port 443', desc: 'HTTPS traffic' },
      { cmd: 'tcpdump -i eth0 -w file.pcap', desc: 'Save to file' }
    ]
  },
  {
    id: 13,
    title: 'nftables',
    color: colors[12],
    items: [
      { cmd: 'nft list ruleset', desc: 'Show all rules' },
      { cmd: 'nft list tables', desc: 'List tables' },
      { cmd: 'nft list table inet filter', desc: 'Show table' },
      { cmd: 'nft monitor', desc: 'Monitor changes' },
      { cmd: 'systemctl status nftables', desc: 'Service status' }
    ]
  },
  {
    id: 14,
    title: 'iptables',
    color: colors[13],
    items: [
      { cmd: 'iptables -L -n -v', desc: 'List rules' },
      { cmd: 'iptables -S', desc: 'Rules as commands' },
      { cmd: 'iptables -t nat -L -n -v', desc: 'NAT rules' },
      { cmd: 'iptables-save', desc: 'Export rules' },
      { cmd: 'ip6tables -L -n -v', desc: 'IPv6 rules' },
      { cmd: 'iptables-restore', desc: 'Restore rules' }
    ]
  },
  {
    id: 16,
    title: 'Hostname',
    color: colors[15],
    items: [
      { cmd: 'hostname', desc: 'System hostname' },
      { cmd: 'hostnamectl', desc: 'Hostname info' },
      { cmd: 'hostname -I', desc: 'IP addresses' },
      { cmd: 'cat /etc/hostname', desc: 'Configured hostname' },
      { cmd: 'cat /etc/hosts', desc: 'Static mappings' },
      { cmd: 'hostname -f', desc: 'Fully qualified hostname' },
    ]
  },
  {
    id: 17,
    title: 'Namespaces',
    color: colors[16],
    items: [
      { cmd: 'ip netns list', desc: 'List namespaces' },
      { cmd: 'ip netns add test', desc: 'Create namespace' },
      { cmd: 'ip netns exec test ip addr', desc: 'Run in namespace' },
      { cmd: 'ip netns exec test ping 10.0.0.1', desc: 'Ping from ns' },
      { cmd: 'ip netns delete test', desc: 'Delete namespace' }
    ]
  },
  {
    id: 18,
    title: 'Bridges',
    color: colors[17],
    items: [
      { cmd: 'ip link show type bridge', desc: 'List bridges' },
      { cmd: 'bridge link', desc: 'Show ports' },
      { cmd: 'ip link add br0 type bridge', desc: 'Create bridge' },
      { cmd: 'ip link set eth0 master br0', desc: 'Add to bridge' },
      { cmd: 'ip link set br0 up', desc: 'Enable bridge' }
    ]
  },
  {
    id: 19,
    title: 'VLANs',
    color: colors[18],
    items: [
      { cmd: 'ip -d link', desc: 'Show VLANs' },
      { cmd: 'ip link add link eth0 name eth0.100 type vlan id 100', desc: 'Create VLAN' },
      { cmd: 'ip link set eth0.100 up', desc: 'Enable VLAN' },
      { cmd: 'ip addr add 192.168.100.10/24 dev eth0.100', desc: 'IP to VLAN' },
      { cmd: 'ip link delete eth0.100', desc: 'Delete VLAN' }
    ]
  },
  {
    id: 24,
    title: 'Processes',
    color: colors[23],
    items: [
      { cmd: 'lsof -i', desc: 'Network processes' },
      { cmd: 'lsof -i :80', desc: 'Port 80 processes' },
      { cmd: 'ss -tulpn', desc: 'Ports to processes' },
      { cmd: 'fuser -n tcp 8080', desc: 'Find process on port' },
      { cmd: 'ps aux | grep ssh', desc: 'SSH processes' },
      { cmd: 'netstat -tulpn', desc: 'Legacy port listing' }
    ]
  },
  {
    id: 25,
    title: 'Logs',
    color: colors[24],
    items: [
      { cmd: 'journalctl -k', desc: 'Kernel logs' },
      { cmd: 'journalctl -k | grep -i network', desc: 'Network events' },
      { cmd: 'journalctl -u NetworkManager', desc: 'NM logs' },
      { cmd: 'dmesg | grep -i eth', desc: 'Ethernet events' },
      { cmd: 'systemctl status NetworkManager', desc: 'NM status' }
    ]
  }
])
</script>

<template>
  <div class="grid grid-cols-5 gap-8 m-20 text-white">
    <Card
      v-for="card in cards"
      :key="card.id"
      :title="card.title"
      :items="card.items"
      :color="card.color"
    />
  </div>
</template>