# API Lifecycle & Versioning: Mercur

## Versioning Strategy
Mercur employs a versioning strategy that primarily uses the URL path to denote the version of the API. This approach allows clients to specify the desired API version directly in the endpoint URL, ensuring clarity and ease of access. For example, the API endpoint might look like `https://api.mercur.com/v1/resource`. Additionally, clients have the option to specify the API version through custom HTTP headers for more flexible version negotiation.

## Current Versions
- **v1.0**: Active (launched January 2022)
- **v1.1**: Active (launched August 2022)
- **v2.0**: Active and preferred (launched May 2023)

## Deprecation Timeline
Mercur operates with a clear deprecation strategy to maintain transparency and consistency for clients:
- **v1.0**: Deprecated in October 2023, with a six-month grace period before sunset in April 2024.
- **v1.1**: Scheduled for deprecation notice in April 2024, sunset in October 2024.
- Clients are notified via email, documentation updates, and in-API warnings six months prior to deprecation and again three months before the final sunset.

## Breaking Changes
Below is a history of major breaking changes introduced in API versions:
- **v1.1**: Modified authentication mechanism; migration from API key to OAuth 2.0.
- **v2.0**: Restructured resource endpoints for consolidation and introduced new error handling formats.

## Migration Guides
To facilitate smooth upgrades between versions, Mercur provides detailed migration guides:
- **v1.0 to v1.1**: A guide focused on updating the authentication process from API key to OAuth 2.0, including step-by-step setup instructions.
- **v1.1 to v2.0**: A comprehensive guide detailing endpoint restructuring, enhanced security features, and updated error handling procedures. Sample code snippets and best practices are provided to ease the transition.

## Backward Compatibility Approach
To maintain a seamless user experience, Mercur strives for backward compatibility within minor versions (e.g., v1.0 to v1.1). Where possible, new features are introduced in a way that does not disrupt existing functionality. However, major versions (such as v2.0) may introduce breaking changes, with ample notice and support offered.

## Version Timeline

```plaintext
|----------------|----------------|----------------|----------------|----------------|----------------|
Jan 2022         Aug 2022         May 2023         Oct 2023         Apr 2024         Oct 2024
v1.0 Launched    v1.1 Launched    v2.0 Launched    v1.0 Deprecated  v1.1 Deprecation v1.1 Sunset
                                                  Notice           Notice            
```

Mercur’s versioning and lifecycle management processes are designed to ensure stability, reliability, and clarity for all API consumers. Regular updates and communication are part of the commitment to high-quality API stewardship.