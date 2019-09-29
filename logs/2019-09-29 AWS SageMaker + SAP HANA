
**Cloud AI with SAP HANA and Amazon SageMaker**   
Ryan Peden 31 Aug 2019   
https://www.codeproject.com/Articles/5164081/Cloud-AI-with-SAP-HANA-and-Amazon-SageMaker

【Note】Check the hana client version at https://tools.hana.ondemand.com/#hanatools, e.g. When the ariticle was written, `hanaclient-2.4.151-linux-x64.tar.gz` was available. However when I was trying to install HANA client, only `2.4.155` was available.   

### Code Block

```
mkdir -p ~/SageMaker/downloads/hanaclient
cd ~/SageMaker/downloads
wget --no-cookies \
  --header "Cookie: eula_3_1_agreed=tools.hana.ondemand.com/developer-license-3_1.txt" \
  "https://tools.hana.ondemand.com/additional/hanaclient-2.4.151-linux-x64.tar.gz" \
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
