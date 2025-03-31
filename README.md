# AAP Organization Configuration Template

This project provides a template for configuring organizations in Ansible Automation Platform (AAP) with the following features:

- AD group creation for Team Execute and Team Developers
- GitLab integration with organization-specific repositories
- Service account configuration for both GitLab and AAP
- Documentation generation for organization setup

## Project Structure

```
.
├── playbooks/
│   └── org_config.yml          # Main playbook for organization configuration
├── templates/
│   └── org_setup_doc.md.j2     # Template for organization setup documentation
├── inventory/
│   └── org_inventory.yml       # Inventory file for organization configuration
├── vaults/
│   └── org_vault.yml          # Vault file for sensitive data
└── docs/                      # Generated documentation
```

## Prerequisites

1. Ansible Automation Platform installed and configured
2. GitLab instance accessible
3. Active Directory domain controller accessible
4. Required credentials stored in vault

## Usage

1. **Prepare Vault File**
   ```bash
   ansible-vault create vaults/org_vault.yml
   ```
   Add the required credentials and configuration values.

2. **Configure Organization**
   ```bash
   ansible-playbook -i inventory/org_inventory.yml playbooks/org_config.yml -e env=dev
   ```

3. **View Generated Documentation**
   The documentation will be generated in the `docs/` directory with the format `{org_name}-setup.md`

## Configuration

1. **Organization Details**
   - Edit `vaults/org_vault.yml` to set organization name and description
   - Configure URLs and domains as needed

2. **Service Accounts**
   - Service account passwords are stored in the vault
   - Names follow the pattern: `{org_name}-{service}-sa`

3. **AD Groups**
   - Team Execute: `G-APP-AAP-{org_name}-USER`
   - Team Developers: `G-APP-AAP-{org_name}-ADMIN`

## Security Notes

1. All sensitive data is stored in vault files
2. Service account credentials are automatically generated
3. AD groups are created with appropriate permissions
4. GitLab repositories are created as private

## Support

For issues or questions:
1. Check the generated documentation
2. Contact the AAP team
3. Submit a ticket through the support portal

## Contributing

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
