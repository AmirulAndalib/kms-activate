# kms-activate
Microsoft Windows/Office 一键激活工具，基于kms.jm33.me的KMS服务器

## supported versions

- Windows 10 Professional
- Windows 10 Enterprise
- Windows 8.1 Professional
- Windows 8.1 Enterprise
- Windows 7 Professional
- Windows 7 Enterprise
- Windows Server 2016 Standard
- Windows Server 2016 Datacenter
- Windows Server 2012 R2 Server Standard
- Windows Server 2012 R2 Datacenter
- Windows Server 2008 R2 Standard
- Windows Server 2008 R2 Enterprise
- Office 2010, 2013, 2016, 2019

## Office Deployment Tool

you can use [Office Deployment Tool](https://www.microsoft.com/en-us/download/details.aspx?id=49117) to download and install Office (VOL) from Microsoft

### modify configuration XML

upon successful extraction, you will see some XML files under office deployment directory,
the one we care about is `configuration-Office2019Enterprise.xml`:

```xml
<Configuration>

  <Add OfficeClientEdition="64" Channel="PerpetualVL2019">
    <Product ID="ProPlus2019Volume">
      <Language ID="en-us" />
    </Product>
    <Product ID="VisioPro2019Volume">
      <Language ID="en-us" />
    </Product>
    <Product ID="ProjectPro2019Volume">
      <Language ID="en-us" />
    </Product>
  </Add>

  <!--  <RemoveMSI All="True" /> -->

  <!--  <Display Level="None" AcceptEULA="TRUE" />  -->

  <!--  <Property Name="AUTOACTIVATE" Value="1" />  -->
</Configuration>
```

comment out the products you don't need, then save a copy as `office.xml`

### how to install

open a powershell window in current directory

```powershell
# download from Microsoft
.\setup.exe /download office.xml
# install when you have finished downloading
.\setup.exe /configure office.xml
```

## NOTE:

- KMS activation requires a working internet connection, and `kms.jm33.me` or your custom KMS server must be reachable
- Change KMS server if activation keeps failing
- Check `Show debug info` to view log
- Make sure kms server is reachable, and is present in your slmgr.vbs
- Office 2019 Vol is recommended
- Download from [here](https://github.com/jm33-m0/kms-activate/releases)

![screenshot](/img/win-activate.JPG)
