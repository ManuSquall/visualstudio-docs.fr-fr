---
title: "&lt;description&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> element [ClickOnce deployment manifest]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# &lt;description&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie les informations de l'application utilisées pour créer la présence d'un shell et l'élément **Ajouter ou supprimer des programmes** dans le Panneau de configuration.  
  
## Syntaxe  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Éléments et attributs  
 L'élément `description` est obligatoire et se trouve dans l'espace de noms `urn:schemas-microsoft-com:asm.v1`.  Il ne contient pas d'éléments enfants et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`publisher`|Obligatoire.  Identifie la société utilisée pour le positionnement de l'icône dans le menu **Démarrer** de Windows et l'élément **Ajouter ou supprimer des programmes** dans le Panneau de configuration, lorsque le déploiement est configuré pour l'installation.|  
|`product`|Obligatoire.  Identifie le nom de produit complet.  Utilisé comme titre de l'icône installée dans le menu **Démarrer** de Windows.|  
|`suiteName`|Facultatif.  Identifie un sous\-dossier dans le dossier `publisher` dans le menu **Démarrer** de Windows.|  
|`supportUrl`|Facultatif.  Spécifie une URL de support affichée dans l'élément **Ajouter et supprimer des programmes** du Panneau de configuration.  Un raccourci vers cette URL est également créé pour le support des applications dans le menu **Démarrer** de Windows, lorsque le déploiement est configuré pour l'installation.|  
  
## Notes  
 L'élément de description est requis dans toutes les configurations de déploiement.  
  
## Exemple  
 L'exemple de code suivant illustre un élément `description` dans un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus complet fourni pour la rubrique [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)