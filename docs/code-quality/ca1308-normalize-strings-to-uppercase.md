---
title: "CA1308 : Normaliser les chaînes en majuscules | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9064ca9861f609499971b9f5188f5b0006458c15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308 : Normaliser les chaînes en majuscules
|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Category|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une opération normalise une chaîne en minuscules.  
  
## <a name="rule-description"></a>Description de la règle  
 Les chaînes doivent être normalisées en majuscules. Un petit groupe de caractères, lorsqu’ils sont convertis en minuscules, ne peut pas faire un aller-retour. Pour faire un aller-retour signifie convertir les caractères à partir des paramètres régionaux pour les autres paramètres régionaux qui représente des données caractères différemment, puis à précisément récupérer les caractères d’origine à partir des caractères convertis.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez les opérations qui convertissent des chaînes en minuscules afin que les chaînes sont converties en majuscules à la place. Par exemple, remplacez `String.ToLower(CultureInfo.InvariantCulture)` à `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un message d’avertissement lorsque vous n’effectuez pas la décision de sécurité basée sur le résultat (par exemple, lorsque vous l’affichez dans l’interface utilisateur).  
  
## <a name="see-also"></a>Voir aussi  
 [Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)