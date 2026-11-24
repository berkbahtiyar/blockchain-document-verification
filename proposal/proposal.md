# Blockchain-Based Document Verification System

SEN0401 Special Topics: Blockchain · 2026-2027 Fall · Proposal · Method: BRSF software-development profile · Self-assessed grade 98.1/100

## Team, roles and work distribution

| Member | Student number | E-mail | Administrative roles | Development roles | Planned share |
| --- | --- | --- | --- | --- | --- |
| Berk Bahtiyar | 2200001070 | 22000010@stu.iku.edu.tr | Team lead | Front-end developer, Requirements analyst, Release and operations, Test engineer | 100% |

### Modules and features

| Module or feature | Kind | What it does | Delivers epic | Responsible member | Second member |
| --- | --- | --- | --- | --- | --- |
| Document Processing | Module | Hash calculation and receipt generation | PDF Processing and Receipt | Berk Bahtiyar · 2200001070 |  |
| Verification | Module | Document lookup and result display | Document Verification | Berk Bahtiyar · 2200001070 |  |
| Smart Contract | Module | Authorized document registration | Blockchain Registration | Berk Bahtiyar · 2200001070 |  |

### Process leads

- Mission analysis: Berk Bahtiyar
- System/software requirements definition: Berk Bahtiyar
- Design definition: Berk Bahtiyar
- Implementation: Berk Bahtiyar
- Verification: Berk Bahtiyar
- Validation: Berk Bahtiyar
- Maintenance: Berk Bahtiyar
- Stakeholder needs and requirements: Berk Bahtiyar
- Architecture definition: Berk Bahtiyar
- System analysis: Berk Bahtiyar
- Integration: Berk Bahtiyar
- Transition: Berk Bahtiyar
- Operation: Berk Bahtiyar
- Disposal: Berk Bahtiyar

### Work log

5 entries; chain with 1 issue(s); head fingerprint 43852253d009d1a1e5c153bcfd09e4c37b6caf78abb22bf112e2c36e53df773b.

| No. | Time (UTC) | Member | Process | Hours | What | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 2026-11-24 08:45 | Berk Bahtiyar | Mission analysis | 3 | Analyzed the project requirements, identified the end-user groups and defined the document verification workflow. |  |
| 2 | 2026-11-24 08:53 | Berk Bahtiyar | Stakeholder needs and requirements | 1 | Identified the document issuer and document verifier as the main end-user groups and defined their needs and expectations from the system. |  |
| 3 | 2026-11-24 08:54 | Berk Bahtiyar | System/software requirements definition | 2 | Defined the software requirements, user stories and acceptance criteria for PDF hashing, blockchain registration and document verification. |  |
| 4 | 2026-11-24 08:54 | Berk Bahtiyar | Architecture definition | 2 | Defined the system architecture and selected HTML, CSS, JavaScript, Solidity and Etherium Sepolia as the main development technologies. |  |
| 5 | 2026-11-24 08:55 | Berk Bahtiyar | Design definition | 2 | Prepared the activity model, sequence model, class model and data model. Designed the document registration and verification workflows. |  |

## 1. Mission

### Customer

| Customer (organisation or role) | Contact person or role | How and when you reached them | Relation | What they get from it |
| --- | --- | --- | --- | --- |
| Koel Electronics | Can Çalışkan - Business Analyst | A meeting with the company representative  is planned during the requirements analysis phase to discuss document verification needs. | Operator who runs it | A simple web application for registering and verifying digital documents using blockchain technology. |

### End users

| User group (short name) | Who exactly | What they do with the system | How often | Device or channel |
| --- | --- | --- | --- | --- |
| Document issuer | Staff members of the customer organization who are responsible for preparing, issuing and distributing official PDF documents, certificates and reports to their recipients. | They select PDF documents, generate SHA-256 fingerprints, register these fingerprints on the blockchain using an authorized wallet and download registration receipts after successful transactions. | Occasionally | Browser |
| Document verifier | Individuals who receive digital PDF documents from the customer organization and need to check whether the received documents match the original versions registered by the document issuer. | They select received PDF documents, calculate their SHA-256 fingerprints, compare the fingerprints with blockchain registration records and view the verification results to check document integrity. | Occasionally | Browser |

