# ConfigMaps and Secrets in Kustomize

## What You'll Learn
This section covers how to manage application configuration using Kustomize:
- Creating ConfigMaps from files
- Mounting ConfigMaps in pods
- Updating configurations for different environments

## Directory Structure
```
.
├── base/                     # Base configuration
│   ├── config/              # Configuration files
│   │   └── app.properties   # Application properties
│   ├── deployment.yaml      # Deployment using ConfigMap
│   └── kustomization.yaml   # Generates ConfigMap
└── overlay/                 # Environment-specific configs
    ├── config/             
    │   └── app.properties   # Modified properties
    └── kustomization.yaml   # Updates ConfigMap
```

## Understanding the Setup

### Base Configuration
- `app.properties`: Default application settings
- `deployment.yaml`: Mounts ConfigMap as a volume
- `kustomization.yaml`: Generates ConfigMap from properties file

### Overlay Configuration
- Modified `app.properties` with environment-specific values
- Uses `replace` behavior to update the entire ConfigMap

## Try It Yourself

1. View the base ConfigMap:
```bash
kubectl kustomize base/
```

2. See the modified version:
```bash
kubectl kustomize overlay/
```

## Key Features
1. **ConfigMap Generation**
   - Automatically creates ConfigMaps from files
   - Handles updates and changes
   - Generates unique names when content changes

2. **Volume Mounting**
   - Mounts ConfigMap as a volume
   - Makes configuration available to containers
   - Updates automatically when ConfigMap changes

3. **Environment Overrides**
   - Easy to maintain different configurations
   - No need to duplicate entire files
   - Clear separation of base and environment-specific settings

## Best Practices
1. Keep sensitive data out of ConfigMaps
2. Use meaningful file names
3. Document your configuration structure
4. Version control your configurations