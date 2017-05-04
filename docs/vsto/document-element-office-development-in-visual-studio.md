---
title: "&lt;document&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "document (élément)"
  - "manifestes d’application (développement Office dans Visual Studio), <document> (élément)"
  - "<document>, élément"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;document&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L'élément `document` de l'espace de noms `vstov4`  stocke des informations spécifiques à la personnalisation pour des personnalisations au niveau du document.  
  
## Syntaxe  
  
```  
<document solutionId />  
```  
  
## Éléments et attributs  
 Obligatoire uniquement pour les personnalisations au niveau du document.  L'élément `document` figure dans l'espace de noms `vstov4` .  L'élément `document` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`solutionId`|Obligatoire.  GUID utilisé par le moment de l'exécution Visual Studio Tools pour Office pour identifier une solution au niveau de le document.  Cette valeur est stockée en tant que propriété \_AssemblyLocation personnalisée du document.  Pour plus d'informations, consultez [Vue d'ensemble des propriétés de document personnalisées](../vsto/custom-document-properties-overview.md).|  
  
 `document` ne possède aucun élément enfant.  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L'exemple de code suivant illustre l'élément `document` pour une solution Office au niveau du document déployée à l'aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Cet exemple de code fait partie d'un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  