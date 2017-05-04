---
title: "&#201;l&#233;ment &lt;postAction&gt; (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes de l’application (développement Office dans Visual Studio), <postAction> (élément)"
  - "<postAction>, élément"
  - "postAction (élément)"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# &#201;l&#233;ment &lt;postAction&gt; (d&#233;veloppement Office dans Visual Studio)
  L’élément `postAction` de l’espace de noms `vstav3`  contient les éléments `entrypoint` et tous les éléments `postActionData` associés à des actions de post\-déploiement, lesquelles s’exécutent après l’installation des solutions Office.  
  
## Syntaxe  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## Éléments et attributs  
 L’élément `postAction` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un seul élément `postAction` défini dans un manifeste de l’application pour chaque action de post\-déploiement.  
  
 L’élément `postAction` ne possède pas d’attributs.  
  
 `postAction` comporte les éléments suivants.  
  
### entryPoint  
 Facultatif. Le rôle de l’élément `entryPoint` dans l’espace de noms `vstav3`  est défini dans [Élément &#60;entryPoint&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### postActionData  
 Facultatif. Le rôle de l’élément `postActionData` dans l’espace de noms `vstav3`  est défini dans [&#60;postActionData&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## Exemple d’action de post\-déploiement  
  
### Description  
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  