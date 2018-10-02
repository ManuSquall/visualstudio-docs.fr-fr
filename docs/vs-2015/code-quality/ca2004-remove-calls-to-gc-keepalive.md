---
title: 'CA2004 : Supprimez les appels à GC. KeepAlive | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8fbaa0bae44b09cef1d75c31c342ac6cf3e463df
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588030"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004 : Supprimez les appels à GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2004 : supprimez les appels à GC. KeepAlive](https://docs.microsoft.com/visualstudio/code-quality/ca2004-remove-calls-to-gc-keepalive).

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Classes utilisent `SafeHandle` mais contiennent toujours des appels à `GC.KeepAlive`.

## <a name="rule-description"></a>Description de la règle
 Si vous convertissez en `SafeHandle` utilisation, supprimez tous les appels à `GC.KeepAlive` (objet). Dans ce cas, les classes ne requièrent pas d’appeler `GC.KeepAlive`, en supposant qu’elles n’ont pas de finaliseur, mais dépendent `SafeHandle` pour terminer le handle du système d’exploitation pour eux.  Bien que le coût de laisser dans un appel à `GC.KeepAlive` peut être négligeable en termes de performances, la perception qui un appel à `GC.KeepAlive` est nécessaire ou suffit à résoudre le problème qui ne peut plus exister rend le code plus difficile pour une durée de vie mettre à jour.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez les appels à `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer cet avertissement uniquement si elle n’est pas techniquement correcte convertir `SafeHandle` utilisation dans votre classe.



