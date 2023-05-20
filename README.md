# SIEMENS-S7-PLCs-attacks
The Siemens industrial control systems architecture consists of Simatic S7 PLCs which communicate with a TIA engineering station and SCADA HMI on one side.In this paper we show that even the latest versions of the devices and protocols are still vulnerable.
Siemens communications overview![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/13b910e1-99bb-4c46-9da6-94338e1edcb7)
S7comms, or Step 7 communications, is a Siemens protocol implemented on an ISO protocol  that is not open and has very tight controls.

The  Simatic line of products includes the “Totally Integrated Automation Portal” (TIA),  which functions as the engineering station, and can also function as an HMI. The TIA (or HMI) and the PLCs communicate over the S7 network protocol. 

The most recent versions of the S7 protocol include cryptographic mechanisms to protect the communication — and most importantly, a cryptographic message integrity code, whose goal is to protect the communication from adversarial manipulation.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/14f2f143-69d3-4382-be0d-e391a018f556)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/7c8fc3ed-315c-4e34-a9a3-a828b5d43c11)

S7 Protocol
 
S7 Protocol, is the backbone of the Siemens communications, its Ethernet implementation relies on ISO TCP (RFC1006) which, by design, is block oriented.
 
Each block is named PDU (Protocol Data Unit), its maximum length depends on the CP and is negotiated during the connection.

S7 Protocol is Function oriented or Command oriented, i.e. each transmission contains a command or a reply to it.
If the size of a command doesn't fit in a PDU, then it must be split across more subsequent PDU.
 
Each command consists of
·         A header.
·         A set of parameters.
·         A parameters data.
·         A data block.
 
The first two elements are always present, the other are optional.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/c1ae93e0-bf8b-48de-bfe7-479814f79e55)

S7 Protocol, ISO TCP and TCP/IP follow the well-known encapsulation rule
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/ac67c9bb-5333-4b97-8020-c6d2d67d5f04)

![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/28c3642f-9863-4650-acd4-49a44d9f1257)

S7 Commands are divided into categories:
Ø  Data Read/Write
Ø  Cyclic Data Read/Write
Ø  Directory info
Ø  System Info
Ø  Blocks move
Ø  PLC Control
Ø  Date and Time
Ø  Security
Ø  Programming
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/333b4303-e60a-4843-8a3b-5dd56d6b773d)

The Partners  can exchange unsolicited data, i.e. once the connection is established, both can send data to the other partner.
his kind of communication often is named Client-Client by Siemens in their manuals.

The peer that requests the connection is named Active Partner, the peer that accepts the connection is named Passive partner.

The communication is performed via FB12/FB13 (S7300) or SFB12/SFB13 (S7400), their symbolic names are BSend/BRecv (Block Send / Block Recv).

An important remark is that : when PLC A calls BSend, BRecv must being call in PLC B in the same time, to complete the transaction.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/909571e4-fe09-4d45-a177-f03f5e1810eb)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/6f666699-d94d-4edc-b1b6-320b92534e6a)

Siemens data format
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/f6c19ea3-4892-4421-8e27-b188433265db)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/e8ad1fea-6093-4a5b-b231-f7f443a0585e)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/7ffae6e6-00f9-4648-a00b-202a07395b76)

The PC  internal data format is LITTLE -Endian

DWORD 0x2F11214C is stored into the PC      
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/b1687ca0-5ff9-4992-826d-33f353030122)

![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/e12dac2a-035c-4ddb-aee0-bd4ff8b30205)

The Siemens theatre
 
In the Siemens communication theatre there are three actors:
1.   The Client
2.   The Server
3.   The Partner (a.k.a. the peer in the classic computer dictionary).
And as in all good theatre companies, they follow their script:
o   The client can only query.
o   The server can only reply.
o   The partners can speak both on their own initiative. 
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/5c80e63c-48db-4c69-8195-2cbf2b86e9ee)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/e5ae7223-eaea-40d8-89c3-26f6f36e4f46)

All three components on the left are Clients, they connect to the internal server of the Communication Processor (CP), and make an S7 Request.
The server replies with a S7 answer telegram.
 
No configuration is needed server side. The server service is automatically handled by the firmware of the CP.
 
The CP can be external such as CP343/CP443 or internal in 3XX-PN or 4XX-PN CPUs, they, however, work in the same way.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/c6eceffe-4d6c-4092-844f-0445f2b97635)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/bade6e4b-3347-44e0-89d2-3263feee513a)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/48ed3fb9-e7f5-43a7-9c98-02242be21f45)