### Problem

Digital documents such as certificates and reports can be copied or modified after they are issued. A person receiving a PDF document may not know whether the received file is identical to the original version. Traditional verification methods may require contacting the document issuer or comparing documents manually. For example, verifying 10 documents manually may require 10 separate comparisons or confirmation requests. This process can increase the time and effort required for document verification. The proposed system addresses this problem by generating a SHA-256 hash for each PDF document and registering the hash on a blockchain. When a document is received, its hash can be calculated again and compared with the registered record. The system aims to reduce manual verification effort, detect document modifications and provide a simple verification method without publishing original document contents. The numerical example is illustrative and actual customer requirements will be confirmed through a customer interview.

### Mission statement

The project aims to provide document issuers and document verifiers with a simple web application for checking the integrity of PDF documents. The system allows document issuers to register document fingerprints on a blockchain and enables document verifiers to detect modified documents without storing the original document contents on the blockchain.

Origin: Session drafted

### Outcome

Document verifiers will be able to determine whether a received PDF matches a fingerprint previously registered by the designated document issuer. The system will provide a clear verification result without exposing the contents of the original document.

## 2. Scope

### Areas

| Area | Where it lives | How big it is today |
| --- | --- | --- |
| Document Processing | Web browser | One PDF at a time |
| Registration and Verification | Web browser | One issuer and one smart contract are planned |

### Deliverables

| Deliverable | Area | Layer | Kind |
| --- | --- | --- | --- |
| PDF selection and SHA-256 hashing | Document Processing | Product layer | Functional |
| JSON-LD registration receipt | Document Processing | Product layer | Functional |
| Issuer-only document registration | Registration and Verification | Product layer | Functional |
| Document verification and result display | Registration and Verification | Product layer | Functional |

### Exclusions

| Left out | Why |
| --- | --- |
| Mainnet deployment and real payments | To avoid real transaction costs and financial risks. |
| Original document storage on blockchain | To protect document contents and reduce storage costs. |
| Multiple issuers and identity certification | To keep the project manageable for a single developer. |

### Domain entities

| Entity | What it is | Created? | Used? | Retired? |
| --- | --- | --- | --- | --- |
| Document Fingerprint | SHA-256 hash calculated from a PDF file. | Created — yes | Used — yes | Retired — no |
| Registration | Blockchain record containing a document fingerprint and registration timestamp. | Created — yes | Used — yes | Retired — no |
| Verification Receipt | JSON-LD record containing document registration and transaction information. | Created — yes | Used — yes | Retired — yes |

### Project kinds

Provenance and trust. Stack layers they need: Identifiers and publishing, Provenance and metadata.

### Semantic technologies, by stack layer

- Provenance and metadata: PROV-O provenance ontology
- Serialisation: JSON-LD 1.1 contexts

JSON-LD will be used to represent document registration receipts in a structured and machine-readable format. PROV-O will describe the document fingerprint as an entity, the registration process as an activity and the document issuer as an agent. These technologies will provide consistent metadata without requiring a complex database or a separate semantic processing engine.

## 3. Goals

| Goal | Facing | Covers area | Why this goal |
| --- | --- | --- | --- |
| Enable reliable document verification | Mission-facing | Registration and Verification | To allow document verifiers to detect changes in registered PDF documents. |
| Complete document processing and receipt generation | Scope-facing | Document Processing | To ensure that PDF hashing and registration receipt generation are completed. |
| Keep implementation within the agreed project scope | Containment-facing | Registration and Verification | To avoid unauthorized registration, original document publication and out-of-scope features. |

### Specification

