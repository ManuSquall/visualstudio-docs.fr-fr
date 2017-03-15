---
title: "CA1059&#160;: Les membres ne doivent pas exposer certains types concrets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1059&#160;: Les membres ne doivent pas exposer certains types concrets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un membre visible de l'extérieur est un certain type concret ou expose certains types concrets par l'intermédiaire de l'un de ses paramètres ou de la valeur de retour.  Cette règle indique actuellement l'exposition des types concrets suivants :  
  
-   Type dérivé de <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## Description de la règle  
 Un type concret est un type qui présente une implémentation complète et, par conséquent, peut être instancié.  Pour permettre une utilisation généralisée du membre, remplacez le type concret par l'interface suggérée.  Cela permet au membre d'accepter tout type qui implémente l'interface ou d'être utilisé lorsqu'un type qui implémente l'interface est attendu.  
  
 Le tableau suivant répertorie les types concrets ciblés et leurs remplacements suggérés.  
  
|Type concret|Replacement|  
|------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> L'utilisation de l'interface découple le membre d'une implémentation spécifique d'une source de données XML.|  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le type concret par l'interface suggérée.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un message de cette règle si les fonctionnalités spécifiques fournies par le type concret sont requises.  
  
## Règles connexes  
 [CA1011 : Si possible, transmettez les types de base en tant que paramètres](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)