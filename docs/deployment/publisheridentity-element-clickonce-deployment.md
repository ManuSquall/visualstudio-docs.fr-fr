---
title: "&lt;publisherIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
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
  - "publisherIdentity Element [ClickOnce deployment manifest], introduction"
  - "required element for signed manifests [ClickOnce], publisherIdentity Element"
  - "publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;publisherIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient les informations relatives à l'éditeur qui a signé ce manifeste de déploiement.  
  
## Syntaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Éléments et attributs  
 L'élément `publisherIdentity` est requis pour les manifestes signés.  Le tableau suivant présente les attributs pris en charge par l'élément `publisherIdentity`.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Obligatoire.  Décrit l'identité du tiers qui a publié cette application.|  
|`issuerKeyHash`|Obligatoire.  Contient le hachage SHA\-1 de la clé publique de l'émetteur du certificat.|  
  
#### Paramètres  
  
## Valeur de propriété\/valeur de retour  
  
## Exceptions  
  
## Notes  
  
## Configuration requise  
  
## Sous\-titre