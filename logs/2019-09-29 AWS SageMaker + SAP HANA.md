
# Cloud AI with SAP HANA and Amazon SageMaker   
https://www.codeproject.com/Articles/5164081/Cloud-AI-with-SAP-HANA-and-Amazon-SageMaker
Ryan Peden 31 Aug 2019  

【Note】    
Check the hana client version at https://tools.hana.ondemand.com/#hanatools     
e.g. When the ariticle was written, `hanaclient-2.4.151-linux-x64.tar.gz` was available.    
However when I was trying to install HANA client, only `2.4.155` was available.   

### Code Block

```
mkdir -p ~/SageMaker/downloads/hanaclient
cd ~/SageMaker/downloads
wget --no-cookies \
  --header "Cookie: eula_3_1_agreed=tools.hana.ondemand.com/developer-license-3_1.txt" \
  "https://tools.hana.ondemand.com/additional/hanaclient-2.4.155-linux-x64.tar.gz" \
  -P ~/SageMaker/downloads
tar -xvf ~/SageMaker/downloads/hanaclient-*-linux-x64.tar.gz
rm -f ~/SageMaker/downloads/hanaclient-*-linux-x64.tar.gz
```
### Log
```
sh-4.2$ mkdir -p ~/SageMaker/downloads/hanaclient
sh-4.2$ cd ~/SageMaker/downloads
sh-4.2$ wget --no-cookies \
>   --header "Cookie: eula_3_1_agreed=tools.hana.ondemand.com/developer-license-3_1.txt" \
>   "https://tools.hana.ondemand.com/additional/hanaclient-2.4.155-linux-x64.tar.gz" \
>   -P ~/SageMaker/downloads
--2019-09-29 14:22:36--  https://tools.hana.ondemand.com/additional/hanaclient-2.4.155-linux-x64.tar.gz
Resolving tools.hana.ondemand.com (tools.hana.ondemand.com)... 23.197.157.94
Connecting to tools.hana.ondemand.com (tools.hana.ondemand.com)|23.197.157.94|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 320250885 (305M) [application/x-gzip]
Saving to: ‘/home/ec2-user/SageMaker/downloads/hanaclient-2.4.155-linux-x64.tar.gz’

hanaclient-2.4.155-linux-x64.tar.gz      100%[=================================================================================>] 305.42M   575KB/s    in 9m 39s  

2019-09-29 14:32:16 (540 KB/s) - ‘/home/ec2-user/SageMaker/downloads/hanaclient-2.4.155-linux-x64.tar.gz’ saved [320250885/320250885]

sh-4.2$ tar -xvf ~/SageMaker/downloads/hanaclient-*-linux-x64.tar.gz
client/
client/hdbsetup
client/hdbinst
client/filelist.clientinst
client/client/
client/client/HALMCLI.TGZ
client/client/CLIENTINST.TGZ
client/client/REPOTOOLS.TGZ.lst
client/client/SAPSYSMF.TGZ
client/client/ENVSCRIPT.TGZ
client/client/REPOTOOLS.TGZ
client/client/PYDBAPI.TGZ
client/client/PYDBAPIML.TGZ.lst
client/client/SAPSYSMF.TGZ.lst
client/client/CLIENTINST.TGZ.lst
client/client/InstallParams.xml
client/client/RUBY.TGZ.lst
client/client/JDBC.TGZ.lst
client/client/GOLANG.TGZ
client/client/GOLANG.TGZ.lst
client/client/HANAMLR.TGZ.lst
client/client/NODEJS.TGZ.lst
client/client/manifest
client/client/SQLDBC.TGZ.lst
client/client/ODBC.TGZ.lst
client/client/ODBC.TGZ
client/client/DBCAPI.TGZ.lst
client/client/installcfg.dtd
client/client/ENVSCRIPT.TGZ.lst
client/client/SQLDBC.TGZ
client/client/RUBY.TGZ
client/client/PYDBAPIML.TGZ
client/client/HALMCLI.TGZ.lst
client/client/DBCAPI.TGZ
client/client/PYDBAPI.TGZ.lst
client/client/HANAMLR.TGZ
client/client/JDBC.TGZ
client/client/NODEJS.TGZ
client/instruntime/
client/instruntime/IO.so
client/instruntime/Socket.so
client/instruntime/LibXML.so
client/instruntime/version/
client/instruntime/version/regex.pm
client/instruntime/libSQLDBCHDB.so
client/instruntime/Cwd.so
client/instruntime/Grid.so
client/instruntime/Exporter.pm
client/instruntime/sdbrun
client/instruntime/Encode.so
client/instruntime/libwx_gtk2u-3.0.so.0
client/instruntime/SHA.so
client/instruntime/HiRes.so
client/instruntime/FCGI.so
client/instruntime/constant.pm
client/instruntime/SSLeay.so
client/instruntime/Carp.pm
client/instruntime/lcm_res.tgz
client/instruntime/Dumper.so
client/instruntime/lcm_pm.tgz
client/instruntime/libperl.so
client/instruntime/vars.pm
client/instruntime/libsdbrun.so
client/instruntime/strict.pm
client/instruntime/distcompat/
client/instruntime/distcompat/SSLeay.so
client/instruntime/distcompat/SSH2.so
client/instruntime/Getopt/
client/instruntime/Getopt/Long.pm
client/instruntime/overload.pm
client/instruntime/overloading.pm
client/instruntime/version.pm
client/instruntime/lcm_pm_ext.tgz
client/instruntime/Exporter/
client/instruntime/Exporter/Heavy.pm
client/instruntime/SSH2.so
client/instruntime/Parser.so
client/instruntime/warnings.pm
client/instruntime/warnings/
client/instruntime/warnings/register.pm
client/instruntime/SQLDBC.so
client/instruntime/Base64.so
client/instruntime/Wx.so
client/instruntime/DND.so
client/hdbuninst
client/LABEL.ASC
client/SIGNATURE.SMF
client/licenses/
client/licenses/poco.txt
client/licenses/lz4.txt
client/licenses/intel_bid.txt
client/hdbclientreg
sh-4.2$ rm -f ~/SageMaker/downloads/hanaclient-*-linux-x64.tar.gz
```

