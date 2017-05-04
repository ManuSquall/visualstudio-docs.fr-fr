---
title: "&lt;customHostSpecified&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes d’application (développement Office dans Visual Studio), <customHostSpecified> (élément)"
  - "<customHostSpecified> (élément)"
  - "customHostSpecified (élément)"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customHostSpecified&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L'élément `customHostSpecified` indique que cette solution n'est pas une application autonome.  Les solutions Office contiennent des composants hébergés dans des applications Microsoft Office.  
  
## Syntaxe  
  
```  
<customHostSpecified />  
```  
  
## Éléments et attributs  
 L'élément `customHostSpecified` est obligatoire pour les solutions Office.  Cet élément se trouve dans l'espace de noms `co.v1` et spécifie que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé et que ce n'est pas une application autonome.  
  
 Cet élément est un enfant du premier élément `<entrypoint>` du manifeste d'application.  Il ne peut pas y avoir d'autre élément enfant dans cet élément `<entrypoint>` ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] retournera une erreur de validation pendant l'installation.  
  
 Cet élément n'a pas d'attributs et aucun élément enfant.  
  
## Exemple  
 L'exemple de code suivant illustre l'élément d' `customHostSpecified` dans un manifeste d'application pour une solution Office.  Cet exemple de code fait partie d'un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  