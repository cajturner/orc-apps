RVC-CAL Implementation of DES (FIPS 46-3)

**********************************************************

Junaid Jameel Ahmad, Shujun Li @ Uni-Konstanz

Last modified on 22 October, 2011

**********************************************************

This RVC-CAL implementation of DES (FIPS 46-3) is composed of the following files.
The naming of cal files follow the terms used in FIPS 46-3.

The test vectors and golden responses are taken from FIPS 46-3.

Since the DES has a number of bit level operations (permutations, selection function, Key scheduling, etc.), 
all the operations are written to manipulate bit streams rather than byte streams. 
Therefore, both (plain/cipher) text and key are transformed into 
bit stream as they enter encipher / decipher and later transformed back into byte stream for output.

The bit order is big-endian because the FIPS 46-3 uses this endianness.
This endianness is also more natural for humans to read the blocks, half blocks and bytes involved.

To support parallel processing of multiple blocks, the output of some FUs is expanded to include the round number. 

Since DES is a Feistel cipher, the RVC-CAL implementation of DES was built on top of a Feistel network.
This Feistel network may be reused to build other Feistel ciphers very easily.

== Basic FUs ==

All basic FUs were written to be compliant with the subset of RVC-CAL supported by Orcc.

-- Common Kernel FUs for both DES encipher and decipher --

DES.DES_KS.cal
DES.DES_Core.xdf
DES.DES_IP.cal
DES.DES_InvIP.cal
DES.DES_f.xdf
DES.DES_f_E.cal
DES.DES_f_P.cal
DES.DES_f_XOR.cal
DES.DES_f_SBoxes.xdf
DES.DES_f_S1.cal
DES.DES_f_S2.cal
DES.DES_f_S3.cal
DES.DES_f_S4.cal
DES.DES_f_S5.cal
DES.DES_f_S6.cal
DES.DES_f_S7.cal
DES.DES_f_S8.cal
Feistel_Networks.Feistel.xdf
Feistel_Networks.Feistel_Manager.cal

-- Utility FUs used in both DES encipher and decipher --

Utilities.Other.Any2Bits.cal
Utilities.Other.Bits2Any.cal
Utilities.Other.Mux2.cal
Utilities.Other.Mux8.cal
Utilities.Other.Demux2.cal
Utilities.Other.Demux8.cal
Utilities.Other.XOR_1b.cal

== DES encipher and decipher as FU networks ==

-- ECB mode --

DES_Encipher.xdf
DES_Decipher.xdf

-- CBC mode --

DES_CBC_Encipher.xdf
DES_CBC_Decipher.xdf

-- 8-bit CFB mode --

DES_CFB8_Encipher.xdf
DES_CFB8_Decipher.xdf

-- 64-bit CFB mode --

DES_CFB64_Encipher.xdf
DES_CFB64_Decipher.xdf

-- OFB mode --

DES_OFB_Cipher.xdf (encipher/decipher)

-- CTR mode --

DES_CTR_Cipher.xdf: DES encipher/decipher

Note: CBC, CFB, OFB and CTR modes have external dependencies on the CAL files under package CTL.Block_Ciphers.Modes.
