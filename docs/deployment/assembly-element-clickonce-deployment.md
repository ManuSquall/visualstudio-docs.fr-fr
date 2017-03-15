---
title: "&lt;assembly&gt; Element (ClickOnce Deployment) | Microsoft Docs"
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
  - "<assembly> element [ClickOnce deployment manifest]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;assembly&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Élément de niveau supérieur du manifeste de déploiement.  
  
## Syntaxe  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Éléments et attributs  
 L'élément `assembly` est l'élément racine et il est obligatoire.  Le premier élément qu'il contient doit être un élément `assemblyIdentity`.  Les éléments de manifeste doivent figurer dans les espaces de noms suivants : `urn:schemas-microsoft-com:asm.v 1`, `urn:schemas-microsoft-com:asm.v 2` et `http://www.w3.org/2000/09/xmldsig #`.  Les éléments enfants de l'assembly doivent également appartenir à ces espaces de noms, par héritage ou par balisage.  
  
 L'élément `assembly` a l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`manifestVersion`|Obligatoire.  Cet attribut doit avoir la valeur `1.0`.|  
  
## Exemple  
 L'exemple de code suivant illustre un élément `assembly` dans un manifeste de déploiement d'une application déployée avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus complet fourni pour la rubrique [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
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
```  
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)