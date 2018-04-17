---
title: 'CA2004 : Supprimez les appels à GC. KeepAlive | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d25c42202f7df2214295af4e3d1a448266cfa6cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Category|Microsoft.Reliability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Utilisation des classes `SafeHandle` mais contiennent toujours des appels à `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Description de la règle  
 Si vous convertissez en `SafeHandle` utilisation, supprimez tous les appels à `GC.KeepAlive` (objet). Dans ce cas, les classes devez pas appeler `GC.KeepAlive`, en supposant qu’elles n’ont pas de finaliseur mais dépendent `SafeHandle` pour terminer le handle du système d’exploitation pour eux.  Bien que le coût de laisser dans un appel à `GC.KeepAlive` peut être négligeable en termes de performances, la perception qui un appel à `GC.KeepAlive` est nécessaire ou suffisant pour résoudre le problème qui ne peut plus exister rend le code plus difficile pour une durée de vie mettre à jour.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimez les appels à `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous pouvez supprimer cet avertissement uniquement si elle n’est pas techniquement correcte convertir `SafeHandle` utilisation dans votre classe.