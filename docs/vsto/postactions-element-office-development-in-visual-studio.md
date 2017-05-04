---
title: "&#201;l&#233;ment &lt;postActions&gt; (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes de l’application (développement Office dans Visual Studio), <postActions> (élément)"
  - "postActions (élément)"
  - "<postActions> (élément)"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &#201;l&#233;ment &lt;postActions&gt; (d&#233;veloppement Office dans Visual Studio)
  L’élément `postActions` de l’espace de noms `vstav3`  contient tous les éléments `postAction` qui décrivent des actions de post\-déploiement, lesquelles s’exécutent après l’installation des solutions Office.  
  
## Syntaxe  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## Éléments et attributs  
 L’élément `postActions` est facultatif et se trouve dans l’espace de noms `vstav3` . Un seul élément `postActions` est défini dans un manifeste de l’application.  
  
 L’élément `postActions` ne possède pas d’attributs.  
  
 `postActions` possède l’élément suivant.  
  
### postAction  
 Facultatif. Le rôle de l’élément `postAction` dans l’espace de noms `vstav3`  est défini dans [Élément &#60;postAction&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## Exemple d’action de post\-déploiement  
  
### Description  
 L’exemple de code suivant illustre l’élément `postActions` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  