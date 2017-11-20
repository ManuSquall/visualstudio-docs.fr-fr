---
title: "CA1809 : Évitez le surplus de variables locales | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a96616d1ee0f7c63e8f36f56a18f234fa27a173
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809 : Évitez le surplus de variables locales
|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un membre contient plus de 64 variables locales, certains d'entre eux peuvent être généré par le compilateur.  
  
## <a name="rule-description"></a>Description de la règle  
 Une optimisation des performances courante consiste à stocker une valeur dans un Registre de processeur au lieu d’en mémoire, ce qui est appelé *enregistrement* la valeur. Le common language runtime considère que jusqu'à 64 variables locales pour l’enregistrement. Les variables qui ne sont pas enregistrées sont placées sur la pile et doivent être déplacées dans un Registre avant toute manipulation. Pour autoriser le risque que toutes les variables locales obtenir les chances d’enregistrement, limiter le nombre de variables locales à 64.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, refactorisez l’implémentation pour utiliser pas plus de 64 variables locales.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle, ou pour désactiver la règle, si les performances ne sont pas un problème.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)