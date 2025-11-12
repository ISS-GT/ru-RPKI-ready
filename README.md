# ru-RPKI-ready
This repository contains the dataset for the paper "ru-RPKI-ready: the Road Left to Full ROA Adoption" by Gouda et al., published in ACM Internet Measurement Conference (IMC) 2025. The dataset provides essential information regarding routed IPv4 and IPv6 prefixes that enables researchers and operators to follow the RPKI planning and deployment framework proposed in the paper. For more details regarding the framework, refer to the [paper](https://deepakgouda.github.io/assets/pdf/IMC-2025-ru-RPKI-ready.pdf).

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17237911.svg)](https://doi.org/10.5281/zenodo.17237911)

## Downloading the Latest Release
To download the latest release of ru-RPKI-ready, you can use the following command in your terminal:

If you do not have Git LFS installed, please refer to the [Git LFS installation guide](https://git-lfs.github.com/) before proceeding.

```bash
git clone git@github.com:ISS-GT/ru-RPKI-ready.git
cd ru-RPKI-ready/data
git lfs pull
```

## Using the dataset in Python
To load and use the dataset in Python, you can use the following code snippet:

```python
>>> import pandas as pd
>>> data = pd.read_parquet("data/prefix_tags_2025-04-01_v4.parquet")
>>> data[data.prefix == "208.186.48.0/20"].iloc[0]
prefix                                                             208.186.48.0/20
af                                                                               4
RIR                                                                           ARIN
RPKI Issuing Authority                                  Allstream Business US, LLC
Authoritative Allocation Type                                           ALLOCATION
Customer Organization(s)                                              [101netlink]
Customer Allocation Type(s)                                         [REALLOCATION]
RPKI Status                                                               NotFound
RPKI Certificate                 46:CD:B7:E7:87:A9:20:32:5B:E6:E3:AA:56:58:59:C...
Origin ASN                                                                   21541
ASN Organization Name                                                   101netlink
Tag List                         [ROA Not Found, Certified, Reassigned, Diff SK...
```

### Dataset Description
- RPKI Issuing Authority: The organization with the authority to issue RPKI certificates and ROAs for the prefix.
- Authoritative Allocation Type: The type of allocation held by the RPKI issuing authority (e.g., `ALLOCATION`, `ALLOCATED PA`).
- Customer Organization(s): The customer organizations holding further reallocations for the prefix.
- Customer Allocation Type(s): The type of allocations held by the customer organizations (e.g., `REALLOCATION`, `ASSIGNED PA`).
- RPKI Status: The RPKI status of the prefix (e.g., `Valid`, `NotFound`, `Invalid` or `Invalid,more-specific`).
- RPKI Certificate: The RPKI certificate containing the prefix, which can be used to issue ROAs.
- Origin ASN: The Autonomous System Number (ASN) originating the prefix in BGP.
- ASN Organization Name: The name of the organization associated with the origin ASN.
- Tag List: A list of tags associated with the prefix.