---
title: 'CA1900 : Les champs de type valeur doivent être portables | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 669f52b3255559dec2ac90eea90356c2bb886c9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900 : Les champs de type valeur doivent être portables
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Category|Microsoft.Portability|  
|Modification avec rupture|Avec rupture - Si le champ peut être visible à l’extérieur de l’assembly.<br /><br /> Sans rupture - Si le champ n’est pas visible à l’extérieur de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Cette règle vérifie que les structures déclarées avec une disposition explicite seront aligneront correctement lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 64 bits. IA-64 n’autorise pas les accès mémoire non alignés et le processus se bloquera si cette violation n’est pas résolue.  
  
## <a name="rule-description"></a>Description de la règle  
 Structures qui ont une disposition explicite qui contient des champs non alignés provoquent des incidents sur les systèmes d’exploitation 64 bits.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Tous les champs qui sont plus petits que 8 octets doivent avoir les décalages qui sont un multiple de leur taille et les champs qui sont de 8 octets ou plus doivent avoir des offsets qui sont un multiple de 8. Une autre solution consiste à utiliser `LayoutKind.Sequential` au lieu de `LayoutKind.Explicit`, si elle est raisonnable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Cet avertissement doit être supprimé uniquement si elle se produit par erreur.