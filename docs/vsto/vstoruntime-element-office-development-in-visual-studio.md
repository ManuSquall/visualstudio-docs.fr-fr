---
title: "&lt;vstoRuntime&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes d’application (développement Office dans Visual Studio), élément <vstoRuntime>"
  - "<vstoRuntime>, élément"
  - "vstoRuntime (élément)"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# &lt;vstoRuntime&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `vstoRuntime` de l’espace de noms `vstav3`  contient une version prise en charge du runtime Visual Studio Tools pour Office pour une solution Office spécifique.  
  
## Syntaxe  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## Éléments et attributs  
 L’élément `vstoRuntime` est obligatoire et se trouve dans l’espace de noms `vstav3` . Si une solution Office prend en charge deux versions du runtime Visual Studio Tools pour Office, il existe deux éléments `vstoRuntime` dans le manifeste de l’application.  
  
 L’élément `vstoRuntime` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`release`|Obligatoire. Version mise en production du runtime de Visual Studio Tools pour Office.|  
|`version`|Obligatoire. Numéro de version du runtime de Visual Studio Tools pour Office.|  
|`supportUrl`|Facultatif. Lien vers l’emplacement d’installation du runtime de Visual Studio Tools pour Office.|  
  
 `vstoRuntime` ne comporte aucun élément.  
  
## Exemple  
 L’exemple de code suivant illustre l’élément `vstoRuntime` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  