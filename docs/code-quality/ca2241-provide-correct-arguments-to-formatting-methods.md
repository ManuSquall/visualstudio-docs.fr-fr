---
title: "CA2241 : Fournissez des arguments corrects aux m&#233;thodes de mise en forme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2241 : Fournissez des arguments corrects aux m&#233;thodes de mise en forme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 L'argument de chaîne `format` passé à une méthode telle que <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> ou <xref:System.String.Format%2A?displayProperty=fullName> ne contient pas un élément de mise en forme qui correspond à chaque argument objet, ou vice versa.  
  
## Description de la règle  
 Les arguments des méthodes comme <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> et <xref:System.String.Format%2A> se composent d'une chaîne de mise en forme suivie par plusieurs instances <xref:System.Object?displayProperty=fullName>.  La chaîne de mise en forme se compose de texte et éléments de format incorporés du formulaire, {index\[,alignment\]\[:formatString\]}. 'index' est un entier de base zéro qui indique l'objet à mettre en forme.  Si un objet n'a pas d'index correspondant dans la chaîne de mise en forme, l'objet est ignoré.  Si l'objet spécifié par 'index' n'existe pas, une <xref:System.FormatException?displayProperty=fullName> est levée au moment de l'exécution.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, fournissez un élément de format pour chaque argument d'objet et un argument d'objet pour chaque élément de format.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente deux violations de la règle.  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]