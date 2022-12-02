# Route 53 Interoperability

Route 53 provides registrar and DNS hosting features. However, it is possible for Route 53 to only do one or the other and have it integrate with other registrars or other DNS hosting.

- R53 accepts your money (domain registration fee)
- R53 allocates 4 name servers (NS) (domain hosting)
- R53 creates a zone file (domain hosting) on the above NS
- R53 communicates with the registry of the TLD (domain registrar)
