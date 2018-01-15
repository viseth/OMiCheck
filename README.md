# OMiCheck: Generate a HTML report about the main component of an OMi distributed deployment. Optionnaly the report can be sent by email
OMiCheck HTML report is built based on OMi CLIs, collected data are then computed to give this report

[![MIT license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/vi7Ch/Test/LICENSE)
[![built with Groovy2.8](https://img.shields.io/badge/built%20with-Groovy-red.svg)](http://www.groovy-lang.org)
[![built with Java8](https://img.shields.io/badge/built%20with-Java-green.svg)](https://www.java.com/en/)

> **DISCLAIMER**
    THIS SOFTWARE IS PROVIDED "AS IS" AND ANY EXPRESSED OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
    HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


### Version: 0.1 - initial release 17/09/2017 - Viseth Chaing

Current supported environment: OMi Windows / Oracle DB 

> **Deployment in OMi context** 
- Download the OMiCheck.jar and config.cfg files. 
- Put them in one OMi DPS management servers in a safe directory. 
- Modify according to your OMi environment the default config.cfg . 
- Use a scheduler to execute this jar file. (advice: do not use OMi Scheduled Tasks)


### Manual Usage:
The default named 'config.cfg' file in the current directory is used and a 'logs' directory is created with the logfile 

```bash
java -jar OMiCheck.jar
```


To encrypt the password (database pwd), copy/paste the output to the config.cfg file in place of the 'pwd' field

```bash
java -jar -DpwdEncrypt=<myNewPwd> OMiCheck.jar
``` 

### Note:
**Required INPUT files**
- A CONFIG file named 'config.cfg' with correct info inside


**OUTPUT files**
- A HTML file that contains all OMi infra sanity checks.
- Logfiles: this tool logs its events in a logfile with the below caracteristics: 
```bash
        - LogLevel: INFO, ERROR, DEBUG
        - LogSize: 10MB
        - LogRotate: 5 files
        - Directory of the logfile: 'logs' 
        - Name: 'OMiCheck.log'

To turn debugging mode so that debugging lines will appear in the logfile:
java -Dapp.env=DEBUG OMiCheck.jar

```
A good practice would be to generate and check this HTML report every morning.

