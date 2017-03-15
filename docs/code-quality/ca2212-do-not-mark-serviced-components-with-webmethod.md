---
title: "CA2212&#160;: Ne marquez pas les composants pris en charge avec WebMethod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2212&#160;: Ne marquez pas les composants pris en charge avec WebMethod
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode dans un type qui hérite de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> est marquée avec <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Description de la règle  
 <xref:System.Web.Services.WebMethodAttribute> s'applique aux méthodes présentes dans un service Web XML créé en utilisant ASP.NET ; il permet l'appel à cette méthode depuis des clients Web distants.  La méthode et la classe doivent être publiques et s'exécuter dans une application Web ASP.NET.  Les types <xref:System.EnterpriseServices.ServicedComponent> sont hébergés par les applications COM\+ et peuvent utiliser des services COM\+.  <xref:System.Web.Services.WebMethodAttribute> n'est pas appliqué aux types <xref:System.EnterpriseServices.ServicedComponent> parce qu'ils ne sont pas prévus pour les mêmes scénarios.  Spécifiquement, l'ajout de l'attribut à la méthode <xref:System.EnterpriseServices.ServicedComponent> ne permet pas d'appeler celle\-ci depuis des clients Web distants.  Sachant que <xref:System.Web.Services.WebMethodAttribute> et une méthode <xref:System.EnterpriseServices.ServicedComponent> ont des comportements incompatibles et des exigences en matière de contexte et de flux de transactions, le comportement de la méthode est incorrect dans certains scénarios.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez l'attribut de la méthode <xref:System.EnterpriseServices.ServicedComponent>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Aucun scénario ne permet de combiner ces éléments de manière correcte.  
  
## Voir aussi  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>