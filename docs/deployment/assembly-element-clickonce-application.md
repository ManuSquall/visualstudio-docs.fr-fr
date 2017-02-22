---
title: "&lt;assembly&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> element [ClickOnce application manifest]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Élément de niveau supérieur du manifeste d'application.  
  
## Syntaxe  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Éléments et attributs  
 L'élément `assembly` est l'élément racine et il est obligatoire.  Le premier élément qu'il contient doit être un élément `assemblyIdentity`.  Les éléments du manifeste doivent appartenir à l'un des espaces de noms suivants :  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Les éléments enfants de l'assembly doivent également appartenir à ces espaces de noms, par héritage ou par balisage.  
  
 L'élément `assembly` a l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`manifestVersion`|Obligatoire.  L'attribut `manifestVersion` doit avoir la valeur `1.0`.|  
  
## Exemple  
 L'exemple de code suivant illustre un élément `assembly` dans un manifeste d'application d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus développé fourni dans [Manifeste d'application ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-deployment.md)