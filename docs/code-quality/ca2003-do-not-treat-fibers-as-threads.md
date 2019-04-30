---
title: 'CA2003 : Ne traitez pas les fibres comme des threads'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8faaf3c6557065188c795d75ea9bbe4e78998709
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806986"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003 : Ne traitez pas les fibres comme des threads

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un thread managé est traité comme un thread Win32.

## <a name="rule-description"></a>Description de la règle

Ne supposez pas qu'un thread managé est un thread Win32 ; Il s’agit d’une fibre. Le common language runtime (CLR) exécute les threads managés en tant que fibres dans le contexte de threads réels qui sont détenus par SQL. Ces threads peuvent être partagés entre les domaines d’application et les bases de données dans le processus SQL Server. À l’aide de managed works de stockage local de thread, mais vous ne pouvez pas utiliser le stockage local de thread non managé ou supposent que votre code s’exécutera à nouveau sur le thread de système d’exploitation actuel. Ne modifiez pas les paramètres, tels que les paramètres régionaux du thread. N’appelez pas CreateCriticalSection ou CreateMutex via P/Invoke, car elles nécessitent que le thread qui accède à un verrou doit aussi être déverrouillé. Étant donné que le thread qui accède à un verrou ne ferme pas un verrou lors de l’utilisation de fibres, les mutex et les sections critiques Win32 sont inutiles dans SQL. Vous pouvez utiliser en toute sécurité de la majeure partie de l’état sur managé <xref:System.Threading.Thread> objet, y compris le stockage local des threads managés et la culture d’interface utilisateur utilisateur actuelle du thread. Toutefois, pour des raisons de modèle de programmation, vous ne pourrez modifier la culture actuelle d’un thread lorsque vous utilisez SQL. Cette limitation est appliquée via une nouvelle autorisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Examinez votre utilisation des threads et modifiez votre code en conséquence.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas cette règle.