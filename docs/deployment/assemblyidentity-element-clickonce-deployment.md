---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> element [ClickOnce deployment manifest]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie l'assembly principal de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Syntaxe  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Éléments et attributs  
 L'élément `assemblyIdentity` est obligatoire.  Il ne contient pas d'éléments enfants et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Obligatoire.  Identifie le nom explicite du déploiement, à des fins d'information.<br /><br /> Si `name` contient des caractères spéciaux, tels que des guillemets simples ou doubles, l'activation de l'application peut échouer.|  
|`version`|Obligatoire.  Spécifie le numéro de version de l'assembly au format suivant : `major.minor.build.revision`.<br /><br /> Cette valeur doit être incrémentée dans un manifeste mis à jour pour déclencher une mise à jour d'application.|  
|`publicKeyToken`|Obligatoire.  Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage SHA\-1 de la clé publique sous laquelle le manifeste de déploiement est signé.  La clé publique utilisée pour la signature doit être une clé de 2 048 bits ou plus.<br /><br /> Signer un assembly est recommandé, mais reste facultatif. Néanmoins, cet attribut est requis.  Si un assembly n'est pas signé, vous devez copier une valeur d'un assembly auto\-signé ou utiliser une valeur « factice » ne comprenant que des zéros.|  
|`processorArchitecture`|Obligatoire.  Spécifie le processeur.  Les valeurs valides sont `msil` pour tous les processeurs, `x86` pour Windows 32 bits, `IA64` pour Windows 64 bits et `Itanium` pour les processeurs Intel Itanium 64 bits.|  
|`type`|Obligatoire.  Pour la compatibilité descendante avec la technologie d'installation côte à côte Windows.  La seule valeur autorisée est `win32`.|  
  
## Notes  
  
## Exemple  
 L'exemple de code suivant illustre un élément `assemblyIdentity` dans un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus complet fourni pour la rubrique [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md).  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)