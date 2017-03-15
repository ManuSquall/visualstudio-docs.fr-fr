---
title: "&lt;Schedules&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> (élément du programme d'amorçage)"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# &lt;Schedules&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément `Schedules` contient des éléments `Schedule` qui définissent les heures spécifiques d'exécution des commandes définies par l'élément `Command`.  
  
## Syntaxe  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Éléments et attributs  
 L'élément `Schedules` est un enfant de l'élément `Product`.  Chaque élément `Product` ne peut avoir qu'un seul élément `Schedules`.  L'élément `Schedules` ne contient pas d'attributs.  
  
## Schedule  
 L'élément `Schedule` est un enfant de l'élément `Schedules`.  Un élément `Schedules` doit avoir au moins un élément `Schedule`.  
  
 `Schedule` possède l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Obligatoire.  Nom de l'élément de planification.  Il correspond à la propriété `ScheduleName` de l'élément `Command`.  Lorsqu'un élément `Command` référence la planification nommée, il n'est exécuté qu'à l'heure indiquée par cet élément `Schedule`.  Les planifications peuvent également être associées aux éléments `FailIf` et `BypassIf` qui limitent l'exécution de ces tests conditionnels à la planification spécifiée.  Pour plus d'informations, consultez [\<Commands\>, élément](../deployment/commands-element-bootstrapper.md).|  
  
 Un élément `Schedule` donné ne peut avoir qu'un seul des enfants suivants.  
  
## BuildList  
 L'élément `BuildList` indique au programme d'installation d'exécuter une commande immédiatement après le démarrage de l'application d'amorçage.  
  
## BeforePackage  
 L'élément `BeforePackage` indique au programme d'installation d'exécuter une commande avant l'installation du package spécifié.  
  
## AfterPackage  
 L'élément `AfterPackage` indique au programme d'installation d'exécuter une commande après l'installation du package spécifié.  
  
## Voir aussi  
 [\<Product\>, élément](../deployment/product-element-bootstrapper.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)