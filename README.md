(90% there - confident in the functionality, but sometimes wants to access rhe server even after installation).

Use at your own risk - you have the source code!).

Offline Bitcoin Transaction Verifier

This a PWA (progressive web app) - once 'added to desktop/installed' no internet access is needed unless specifically required to download new data.

This app works in tandem with Coinkite (https://coinkite.com/) Opendime and Satscard to enable secure, private Bitcoin transactions without an internet connection.

Key Features:  
- Conduct face-to-face Bitcoin trades instantly  
- No need for internet connection during the exchange
- Eliminate waiting for on-chain confirmations  
- Verify transaction legitimacy offline

How It Works:

- Pre-download relevant block data (one-time setup)  
At the time of trade:  
- Verify the Bitcoin transaction offline  
- Confirm funds on the Opendime or Sats Card  
- Complete the exchange with confidence  

Perfect for:  
- Private, off-grid transactions  
- Instant peer-to-peer Bitcoin exchanges  
   Situations where internet access is limited or unavailable  

Experience truly trustless, immediate, and untraceable Bitcoin trades. No delays, no trust required, no digital footprint.

Most of this code was written by AI with supervision from Immediate Data Ltd.

**User Guide**  
-   Grab the files.  
-   Serve from https or localhost - this allows you to 'add to home page/install'  
-   Select 'Update Block Hash File'  
      This will download the hashes of any new blocks. First time this will be all of them(!).  
      When complete you will be asked to save the file - using a subdirectory in documents works for me.
-   Find a block that you are interested in (one containing a credit transaction to an opendime or satscard) and download the block. Save it locally.  
   **From here no internet connection is required**
-   Select 'Load Block Hashes' and select the file of hashes you downloaded earlier.  
-   Now select 'Check Block' and select the block file that you downloaded earlier.
      The block will have each transaction verfied, the block verified and then the hash verified. If all these tests are passed then the block has not been tampered with and is genuine.  
-   Now select 'Show Transactions'and enter the address of the wallet you are verifying. The transaction crediting the wallet should be shown.

You now know that the device has been credited with bitcoin, and the device itself will show you that it has not been accessed.

As written the code uses https://ankr.com/ to get blockchain data, but this will eventually be configurable.

