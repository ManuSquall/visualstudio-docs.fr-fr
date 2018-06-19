---
title: Manifeste d’Application ClickOnce | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52d5a288444b1e98df75e6748fa31176b27211b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565079"
---
# <a name="clickonce-application-manifest"></a>ClickOnce Application Manifest
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application est un fichier XML qui décrit une application est déployée à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes d’application possèdent les éléments et attributs suivants.  
  
|Élément|Description|Attributs|  
|-------------|-----------------|----------------|  
|[\<assembly > élément](../deployment/assembly-element-clickonce-application.md)|Obligatoire. Élément de niveau supérieur.|`manifestVersion`|  
|[\<assemblyIdentity > élément](../deployment/assemblyidentity-element-clickonce-application.md)|Obligatoire. Identifie l’assembly principal de le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo > élément](../deployment/trustinfo-element-clickonce-application.md)|Identifie les exigences de sécurité de l’application.|Aucun|  
|[\<entryPoint > élément](../deployment/entrypoint-element-clickonce-application.md)|Obligatoire. Identifie le point d’entrée de code application.|`name`|  
|[\<dépendance > élément](../deployment/dependency-element-clickonce-application.md)|Obligatoire. Identifie chaque dépendance requise pour l’exécution de l’application. Identifie éventuellement les assemblys qui doivent être préinstallés.|Aucun|  
|[\<fichier > élément](../deployment/file-element-clickonce-application.md)|Facultatif. Identifie chaque fichier autre qui est utilisé par l’application. Peut inclure les données d’isolation COM (Component Object Model) associées au fichier.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation > élément](../deployment/fileassociation-element-clickonce-application.md)|Facultatif. Identifie une extension de fichier à associer à l’application.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Notes  
 Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichier manifeste d’application identifie une application déployée à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Pour plus d’informations sur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Emplacement du fichier  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application est spécifique à une seule version d’un déploiement. Pour cette raison, ils doivent être stockés séparément des manifestes de déploiement. La convention commune est de les placer dans un sous-répertoire nommé d’après la version associée.  
  
 Le manifeste d’application doit toujours être signé avant le déploiement. Si vous modifiez manuellement un manifeste d’application, vous devez utiliser mage.exe pour signer à nouveau le manifeste d’application, de mettre à jour le manifeste de déploiement et de signer de nouveau le manifeste de déploiement. Pour plus d’informations, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Syntaxe du nom de fichier  
 Le nom d’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichier manifeste d’application doit être le nom complet et l’extension de l’application, telle qu’identifiée dans le `assemblyIdentity` élément, suivi par l’extension .manifest. Par exemple, un manifeste d’application qui fait référence à l’application Example.exe utiliseriez la syntaxe suivante.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre un manifeste d’application pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)