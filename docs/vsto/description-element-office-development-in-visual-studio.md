---
title: "&lt;description&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "description (élément)"
  - "<description> (élément)"
  - "manifestes d’application (développement Office dans Visual Studio), <description> (élément)"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;description&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `description` de l’espace de noms `vstov4`  stocke la description de la solution Office qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.  
  
## Syntaxe  
  
```  
<description>  
</description>  
```  
  
## Éléments et attributs  
 Facultatif. L’élément `description` se trouve dans l’espace de noms `vstov4` . Il contient la description du complément qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.  
  
 L’élément `description` n’a aucun attribut ou élément.  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `description` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  