---
title: "ClickOnce Deployment Manifest | Microsoft Docs"
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
  - "ClickOnce, deployment manifests"
  - "deployment manifests [ClickOnce]"
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# ClickOnce Deployment Manifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un manifeste de déploiement est un fichier XML qui décrit un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], y compris l'identification de la version actuelle de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à déployer.  
  
 Les manifestes de déploiement possèdent les éléments et attributs suivants.  
  
|Élément|Description|Attributs|  
|-------------|-----------------|---------------|  
|[Élément \<assembly\>](../deployment/assembly-element-clickonce-deployment.md)|Obligatoire.  Élément de niveau supérieur.|`manifestVersion`|  
|[Élément \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-deployment.md)|Obligatoire.  Identifie le manifeste d'application pour cette application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[Élément \<description\>](../deployment/description-element-clickonce-deployment.md)|Obligatoire.  Identifie les informations de l'application utilisées pour créer la présence d'un shell et l'élément **Ajout\/Suppression de programmes** dans le Panneau de configuration.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[Élément \<deployment\>](../deployment/deployment-element-clickonce-deployment.md)|Facultatif.  Identifie les attributs utilisés pour le déploiement de mises à jour et l'exposition au système.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks\> Element](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)|Obligatoire.  Identifie les versions du .NET Framework pour lesquelles cette application peut s'installer et s'exécuter.|`SupportUrl`|  
|[Élément \<dependency\>](../deployment/dependency-element-clickonce-deployment.md)|Obligatoire.  Identifie la version de l'application à installer pour le déploiement et l'emplacement du manifeste d'application.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity\> Element](../deployment/publisheridentity-element-clickonce-deployment.md)|Requis pour les manifestes signés.  Contient des informations sur l'éditeur qui a signé ce manifeste de déploiement.|`Name`<br /><br /> `issuerKeyHash`|  
|[Élément \<signature\>](../deployment/signature-element-clickonce-deployment.md)|Facultatif.  Contient les informations nécessaires pour signer numériquement ce manifeste de déploiement.|Aucun|  
|[\<customErrorReporting\> Element](../deployment/customerrorreporting-element-clickonce-deployment.md)|Facultatif.  Spécifie un URI à afficher en cas d'erreur.|URI|  
  
## Notes  
 Le fichier manifeste de déploiement identifie le déploiement d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], y compris la version actuelle et d'autres paramètres de déploiement.  Il fait référence au manifeste d'application, qui décrit la version actuelle de l'application et tous les fichiers contenus dans le déploiement.  
  
 Pour plus d'informations, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Emplacement du fichier  
 Le fichier manifeste de déploiement fait référence au manifeste d'application correct pour la version actuelle de l'application.  Quand vous mettez à disposition une nouvelle version d'un déploiement d'application, vous devez mettre à jour le manifeste de déploiement pour faire référence au nouveau manifeste d'application.  
  
 Le fichier manifeste de déploiement doit avoir un nom fort et peut également contenir des certificats pour la validation de l'éditeur.  
  
## Syntaxe du nom de fichier  
 Le nom d'un fichier manifeste de déploiement doit se terminer par l'extension .application.  
  
## Exemples  
 L'exemple de code suivant illustre un manifeste de déploiement.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></asmv1:assembly>  
```  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)