### Code block
```
mkdir -p ~/SageMaker/sap/hdbclient

cd ~/SageMaker/downloads/client
./hdbinst --path=/home/ec2-user/SageMaker/sap/hdbclient/

cd ~
rm -Rf ~/SageMaker/downloads/client

source activate tensorflow_p36
pip install /home/ec2-user/SageMaker/sap/hdbclient/hdbcli-*.tar.gz
```

### Log

```
sh-4.2$ mkdir -p ~/SageMaker/sap/hdbclient
sh-4.2$ 
sh-4.2$ cd ~/SageMaker/downloads/client
sh-4.2$ ./hdbinst --path=/home/ec2-user/SageMaker/sap/hdbclient/
SAP HANA Database Client installation kit detected.


SAP HANA Lifecycle Management - Client Installation 2.4.155.1565706773
**********************************************************************



Checking installation...
Preparing package 'Product Manifest'...
Preparing package 'SQLDBC'...
Preparing package 'REPOTOOLS'...
Preparing package 'Python DB API'...
Preparing package 'Python Machine Learning API'...
Preparing package 'ODBC'...
Preparing package 'R Machine Learning API'...
Preparing package 'JDBC'...
Preparing package 'HALM Client'...
Preparing package 'DBCAPI'...
Preparing package 'node.js Client'...
Preparing package 'golang Client'...
Preparing package 'Ruby Client'...
Preparing package 'Environment Script'...
Preparing package 'Client Installer'...
Installing SAP HANA Database Client to /home/ec2-user/SageMaker/sap/hdbclient/...
Installing package 'Product Manifest'...
Installing package 'SQLDBC'...
Installing package 'REPOTOOLS'...
Installing package 'Python DB API'...
Installing package 'Python Machine Learning API'...
Installing package 'ODBC'...
Installing package 'R Machine Learning API'...
Installing package 'JDBC'...
Installing package 'HALM Client'...
Installing package 'DBCAPI'...
Installing package 'node.js Client'...
Installing package 'golang Client'...
Installing package 'Ruby Client'...
Installing package 'Environment Script'...
Installing package 'Client Installer'...
Installation done
Log file written to '/var/tmp/hdb_client_2019-09-29_14.35.10_8690/hdbinst_client.log' on host 'ip-172-16-16-61'.
sh-4.2$ 
sh-4.2$ cd ~
sh-4.2$ rm -Rf ~/SageMaker/downloads/client
sh-4.2$ 
sh-4.2$ source activate tensorflow_p36
(tensorflow_p36) sh-4.2$ pip install /home/ec2-user/SageMaker/sap/hdbclient/hdbcli-*.tar.gz
Processing ./SageMaker/sap/hdbclient/hdbcli-2.4.155.tar.gz
Building wheels for collected packages: hdbcli
  Running setup.py bdist_wheel for hdbcli ... done
  Stored in directory: /home/ec2-user/.cache/pip/wheels/23/fc/ce/e7f2512bbb7b1e96be2d0a8a34d7fb3b1d74f61c42299dac90
Successfully built hdbcli
Installing collected packages: hdbcli
Successfully installed hdbcli-2.4.155
You are using pip version 10.0.1, however version 19.2.3 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

### Code block

```
source activate tensorflow_p36 
pip install /home/ec2-user/SageMaker/sap/hdbclient/hana_ml-*.tar.gz
```

### Log

```
(tensorflow_p36) sh-4.2$ source activate tensorflow_p36 
(tensorflow_p36) sh-4.2$ pip install /home/ec2-user/SageMaker/sap/hdbclient/hana_ml-*.tar.gz
Processing ./SageMaker/sap/hdbclient/hana_ml-1.0.7.tar.gz
Requirement already satisfied: hdbcli in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from hana-ml==1.0.7) (2.4.155)
Requirement already satisfied: numpy in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from hana-ml==1.0.7) (1.16.4)
Requirement already satisfied: pandas in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from hana-ml==1.0.7) (0.24.2)
Collecting pydot (from hana-ml==1.0.7)
  Downloading https://files.pythonhosted.org/packages/33/d1/b1479a770f66d962f545c2101630ce1d5592d90cb4f083d38862e93d16d2/pydot-1.4.1-py2.py3-none-any.whl
