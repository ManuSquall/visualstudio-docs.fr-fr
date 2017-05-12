---
title: "&lt;postActionData&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "<postActionData>, élément"
  - "manifestes d’application (développement Office dans Visual Studio), élément <postActionData>"
  - "postActionData, élément"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActionData&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `postActionData` de l’espace de noms `vstav3`  spécifie les données associées aux actions de post\-déploiement qui s’exécutent après l’installation des solutions Office.  
  
## Syntaxe  
  
```  
<postActionData>  
</postActionData>  
```  
  
## Éléments et attributs  
 L’élément `postActionData` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un élément `postActionData` défini dans un manifeste de l’application pour chaque action de post\-déploiement.  
  
 L’élément `postActions` n’a pas d’attributs.  
  
 `postActions` n’a aucun élément enfant.  
  
## Exemple d’action de post\-déploiement  
  
### Description  
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  