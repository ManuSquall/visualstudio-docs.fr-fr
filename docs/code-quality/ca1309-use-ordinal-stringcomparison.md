---
title: "CA1309 : Utiliser StringComparison avec la valeur Ordinal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1309 : Utiliser StringComparison avec la valeur Ordinal
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Opération de comparaison de chaînes non linguistique qui n'affecte pas au paramètre <xref:System.StringComparison> la valeur **Ordinal** ou **OrdinalIgnoreCase**.  
  
## Description de la règle  
 De nombreuses opérations de chaîne, dont les plus importantes sont les méthodes <xref:System.String.Compare%2A?displayProperty=fullName> et <xref:System.String.Equals%2A?displayProperty=fullName>, fournissent maintenant une surcharge qui accepte une valeur d'énumération <xref:System.StringComparision?displayProperty=fullName> en tant que paramètre.  
  
 Lorsque vous spécifiez **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, la comparaison de chaînes est non linguistique.  Autrement dit, les fonctionnalités qui sont spécifiques au langage naturel sont ignorées lors de la prise de décisions de comparaison.  Cela signifie les décisions reposent sur de simples comparaisons d'octets et ignorent la casse ou les tables d'équivalences paramétrables par la culture.  En conséquence, en affectant explicitement au paramètre la valeur **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, substituez à la méthode de comparaison de chaînes une surcharge qui accepte l'énumération <xref:System.StringComparison?displayProperty=fullName> en tant que paramètre et spécifiez **Ordinal** ou **OrdinalIgnoreCase**.  Par exemple, remplacez `String.Compare(str1, str2)` par `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle quand la bibliothèque ou l'application est destinée à un parc d'utilisateurs local limité ou lorsque la sémantique de la culture actuelle doit être utilisée.  
  
## Voir aussi  
 [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)   
 [CA1307 : Spécifier StringComparison](../code-quality/ca1307-specify-stringcomparison.md)