The system shall allow users to select PDF documents through a simple web interface. Each document shall be limited to a maximum file size of 10 MB. The application shall calculate a SHA-256 hash locally in the browser. The designated document issuer shall be able to register the hash using a Solidity smart contract on the Ethereum Sepolia test network. Document verifiers shall be able to check whether a calculated hash exists in the contract. The system shall display registered, not registered or an appropriate error message. Duplicate and unauthorized registrations shall be rejected. A JSON-LD receipt shall be available after successful registration. Original PDF contents shall not be stored on the blockchain.

### Test scenarios

| Kind | Scenario (Given / When / Then) |
| --- | --- |
| Nominal | Given a registered PDF, when the verifier selects the original file, then the system displays Registered. |
| Rejection | Given an unauthorized wallet, when it attempts to register a document, then the smart contract rejects the transaction. |
| Boundary | Given a valid PDF with a size of exactly 10 MB, when the user selects it, then the application accepts the file. |
| Absent | Given that no PDF has been selected, when the user attempts verification, then the application displays an error message. |

### Use cases

Actor 1: Document issuer

UC1: Select a PDF document.UC2: Calculate the SHA-256 fingerprint.UC3: Register the fingerprint on the blockchain.UC4: Download a registration receipt.

Actor 2: Document verifier

UC5: Select a received PDF document.UC6: Verify the document fingerprint.UC7: View the verification result.

## 4. Objectives

| Objective | Goal | Measured by | How exactly it is measured | Now | Target | Direction |
| --- | --- | --- | --- | --- | --- | --- |
| Achieve correct document verification results | Enable reliable document verification | Counted | Count correct verification results for two original and two modified PDF documents. | 0 of 4 verified | 4 of 4 verified | Increase |
| Complete document processing functions | Complete document processing and receipt generation | Counted | Count successful SHA-256 hashing and JSON-LD receipt generation tests. | 0 of 2 | 2 of 2 | Increase |
| Maintain the agreed implementation boundaries | Keep implementation within the agreed project scope | Counted | Count unauthorized registrations, raw PDF publications and implemented excluded features during testing and code review. | 0 | 0 | Hold |

### Activity model

The process starts when the user selects a PDF document. The application checks the file type and size. If the file is invalid, an error message is displayed. Otherwise, the SHA-256 fingerprint is calculated. The user selects registration or verification. Registration requires the authorized issuer wallet and transaction confirmation. If the transaction succeeds, a receipt can be downloaded. If it fails, an error is displayed. Verification reads the blockchain record and displays the verification result. The process ends after the result is shown.

### Sequence model

The document issuer selects a PDF through the browser interface. The browser sends the document bytes to the Web Crypto API locally and receives a SHA-256 fingerprint. The browser requests transaction approval from MetaMask. MetaMask submits the fingerprint to the smart contract. The contract checks authorization and returns a transaction result. After confirmation, the browser generates a receipt. The document verifier selects a received PDF. The browser calculates its fingerprint and sends a read-only request to the smart contract. The contract returns the registration status, and the browser displays the result to the verifier.

## 5. Backlog

Kind of development: Initial development

### Epics

| Epic | Pursues objective |
| --- | --- |
| PDF Processing and Receipt | Complete document processing functions |
| Document Verification | Achieve correct document verification results |
| Blockchain Registration | Maintain the agreed implementation boundaries |

### Stories

