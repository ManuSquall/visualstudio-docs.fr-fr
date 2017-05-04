---
title: "&lt;friendlyName&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes d’application (développement Office dans Visual Studio), élément <friendlyName>"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;friendlyName&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `friendlyName` de l’espace de noms `vstov4`  stocke le nom qui apparaît dans la liste des programmes installés.  
  
## Syntaxe  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## Éléments et attributs  
 L’élément `friendlyName` se trouve dans l’espace de noms `vstov4` . La valeur apparaît dans la liste des programmes installés sur l’ordinateur, ainsi que dans la boîte de dialogue des compléments VSTO COM des applications Microsoft Office.  
  
 L’élément `friendlyName` n’a aucun attribut ou élément enfant.  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `friendlyName` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  