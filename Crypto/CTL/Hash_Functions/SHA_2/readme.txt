RVC-CAL Implementation of SHA-2 (FIPS-180-3)

**********************************************************

Junaid Jameel Ahmad @ Uni-Konstanz

Last modified: 25.09.2011

**********************************************************

Secure Hash Algorithms (SHA-2) has been implemented by following NIST's FIPS-180-3 
and is composed of the following files.

== Basic FUs ==

All basic FUs were written to be compliant with the subset of RVC-CAL supported by Orcc.

-- Common Kernel FUs used--

Preprocessor64.cal
TruncateHash.cal

Note: These FUs are located under package CTL.Hash_Functions.common.

-- Utility FUs used--

Smaller2Bigger.cal

Note: Utilities are located under package CTL.Utilities.Other.

== SHA-2 FU network ==

Top_SHA_224.xdf
Top_SHA_256.xdf

Note: SHA-384 and SHA-512 are not yet implemented because of the lack of big integers support in Orcc. 
They will be implemented after implementing a library for BigIntegers in CAL.
