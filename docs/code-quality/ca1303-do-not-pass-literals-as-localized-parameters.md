---
title: "CA1303 : Ne pas transmettre des litt&#233;raux en tant que param&#232;tres localis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303 : Ne pas transmettre des litt&#233;raux en tant que param&#232;tres localis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode passe un littéral de chaîne en tant que paramètre à un constructeur ou une méthode présent dans la bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et cette chaîne doit être localisable.  
  
 Cet avertissement est déclenché lorsqu'une chaîne littérale est passée comme une valeur à un paramètre ou une propriété et qu'un ou plusieurs des cas suivants se vérifient :  
  
-   L'attribut <xref:System.ComponentModel.LocalizableAttribute> du paramètre ou de la propriété a la valeur true.  
  
-   Le paramètre ou le nom de propriété contient "Text", "Message" ou "Caption".  
  
-   Le nom du paramètre de chaîne passé à une méthode Console.Write ou Console.WriteLine est "value" ou "format".  
  
## Description de la règle  
 Les littéraux de chaîne incorporés au code source sont difficiles à localiser.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée par le biais d'une instance de la classe <xref:System.Resources.ResourceManager>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si la bibliothèque de code n'est pas localisée, ou si la chaîne n'est pas exposée à l'utilisateur final ou à un développeur à l'aide de la bibliothèque de code.  
  
 Les utilisateurs peuvent éliminer le bruit qui interfère avec les méthodes qui ne doivent pas constituer des chaînes localisées passées, soit en renommant le paramètre ou la propriété nommée, soit en marquant ces éléments comme conditionnels.  
  
## Exemple  
 L'exemple suivant présente une méthode qui lève une exception lorsque l'un de ses deux arguments est hors limites.  Pour le premier argument, le constructeur d'exception reçoit une chaîne littérale qui enfreint cette règle.  Pour le second argument, le constructeur reçoit correctement une chaîne récupérée par le biais d'un <xref:System.Resources.ResourceManager>.  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## Voir aussi  
 [Ressources dans des applications de bureau](../Topic/Resources%20in%20Desktop%20Apps.md)