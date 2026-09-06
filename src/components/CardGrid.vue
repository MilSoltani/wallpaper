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
    title: 'Connectivity',
    color: colors[2],
    items: [
      { cmd: 'ping -c 4 8.8.8.8', desc: '4 pings' },
      { cmd: 'traceroute example.com', desc: 'Path to host' },
      { cmd: 'mtr example.com', desc: 'Ping + traceroute' },
      { cmd: 'tracepath example.com', desc: 'Path + MTU' },
      { cmd: "curl -o /dev/null -s -w '%{time_total}\\n' URL", desc: 'Time a request' }
    ]
  },
  {
    id: 4,
    title: 'DNS',
    color: colors[3],
    items: [
      { cmd: 'dig example.com', desc: 'DNS query' },
      { cmd: 'dig +short example.com', desc: 'Short answer' },
      { cmd: 'dig AAAA example.com', desc: 'IPv6 query' },
      { cmd: 'host example.com', desc: 'Simple DNS lookup' },
      { cmd: 'nslookup example.com', desc: 'DNS lookup' },
      { cmd: 'resolvectl status', desc: 'DNS config' }
    ]
  },
  {
    id: 5,
    title: 'TCP/UDP Ports',
    color: colors[4],
    items: [
      { cmd: 'ss -tuln', desc: 'Listening ports' },
      { cmd: 'ss -tulpn', desc: 'Ports with processes' },
      { cmd: 'ss -tan', desc: 'All TCP connections' },
      { cmd: 'ss -ltnp', desc: 'TCP ports with PIDs' },
      { cmd: 'ss -s', desc: 'Socket stats' },
      { cmd: 'ss -uan', desc: 'All UDP sockets' }
    ]
  },
  {
    id: 6,
    title: 'Port Testing',
    color: colors[5],
    items: [
      { cmd: 'nc -vz 192.168.1.10 22', desc: 'Test TCP port' },
      { cmd: 'nc -zv 192.168.1.10 20-25', desc: 'Scan ports' },
      { cmd: 'nc -u -vz 192.168.1.10 53', desc: 'Test UDP port' },
      { cmd: 'telnet example.com 80', desc: 'Manual TCP test' },
      { cmd: 'curl telnet://example.com:25', desc: 'TCP test' }
    ]
  },
  {
    id: 7,
    title: 'HTTP/HTTPS',
    color: colors[6],
    items: [
      { cmd: 'curl https://example.com', desc: 'GET request' },
      { cmd: 'curl -I https://example.com', desc: 'Headers' },
      { cmd: "curl -X POST -d '{}' URL", desc: 'POST JSON' },
      { cmd: "curl -H 'Authorization: Bearer TOKEN' URL", desc: 'Auth' },
      { cmd: 'curl -L https://example.com', desc: 'Follow redirects' },
    ]
  },
  {
    id: 8,
    title: 'SSL/TLS',
    color: colors[7],
    items: [
      { cmd: 'openssl s_client -connect example.com:443', desc: 'Test TLS handshake' },
      { cmd: 'openssl x509 -in cert.pem -noout -dates', desc: 'Cert expiry dates' },
      { cmd: 'echo | openssl s_client -connect HOST:443 2>/dev/null | openssl x509 -noout -enddate', desc: 'expiry check' }
    ]
  },
  {
    id: 9,
    title: 'SSH & Remote Access',
    color: colors[8],
    items: [
      { cmd: 'ssh -i key.pem user@host', desc: 'with key' },
      { cmd: 'rsync -avz dir/ user@host:/path', desc: 'Sync directory' },
      { cmd: 'ssh-keygen -t ed25519', desc: 'Generate SSH key' },
      { cmd: 'ssh-copy-id user@host', desc: 'Copy key to server' }
    ]
  },
  {
    id: 10,
    title: 'File Permissions',
    color: colors[9],
    items: [
      { cmd: 'chmod 755 file', desc: 'Set rwxr-xr-x' },
      { cmd: 'chmod -R 755 dir', desc: 'Recursive' },
      { cmd: 'chown user:group file', desc: 'Change owner' },
      { cmd: 'chown -R user:group dir', desc: 'Recursive owner' },
      { cmd: 'ls -la', desc: 'List with permissions' }
    ]
  },
  {
    id: 11,
    title: 'Users & Groups',
    color: colors[10],
    items: [
      { cmd: 'adduser username', desc: 'Create user (Debian)' },
      { cmd: 'usermod -aG sudo username', desc: 'Grant sudo access' },
      { cmd: 'usermod -aG groupname username', desc: 'Add to group' },
      { cmd: 'groups username', desc: 'Show user groups' },
      { cmd: 'deluser username', desc: 'Remove user' }
    ]
  },
  {
    id: 12,
    title: 'Processes',
    color: colors[11],
    items: [
      { cmd: 'lsof -i', desc: 'Network processes' },
      { cmd: 'lsof -i :80', desc: 'Port 80 processes' },
      { cmd: 'ss -tulpn', desc: 'Ports to processes' },
      { cmd: 'fuser -n tcp 8080', desc: 'Find process on port' },
      { cmd: 'ps aux | grep node', desc: 'Filter processes' }
    ]
  },
  {
    id: 13,
    title: 'Text Processing & Search',
    color: colors[12],
    items: [
      { cmd: "grep -r 'text' .", desc: 'Recursive search' },
      { cmd: "find . -name '*.js'", desc: 'Find files by name' },
      { cmd: 'find . -mtime -1', desc: 'Modified in last day' },
      { cmd: "awk '{print $1}' file", desc: 'Print column' },
      { cmd: "sed 's/old/new/g' file", desc: 'Replace text' }
    ]
  },
  {
    id: 14,
    title: 'Signals & Job Control',
    color: colors[13],
    items: [
      { cmd: 'kill -9 PID', desc: 'Force kill process' },
      { cmd: 'kill -HUP PID', desc: 'Reload config (SIGHUP)' },
      { cmd: 'command &', desc: 'Run in background' },
      { cmd: 'nohup command &', desc: 'Survive terminal close' },
      { cmd: 'jobs -l', desc: 'List background jobs' },
      { cmd: 'fg %1', desc: 'Bring job to foreground' }
    ]
  },
  {
    id: 15,
    title: 'Systemd Services',
    color: colors[14],
    items: [
      { cmd: 'systemctl list-units --type=service', desc: 'List running services' },
      { cmd: 'systemctl daemon-reload', desc: 'Reload unit files' },
      { cmd: 'systemctl is-active service', desc: 'Check if running' }
    ]
  },
  {
    id: 16,
    title: 'Kernel & Boot',
    color: colors[15],
    items: [
      { cmd: 'uname -a', desc: 'Kernel & system info' },
      { cmd: 'dmesg | tail -50', desc: 'Recent kernel messages' },
      { cmd: 'journalctl -b', desc: 'Logs since last boot' },
      { cmd: 'cat /proc/cpuinfo', desc: 'CPU details' },
      { cmd: 'lsmod', desc: 'Loaded kernel modules' }
    ]
  },
{
    id: 17,
    title: 'pnpm',
    color: colors[16],
    items: [
      { cmd: 'pnpm why pkg', desc: 'Why is this package installed' },
      { cmd: 'pnpm outdated', desc: 'Check for outdated' },
      { cmd: 'pnpm store prune', desc: 'Clean unused store packages' },
      { cmd: 'pnpm -filter pkgname run build', desc: 'Run script in a workspace pkg' }
    ]
  },
  {
    id: 18,
    title: 'Disk & Storage',
    color: colors[17],
    items: [
      { cmd: 'df -h', desc: 'Disk usage by filesystem' },
      { cmd: 'du -sh dir', desc: 'Size of directory' },
      { cmd: 'du -sh * | sort -h', desc: 'Largest items in dir' },
      { cmd: 'free -h', desc: 'Memory usage' },
      { cmd: 'lsblk', desc: 'List block devices' }
    ]
  },
  {
    id: 19,
    title: 'Archives & Compression',
    color: colors[18],
    items: [
      { cmd: 'tar -czvf archive.tar.gz dir/', desc: 'Compress' },
      { cmd: 'tar -xzvf archive.tar.gz', desc: 'Extract' },
      { cmd: 'zip -r archive.zip dir/', desc: 'Zip directory' },
      { cmd: 'unzip archive.zip', desc: 'Unzip' }
    ]
  },
  {
    id: 20,
    title: 'Logs',
    color: colors[19],
    items: [
      { cmd: 'journalctl -f', desc: 'Follow live logs' },
      { cmd: 'journalctl -u service', desc: 'Service logs' },
      { cmd: 'tail -f /var/log/syslog', desc: 'Follow syslog' },
      { cmd: 'dmesg | tail', desc: 'Recent kernel messages' }
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