| Epic | As a | I want | So that | Acceptance (Given / When / Then) | Category | Design concern | Value 1–10 | Time 1–10 | Risk 1–10 | Size 1–10 | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| PDF Processing and Receipt | Document issuer (end user) | to generate a SHA-256 fingerprint from a PDF document | I can identify the exact version of the document | Given a valid PDF document, when the document issuer selects the file, then the application calculates and displays its SHA-256 fingerprint. | New capability | Data | 10 | 9 | 7 | 2 | 13 |
| PDF Processing and Receipt | Document issuer (end user) | to download a registration receipt | I can retain evidence of document registration | Given a successfully confirmed registration transaction, when the document issuer clicks the download button, then the application downloads a JSON-LD receipt containing the fingerprint and transaction information. | New capability | Data | 6 | 4 | 3 | 3 | 4.3 |
| Document Verification | Document verifier (end user) | to verify an original PDF document | I can check whether it matches a registered document | Given a previously registered PDF document, when the document verifier selects the identical file and clicks Verify, then the system displays Registered. | New capability | Interaction | 10 | 9 | 7 | 3 | 8.7 |
| Document Verification | Document verifier (end user) | to check whether a document has been modified | I can identify files that do not match a registered fingerprint | Given a modified version of a registered PDF whose new fingerprint has not been registered, when the document verifier checks the file, then the system displays Not Registered. | New capability | Interaction | 9 | 7 | 8 | 2 | 12 |
| Blockchain Registration | Document issuer (end user) | to restrict document registration to my authorized wallet | unauthorized users cannot register documents in my name | Given a wallet address that is not authorized to register documents, when the wallet attempts to submit a new fingerprint, then the smart contract rejects the transaction and leaves its stored records unchanged. | New capability | Security | 9 | 8 | 9 | 3 | 8.7 |
| Blockchain Registration | Document issuer (end user) | to register a document fingerprint on the blockchain | document verifiers can check it later | Given an authorized issuer wallet and an unregistered document fingerprint, when the issuer confirms the registration transaction, then the smart contract stores the fingerprint and its registration timestamp. A repeated registration of the same fingerprint shall be rejected. | New capability | Security | 10 | 10 | 9 | 3 | 9.7 |

### Definition of done

| Criterion | How it is checked |
| --- | --- |
| SHA-256 document fingerprints are generated correctly. | Compare the generated fingerprint with a reference SHA-256 hash of the same PDF. |
| Original and modified documents are correctly identified. | Verify two original and two modified PDF documents and check the displayed results. |
| Unauthorized and duplicate registrations are rejected. | Attempt registration using an unauthorized wallet and an already registered fingerprint. |

### Class model

The system contains three main classes: DocumentFingerprint, Registration and Receipt. DocumentFingerprint contains the SHA-256 digest and file size. Registration contains the document digest, authorized issuer address and registration timestamp. Receipt contains the digest, issuer address, transaction hash and contract address. One document fingerprint can have zero or one blockchain registration. A confirmed registration can generate a receipt. Original PDF contents remain in the browser and are not permanently stored by the application.

### Test cases

| For story | Test case | Test data |
| --- | --- | --- |
| to generate a SHA-256 fingerprint from a PDF document | Generate the SHA-256 hash and compare it with an independent SHA-256 tool. |  |
| to download a registration receipt | Download the receipt and verify the JSON-LD fields and transaction reference. |  |
| to verify an original PDF document | Verify two original registered documents and check that both return Registered. |  |
| to check whether a document has been modified | Verify modified versions of both documents and check that both return Not Registered. |  |
| to restrict document registration to my authorized wallet | Attempt document registration using an unauthorized wallet and check that the transaction is rejected. |  |
| to register a document fingerprint on the blockchain | Register a new fingerprint, verify its stored timestamp and attempt duplicate registration. |  |

### Data — Class diagram

The data model contains DocumentFingerprint, Registration and Receipt entities. The document fingerprint is represented as a 32-byte SHA-256 digest. The smart contract uses the digest as a unique mapping key and stores the registration timestamp. The issuer address is defined during contract deployment. The JSON-LD receipt contains the document fingerprint, issuer address, contract address and transaction hash. Original PDF contents are not stored permanently.

### Interaction — Sequence diagram

The document issuer selects a PDF file through the browser interface and clicks the Register button. The application calculates the fingerprint and requests transaction approval through MetaMask. After confirmation, a success message and receipt download button are displayed. The document verifier selects a PDF and clicks the Verify button. The application displays Registered, Not Registered or an error message depending on the blockchain response.

### Security — State machine diagram

