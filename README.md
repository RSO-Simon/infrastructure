# RSO Infrastructure

This repository contains runtime/deployment configuration for the system.

## Configuration management

All runtime configuration is externalized via environment variables and Helm values.
Changing configuration only a Helm upgrade.

### Configuration inventory

| Service | Config | Source | Example |
|--------|--------|--------|---------|
| ship-service | server port | Helm values → env | 8081 |
| ship-service | context path | Helm values → env | /api/ships |
| ship-service | DB URL | Secret/values → env | jdbc:postgresql://postgres:5432/... |
| ship-service | DB user | Secret → env | postgres |
| ship-service | DB password | Secret → env | (hidden) |
| ship-service | actuator exposure | properties/env | health,info |
| component-service | server port | Helm values → env | 8082 |
| component-service | context path | Helm values → env | /api/components |
| component-service | DB URL | Secret/values → env | jdbc:postgresql://postgres:5432/... |
| component-service | DB user | Secret → env | postgres |
| component-service | DB password | Secret → env | (hidden) |