# [ZCash](https://z.cash/) Desktop GUI Wallet - binary release v0.25-beta

This document describes how to install binary release v0.25-beta of the [ZCash](https://z.cash/) 
Desktop GUI Wallet. This release of the ZCash Desktop GUI Wallet is tested with ZCash version 
[v1.0.0-rc1](https://github.com/zcash/zcash/releases/tag/v1.0.0-rc1). 
It is intended to be used in the ZCash test network only - not in production!

![Screenshot](https://github.com/vaklinov/zcash-swing-wallet-ui/raw/master/docs/ZCashWalletSmall.png "Main Window")

## Installing and running the Wallet GUI

1. Downloading the wallet
 
   Download file [ZCashSwingWalletUI.jar](https://github.com/vaklinov/zcash-swing-wallet-ui/releases/download/v0.25-beta/ZCashSwingWalletUI.jar)
   and place it in a folder like `~/Downloads`.
   
2. Verifying the download

   **This step is very important!** To verify that the file `ZCashSwingWalletUI.jar` is an authentic release, you
   need to compute its SHA256 checksum, like this:
   ```
   user@ubuntu:~/Downloads$ sha256sum ZCashSwingWalletUI.jar 
   5042002b1ac2ceabdce04fc2a2a2534315c4ad59f85e7efa7349ad20ec3519ad  ZCashSwingWalletUI.jar
   ```
   **If the resulting checksum is not `5042002b1ac2ceabdce04fc2a2a2534315c4ad59f85e7efa7349ad20ec3519ad` then**
   **something is wrong and you should discard the downloaded wallet!**

3. Installing the downloaded ZCash GUI wallet

  3.1. If you have built ZCash from source code:

   Assuming you have already built from source code [ZCash](https://z.cash/) in directory `/home/user/zcash/src` (for 
   example - this is the typical build dir. for ZCash v1.0.0-rc1) which contains the command line tools `zen-cli` 
   and `zend` you need to take the downloaded file `ZCashSwingWalletUI.jar` and copy it 
   to diretcory `/home/user/zcash/src` (the same dir. that contains `zen-cli` and `zend`). Example copy command:
   ```
   user@ubuntu:~/Downloads$ cp ./ZCashSwingWalletUI.jar /home/user/zcash/src    
   ```
   
  3.2. If you have installed the ZCash [binary packages](https://github.com/zcash/zcash/wiki/Debian-binary-packages)

   The command line tools `zen-cli` and `zend` are placed by the package installer in:
   ```
   /usr/bin/zen-cli
   /usr/bin/zend
   ```
   The ZCash GUI wallet knows how to find them there. You may place the file  `ZCashSwingWalletUI.jar`
   anywhere in your `/home` directory that you find convenient and start it from there.

4. Running the installed ZCash GUI wallet

   Before running the GUI you need to start zend (e.g. `zend --daemon`). The wallet GUI is a Java program packaged 
   as an executable JAR file. It may be run from command line or started from another GUI tool (e.g. file manager). 
   Assuming you have already installed [ZCash](https://z.cash/) and the GUI Wallet `ZCashSwingWalletUI.jar` in 
   directory `/home/user/zcash/src` one way to run it from command line is:
   ```
   user@ubuntu:~/Downloads$ java -jar /home/user/zcash/src/ZCashSwingWalletUI.jar
   ```
   If you are using Ubuntu (or similar ;) Linux you may instead just use the file manager and 
   right-click on the `ZCashSwingWalletUI.jar` file and choose the option "Open with OpenJDK 8 Runtime". 
   This will start the ZCash GUI wallet.



### License
This program is distributed under an [MIT License](https://github.com/vaklinov/zcash-swing-wallet-ui/raw/master/LICENSE).

### Disclaimer
This program is not officially endorsed by or associated with the ZCash project and the ZCash company.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

### Known issues and limitations

1. Issue: the GUI wallet does not work correctly if zend is started with a custom data directory, like:
`zend -datadir=/home/data/whatever` This will be fixed in later versions.
1. Issue: GUI data tables (transactions/addresses etc.) allow copying of data via double click but also allow editing. 
The latter needs to be disabled. 
1. Limitation: The list of transactions does not show all outgoing ones (specifically outgoing Z address 
transactions). This will be addressed when it becomes possible to do so via the ZCash command line tools 
(`zen-cli`). A corresponding issue [#1438](https://github.com/zcash/zcash/issues/1438) has been opened 
for the ZCash developers. 
1. Limitation: The CPU percentage shown to be taken by zend is the average for the entire lifetime of the process. 
This is not very useful. This will be improved in future versions.
