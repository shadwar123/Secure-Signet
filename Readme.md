<a name="readme-top"></a>


<!-- PROJECT LOGO -->
<br />
<div align="center">


  <p align="center">
    A Student Document Management System based on Ethereum Blockchain
    
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About the project</a></li>
    <li><a href="#features">Features</a></li>
    <li>
      <a href="#architecture">Architecture</a>
      <ul>
        <li><a href="#issuer-workflow-process">Issuer workflow process</a></li>
        <li><a href="#verifier-workflow-process">Verifier workflow process</a></li>
        <li><a href="#use-case-diagrams">Use-case diagrams</a></li>
      </ul>
    </li>
    <li><a href="#technologies-used">Technologies used</a></li>
    <li><a href="#local-setup">Local Setup</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project


Etherdocs is a project that aims to implement an efficient anti-forgery mechanism for academic documents, such as mark sheets, transcripts, diplomas, and other certificates. The goal is to ensure the authenticity of academic documents, reducing the incidence of counterfeit certificates, and saving time and financial resources for all parties involved in document verification.

The solution proposed by Etherdocs revolves around three roles or entities: **an Issuer, a Verifier, and a Student**. 
* The issuer is the authority that creates and issues the electronic version of the certificate, eg: A university issuing graduating certificates
* Verifier is the potential employer or any person who wants to verify the authenticity of the certificate provided by the student, eg: A potential employer doing background check. 
* Finally, the student is the recipient of the certificate and can only view the documents issued to him.

 Etherdocs is a project that provides an efficient anti-forgery mechanism for academic documents. By using a combination of blockchain, IPFS, and hash functions, the authenticity of the certificate can be ensured, reducing the incidence of counterfeit certificates and saving time and financial resources for all parties involved in document verification.
 
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Features

- **Security:** By using blockchain, IPFS, and hash functions, Etherdocs provides a highly secure platform for storing and verifying academic documents. The blockchain is tamper-proof and immutable, ensuring that the data stored on it cannot be modified or deleted. The use of hash functions ensures that any modification to the document will be detected, making it difficult for counterfeit certificates to be created.
- **Efficiency:** Etherdocs streamlines the process of verifying academic documents, saving time and resources for all parties involved. Verifiers can easily access the certificates and compare the hash values, eliminating the need for manual verification.
- **Accessibility:** Etherdocs makes it easy for students to access and share their academic documents. The use of IPFS allows for quick and easy access to the documents, while the UUID ensures that the documents are easily identifiable and verifiable.
- **Transparency:** The use of blockchain ensures transparency and accountability in the issuance and verification of academic documents. All data related to the certificate and the IPFS link are stored on the blockchain, providing a transparent and auditable record of the entire process.
- **Universality:** Etherdocs can be used by any educational institution, making it a universal solution for ensuring the authenticity of academic documents. The platform can also be used by potential employers, government agencies, or any organization that needs to verify the authenticity of academic documents.

The Etherdocs project is needed because the current system of issuing and verifying academic documents is prone to fraud and counterfeiting. Without an efficient anti-forgery mechanism, it is difficult to ensure the authenticity of academic documents, leading to wasted time and resources for all parties involved. Etherdocs provides a secure, efficient, and transparent solution for verifying academic documents, ensuring that the information on the certificate is accurate and trustworthy.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Architecture 


### Issuer workflow process

- The below diagram shows the overview of the issuer part of system.

![image](https://user-images.githubusercontent.com/56788568/231941576-ab87de05-b081-42b0-b569-f5e615c6947a.png)

1. Issuer submits raw doc  and user's blockchain address
2. Send raw document to Node server 
3. Generation of UUID and QR
Generate UUID , add UUID to document
 Calculate hash of document with doc path
4. Upload doc with with UUID to IPFS
5. React receives IPFS link & hash value of doc from Node server
6. Store hash value, issuer address, user address and IPFS link
7. React app returns a response: hash value, issuer and user address, IPFS link

### Verifier workflow process

- The below diagram shows the overview of the verifier part of system.

![image](https://user-images.githubusercontent.com/56788568/231941877-eb61e3ad-06c7-4e1c-8652-ae37590accf2.png)

0. The student has sent a digital document with a QR code, UUID, issuer name, user address, and user's name.
1. Find the authentic address of the issuer.
2. Enter the document with the QR code, UUID, issuer address, user address, and user name.
3. Pass the document to the node server.
4. Compute the hash value of the document entered by the verifier.
5. Return the hash value.
6. Send the UUID, hash value, issuer address, user address, and user name to the blockchain for verification.
7. Execute the smart contract for verification by matching the UUID associated with the user's address and name and the hash with the verifier-provided details.
8. Return the result of verification to the React App.
9. Return the verification result to the verifier.

### Use-case diagrams

- The below are use-case diagrams of Issuer, Verifier and User(Student)

![image](https://user-images.githubusercontent.com/56788568/231942409-48843d21-7ffe-436b-91b2-350b8588f00b.png)

![image](https://user-images.githubusercontent.com/56788568/231942481-18024564-9c8a-4de5-81c1-3bf7f18d2cf3.png)

![image](https://user-images.githubusercontent.com/56788568/231942572-55d21117-059a-4aa0-b506-4cd6f67ce25d.png)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Corner-cases

In the event of a human error while issuing a certificate, the issuer can use the invalidate button to invalidate the certificate. This will revoke the certificate's validity and remove it from the blockchain, ensuring that it cannot be used for verification.

The invalidate button can only be accessed by the issuer and is not visible to the student or verifier. This ensures that the issuer has complete control over the validity of the certificates they issue and can take action to correct any errors or revoke certificates that have been issued in error.

By providing a mechanism for revoking certificates, the Etherdocs system ensures the integrity of the certification process and reduces the risk of fraudulent or erroneous certificates being used for verification.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Technologies Used

- Workflow and Architecture Design
  - Excalidraw • Draw.io
- Frontend
  - React.js and related packages
  - CSS and related packages
- Blockchain network: Ethereum
- Smart contracts are written in **Solidity** programming language
- Smart contracts compilation and deployment to test network was done using **Hardhat**
- Blockchain wallet used: **MetaMask** 
- Javascript library to communicate with blockchain: **Ethers.js**
- **IPFS Desktop** for interacting with IPFS without using terminal

<p align="right">(<a href="#readme-top">back to top</a>)</p>

