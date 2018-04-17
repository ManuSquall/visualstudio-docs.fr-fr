---
title: 'CA1308 : Normaliser les chaînes en majuscules | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 979b6d0bbd14d6432ea376622ce61f6329f708fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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