Two different protocol flavours are implemented by Simatic S7 products: 
The older Simatic S7 PLCs implement an S7 flavor that is identified by the protocol number 0x32 (S7comm), 
while the new generation PLCs implement an S7 flavor that is identified by the protocol number 0x72 (S7CommPlus
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/dafa6607-8a02-41e2-9d02-f09f307431a7)
All the operations  ( start/stop , download , read /write) are translated by the TIA software to S7 messages, that are transmitted to the PLC. The PLC acts upon the messages it receives, performs the operations, and responds.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/8bfe2475-7286-4882-af68-6d8bbc2fa610)

The S7 cryptographic protection
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/7fc22488-4244-4818-ab5e-61bf1ac860a6)

The message cryptographic protection mechanism consist of the following modules:

A key exchange protocol, that the two parties (PLC and TIA) use to establish a secret shared key, which we call the session key.

A message integrity protection algorithm, that calculates a MAC (Message Authentication Code) value, based on the session key and the message bytes.

A payload encryption algorithm.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/0134548c-c0f6-44a3-9052-25244e4c95bd)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/36bea0fb-72f1-4f2e-8785-f61390b973b7)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/4b1dd0d1-5b7d-4d4f-ae7e-59594e813ec5)

Message  integrity mechanisms and the key exchange
protocols used by various TIA and S7 PLC firmware versions.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/5a8e4a4e-b6e0-4095-b22c-3041bc9eb2df)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/1c34c0ec-a9cd-4179-bd73-038ac3b5dd6c)
the messages that the TIA and S7-1500 PLCs exchange are integrity
protected by a message authentication code. It is calculated under a (symmetric) secret key,
which we denote by session Key, shared between the PLC and the TIA
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/5daa2cca-585f-4ebb-b11b-90a80f625591)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/bdea1f62-d032-4eab-a240-687238f9965f)

Siemens communications VULNERABILITIES ![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/70bad552-c6a4-4b1d-8fc6-837c16ee51cc)
As the implementations of HMAC-SHA256 used by the TIA is one in which finalize modifies the context though it does not add any fragment, all digests but the first one are not valid HMAC-SHA256 digests. Moreover, the security proofs of HMAC do not hold for this incremental variant of HMAC. In fact, this incremental variant is less secure than HMACSHA256
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/ea3d407e-bd28-4b2c-af0b-455dbf6b8f4e)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/7369ba57-626c-4ea6-bf23-5bbfc60a1832)

![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/7f7831a5-f80e-4942-9f2f-6c51e472b962)

S7 integrity protection in protocol P3
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/ccddff4e-dc02-4986-a220-92a8dfa1f654)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/6bf8eafb-b0da-4d2d-98e3-779b2f96ac7d)
Vulnerability CVE-2019-10929

An attacker in a Man-in-the-Middle position could potentially modify network traffic exchanged on port
102/tcp to PLCs of the SIMATIC S7-1200, SIMATIC S7-1500 and SIMATIC Software Controller CPU
families, due to certain properties in the calculation used for integrity protection.
In order to exploit the vulnerability, an attacker must be able to perform a Man-in-the-Middle attack.
The vulnerability could impact the integrity of the communication.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/37633000-dfec-4e71-a7ca-945e7fd3da4b)

The P2 protocol uses a simplistic key synchronization scheme, which is equivalent to usage  of a list fixed keys in a sequence.
During each new handshake the next key is calculated by both parties.

The  same sequence of keys is used each time a TIA is restarted, regardless of whether it is the same TIA instance or another instance.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/2ea7bf5a-cc90-4bd9-9d05-169b69d96e8e)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/99701174-1c46-4b78-abb6-dfded0d87d22)

In the P3 protocol, Siemens replaced the simplistic P2 key generation process by a more sophisticated challenge-response protocol, that involves elliptic-curve public-key cryptography for the key exchange.
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/3a2fcae4-3d66-4ffb-8f9d-d81a5ecedede)
The P3 key exchange uses one-way group authentication. A PLC of a given model and
firmware version has the necessary private key and is able to successfully decrypt the
KDK, and derive the Session Key. 
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/9c946b85-5e81-4285-854a-611e879002ee)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/a2c804b9-06d6-4ab1-b234-670fa668afbb)
Siemens communications attacks ![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/372f43e9-3698-4ee7-b8d1-49f78ac9847e)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/1d937be4-39f6-4ab8-9c2b-d0c3b690c9c2)
![image](https://github.com/Esamgold/SIEMENS-S7-PLCs-attacks/assets/76063102/0fdfdff5-dccd-4fe4-9e97-0a09dc9637e2)
