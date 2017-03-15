---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "<assemblyIdentity> element [ClickOnce application manifest]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie l'application déployée dans un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Syntaxe  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Éléments et attributs  
 L'élément `assemblyIdentity` est obligatoire.  Il ne contient pas d'éléments enfants et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Obligatoire.  Identifie le nom de l'application.<br /><br /> Si `Name` contient des caractères spéciaux, tels que des guillemets simples ou doubles, l'activation de l'application peut échouer.|  
|`Version`|Obligatoire.  Spécifie le numéro de version de l'application, au format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Facultatif.  Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage `SHA-1` de la clé publique sous laquelle l'application ou l'assembly est signé.  La clé publique utilisée pour la signature du catalogue doit être une clé de 2 048 bits ou plus.<br /><br /> Signer un assembly est recommandé, mais reste facultatif. Néanmoins, cet attribut est requis.  Si un assembly n'est pas signé, vous devez copier une valeur d'un assembly auto\-signé ou utiliser une valeur « factice » ne comprenant que des zéros.|  
|`processorArchitecture`|Obligatoire.  Spécifie le processeur.  Les valeurs valides sont `msil` pour tous les processeurs, `x86` pour Windows 32 bits, `IA64` pour Windows 64 bits et `Itanium` pour les processeurs Intel Itanium 64 bits.|  
|`language`|Obligatoire.  Identifie les codes de la langue de l'assembly, en deux parties \(par exemple, `fr-FR`\).  Cet élément figure dans l'espace de noms `asmv2`.  S'il n'est pas spécifié, il a par défaut une valeur `neutre`.|  
  
## Exemples  
  
### Description  
 L'exemple de code suivant illustre un élément `assemblyIdentity` dans un manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus développé fourni dans [Manifeste d'application ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### Code  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-deployment.md)