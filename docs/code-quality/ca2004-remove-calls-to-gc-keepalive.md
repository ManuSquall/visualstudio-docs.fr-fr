---
title: "CA2004 : Supprimez les appels à GC. KeepAlive | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Catégorie|Microsoft.Reliability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Utilisation des classes `SafeHandle` mais contiennent toujours des appels à `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Description de la règle  
 Si vous convertissez en `SafeHandle` utilisation, supprimez tous les appels à `GC.KeepAlive` (objet). Dans ce cas, les classes devez pas appeler `GC.KeepAlive`, en supposant qu’elles n’ont pas de finaliseur mais dépendent `SafeHandle` pour terminer le handle du système d’exploitation pour eux.  Bien que le coût de laisser dans un appel à `GC.KeepAlive` peut être négligeable en termes de performances, la perception qui un appel à `GC.KeepAlive` est nécessaire ou suffisant pour résoudre le problème qui ne peut plus exister rend le code plus difficile pour une durée de vie mettre à jour.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimez les appels à `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous pouvez supprimer cet avertissement uniquement si elle n’est pas techniquement correcte convertir `SafeHandle` utilisation dans votre classe.