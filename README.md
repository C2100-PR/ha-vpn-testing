# HA VPN Testing Tools

This repository contains tools for testing and monitoring High Availability VPN configurations in Google Cloud Platform.

## Components

1. **VPN Testing Script** (`scripts/test_vpn.sh`)
   - Tests VPN tunnel status across all regions
   - Verifies peer IP connectivity
   - Monitors tunnel establishment

2. **VPN Monitor Component** (`src/components/VPNMonitor.jsx`)
   - React component for visualizing VPN status
   - Real-time monitoring of tunnel states
   - Configuration overview for both prod and nonprod environments

## Configuration

### Production VPC (vpc-prod-shared)
- **us-west1**
  - Gateway: prod-us-west1-gateway
  - Peer Gateway: home-vpn-gateway-1
  - Tunnels: tnl0, tnl1 (IKE_V2)

- **us-west4**
  - Gateway: prod-us-west4-gateway
  - Peer Gateway: home-vpn-gateway
  - Tunnels: tnl0, tnl1 (IKE_V2)

### Non-Production VPC (vpc-nonprod-shared)
- **us-central1**
  - Gateway: nonprod-us-central1-gateway
  - Tunnels: tnl0, tnl1 (IKE_V2)

- **us-east1**
  - Gateway: nonprod-us-east1-gateway
  - Tunnels: tnl0, tnl1 (IKE_V2)

- **us-west1**
  - Gateway: nonprod-us-west1-gateway
  - Tunnels: tnl0, tnl1 (IKE_V2)

## Usage

### Testing Script
```bash
chmod +x scripts/test_vpn.sh
./scripts/test_vpn.sh
```

### React Component
Import and use the VPNMonitor component in your React application:

```jsx
import VPNMonitor from './components/VPNMonitor';

function App() {
  return (
    <div>
      <VPNMonitor />
    </div>
  );
}
```

## Notes
- All tunnels use IKE_V2
- Cloud ASN: 64512
- Peer ASN: 64514
- Monitoring includes both tunnel status and peer IP connectivity