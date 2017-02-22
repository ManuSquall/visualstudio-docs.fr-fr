---
title: "CA1308&#160;: Normaliser les cha&#238;nes en majuscules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308&#160;: Normaliser les cha&#238;nes en majuscules
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une opération normalise une chaîne à écrire en minuscules.  
  
## Description de la règle  
 Les chaînes doivent être normalisées en majuscules.  Il existe un petit groupe de caractères qui, en cas de conversion en minuscules, ne peut pas faire un aller\-retour.  Faire un aller\-retour signifie convertir les caractères depuis des paramètres régionaux vers d'autres qui représentent des données caractères différemment, puis récupérer sans perte les caractères d'origine à partir des caractères convertis.  
  
## Comment corriger les violations  
 Modifiez des opérations qui convertissent des chaînes en minuscules afin que les chaînes soient converties en majuscules.  Par exemple, remplacez `String.ToLower(CultureInfo.InvariantCulture)` par `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## Quand supprimer les avertissements  
 Vous pouvez supprimer sans risque un message d'avertissement lorsque vous ne prenez pas de décision de sécurité basée sur le résultat, par exemple, lorsque vous l'affichez dans l'interface utilisateur.  
  
## Voir aussi  
 [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)