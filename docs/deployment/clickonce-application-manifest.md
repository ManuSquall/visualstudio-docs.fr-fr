---
title: "ClickOnce Application Manifest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "application manifests [ClickOnce]"
  - "ClickOnce, application manifests"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# ClickOnce Application Manifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un manifeste d'application de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est un fichier XML qui décrit une application qui est déployée à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 les manifestes d'application de[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ont les éléments et les attributs suivants.  
  
|Élément|Description|Attributs|  
|-------------|-----------------|---------------|  
|[\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)|Obligatoire.  Élément du niveau le plus haut.|`manifestVersion`|  
|[\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)|Obligatoire.  Identifie l'assembly principal de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo\>, élément](../deployment/trustinfo-element-clickonce-application.md)|Identifie la configuration de sécurité requise de l'application.|Aucun|  
|[\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)|Obligatoire.  Identifie le point d'entrée de code d'application.|`name`|  
|[\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)|Obligatoire.  Identifie chaque dépendance requise pour que l'application s'exécute.  Identifie éventuellement les assemblys à préinstaller.|Aucun|  
|[\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|Facultatif.  Identifie chaque fichier, autre que les fichiers d'assembly, utilisé par l'application.  Il peut inclure des données d'isolation COM associées au fichier.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)|Facultatif.  Identifie une extension de fichier à associer à l'application.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Notes  
 Le fichier manifeste de l'application de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identifie une application déployée à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Pour plus d'informations sur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Emplacement du fichier  
 Un manifeste d'application de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est spécifique à une version unique d'un déploiement.  Pour cette raison, ils doivent être enregistrés séparément des manifestes de déploiement.  Il est généralement convenu de les placer dans un sous\-répertoire prenant le nom de la version associée.  
  
 Le manifeste d'application doit toujours être signé avant son déploiement.  Si vous modifiez un manifeste de l'application manuellement, vous devez utiliser mage.exe pour ré\-signer le manifeste de l'application, mettre à jour le manifeste de déploiement, puis ré\-signer le manifeste de déploiement.  Pour plus d'informations, consultez [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Syntaxe des noms de fichier  
 Le nom d'un fichier manifeste de l'application de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] doit être le nom complet et l'extension de l'application comme cela est identifié dans l'élément d' `assemblyIdentity` , suivi de l'extension .manifest.  Par exemple, le manifeste d'une application faisant référence à la solution Exemple.exe doit respecter la syntaxe de nom suivante.  
  
 `example.exe.manifest`  
  
## Exemple  
 L'exemple de code suivant illustre un manifeste d'application pour une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)