---
title: "CA2101&#160;: Sp&#233;cifiez le marshaling pour les arguments de cha&#238;ne P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2101&#160;: Sp&#233;cifiez le marshaling pour les arguments de cha&#238;ne P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un membre d'appel de code non managé autorise les appelants dotés d'un niveau de confiance partielle, présente un paramètre de chaîne et ne marshale pas explicitement la chaîne.  
  
## Description de la règle  
 Lorsque vous convertissez le format Unicode au format ANSI, il est possible que tous les caractères Unicode ne puissent pas être représentés dans une page de code ANSI spécifique.  *Le mappage ajusté* essaie de résoudre ce problème en substituant un caractère qui ne peut pas être représenté au profit d'un autre.  L'utilisation de cette fonctionnalité peut induire une faille de sécurité car vous ne pouvez pas contrôler le caractère choisi.  Par exemple, un code malveillant peut créer intentionnellement une chaîne Unicode contenant des caractères non trouvés dans une page de code donnée, qui sont convertis en caractères spéciaux du système de fichiers \(tels que '..' ou '\/'\).  Remarquez également que les vérifications de sécurité concernant les caractères spéciaux se produisent fréquemment avant la conversion de la chaîne au format ANSI.  
  
 Le mappage ajusté constitue la valeur par défaut pour la conversion non managée, WChar en Mbyte.  Sauf désactivation explicite du mappage ajusté, votre code peut présenter une faille de sécurité exploitable du fait de ce problème.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, marshalez explicitement les types de données String.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente une méthode qui viole cette règle, puis indique comment corriger la violation.  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]