Requirement already satisfied: matplotlib in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from hana-ml==1.0.7) (3.0.3)
Requirement already satisfied: pytz>=2011k in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from pandas->hana-ml==1.0.7) (2018.4)
Requirement already satisfied: python-dateutil>=2.5.0 in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from pandas->hana-ml==1.0.7) (2.7.3)
Requirement already satisfied: pyparsing>=2.1.4 in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from pydot->hana-ml==1.0.7) (2.2.0)
Requirement already satisfied: cycler>=0.10 in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from matplotlib->hana-ml==1.0.7) (0.10.0)
Requirement already satisfied: kiwisolver>=1.0.1 in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from matplotlib->hana-ml==1.0.7) (1.0.1)
Requirement already satisfied: six>=1.5 in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from python-dateutil>=2.5.0->pandas->hana-ml==1.0.7) (1.11.0)
Requirement already satisfied: setuptools in ./anaconda3/envs/tensorflow_p36/lib/python3.6/site-packages (from kiwisolver>=1.0.1->matplotlib->hana-ml==1.0.7) (41.0.1)
Building wheels for collected packages: hana-ml
  Running setup.py bdist_wheel for hana-ml ... done
  Stored in directory: /home/ec2-user/.cache/pip/wheels/ba/15/f1/18396eda5df904b63b67e889eb42a7b91c1a27069a65e2e921
Successfully built hana-ml
Installing collected packages: pydot, hana-ml
Successfully installed hana-ml-1.0.7 pydot-1.4.1
You are using pip version 10.0.1, however version 19.2.3 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