Only the designated issuer wallet is authorized to register document fingerprints. Every registration request is checked by the smart contract before modifying its stored data. Unauthorized and duplicate registrations are rejected. Verification operations are read-only and cannot modify blockchain records. Original PDF contents remain in the browser. The system does not request or store wallet private keys, passwords or sensitive document contents.

## 6. Course-specific

### Blockchain design

The project will use the Ethereum Sepolia test network and a simple Solidity smart contract for document registration and verification. MetaMask will be used to connect the authorized issuer wallet, while JavaScript and ethers.js will provide communication between the web application and the blockchain.

The application will calculate SHA-256 document fingerprints locally using the browser Web Crypto API. The smart contract will store fingerprints and registration timestamps using a mapping data structure. Only the designated issuer wallet will be allowed to register new fingerprints. Duplicate registrations will be rejected.

Ethereum uses a Proof of Stake consensus mechanism. Blockchain technology is selected because it provides an independently readable and tamper-resistant registration history. Unlike a traditional database controlled by a single administrator, confirmed registration records cannot be silently modified through the proposed smart contract.

A traditional database would be simpler if all users fully trusted a central administrator. However, this project aims to demonstrate independently verifiable document registration. The test network will be used for educational purposes rather than production deployment. No cryptocurrency payments, tokens, NFTs or original PDF contents will be included in the system.

## Plan and risks

| Date | Deliverable | Lead |
| --- | --- | --- |
| 2026-11-24 | Complete customer analysis, requirements and project proposal. | Berk Bahtiyar |
| 2026-11-30 | Implement and test the Solidity smart contract. | Berk Bahtiyar |
| 2026-12-05 | Develop the web interface, document verification and JSON-LD receipt generation. | Berk Bahtiyar |
| 2026-12-13 | Complete system testing, customer validation, documentation, test report and tagged GitHub release. | Berk Bahtiyar |

| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |
| Ethereum test network or faucet problems | Medium | Medium | Test the smart contract locally using Remix VM before deploying it to Sepolia. |
| Smart contract and wallet integration errors | Medium | High | Develop a single simple contract and test each function separately. |
| Limited development time because of a single-member team | High | Medium | Prioritize document registration and verification and avoid unnecessary features. |
| Unclear customer requirements | Medium | High | Confirm the customer's needs before implementation and keep the project scope limited. |

Repository: https://github.com/berkbahtiyar/blockchain-document-verification — Confirmed on GitHub 2026-11-24 (public, created 2026-11-24)

## References

1. NIST. FIPS PUB 180-4: Secure Hash Standard. https://csrc.nist.gov/pubs/fips/180-4/upd1/final
2. Ethereum Foundation. Ethereum Networks. https://ethereum.org/en/developers/docs/networks/
3. Solidity Documentation. https://docs.soliditylang.org/
4. MDN Web Docs. SubtleCrypto: digest() method. https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/digest
5. W3C. JSON-LD 1.1. https://www.w3.org/TR/json-ld11/
6. W3C. PROV-O: The PROV Ontology. https://www.w3.org/TR/prov-o/

## Self-assessment

| Part | Weight | Grade | Criteria met |
| --- | --- | --- | --- |
| Team and work | 10% | 81/100 | 10 of 12 |
| Mission | 20% | 100/100 | 7 of 7 |
| Scope | 15% | 100/100 | 8 of 8 |
| Goal | 15% | 100/100 | 7 of 7 |
| Objective | 10% | 100/100 | 3 of 3 |
| Backlog | 20% | 100/100 | 10 of 10 |
| Course-specific | 5% | 100/100 | 1 of 1 |
| Plan and references | 5% | 100/100 | 3 of 3 |
| Overall | 100% | 98.1/100 |  |

### Member grades (Proposal)

Project grade 100 (60%), team grade 81 (20%), individual contribution (20%).

| Member | Student number | Individual | Member grade |
| --- | --- | --- | --- |
| Berk Bahtiyar | 2200001070 | 100 | 96.2 |

