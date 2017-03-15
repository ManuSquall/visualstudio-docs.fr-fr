---
title: "CA1307&#160;: Sp&#233;cifier StringComparison | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1307&#160;: Sp&#233;cifier StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre <xref:System.StringComparison>.  
  
## Description de la règle  
 De nombreuses opérations de chaîne, dont les plus importantes sont les méthodes <xref:System.String.Compare%2A> et <xref:System.String.Equals%2A>, fournissent une surcharge qui accepte une valeur d'énumération <xref:System.StringComparison> en tant que paramètre.  
  
 Toutes les fois qu'il existe une surcharge qui prend un paramètre <xref:System.StringComparison>, elle doit être utilisée à la place d'une surcharge qui n'en prend pas.  En définissant ce paramètre explicitement, votre code devient souvent plus clair et plus facile gérer.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, substituez aux méthodes de comparaison de chaînes des surcharges qui acceptent l'énumération <xref:System.StringComparison> en tant que paramètre.  Par exemple, remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle quand la bibliothèque ou l'application est destinée à un parc d'utilisateurs local limité et ne sera donc pas localisée.  
  
## Voir aussi  
 [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)   
 [CA1309 : Utiliser StringComparison avec la valeur Ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)