---
title: 'CA2003 : Ne traitez pas les fibres comme des threads | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3d72e052decc5a26dd134aafcaac8aba6af699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810916"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003 : Ne traitez pas les fibres comme des threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un thread managé est traité comme un thread Win32.

## <a name="rule-description"></a>Description de la règle
 Ne supposez pas qu'un thread managé est un thread Win32. Il s’agit d’une fibre. Le common language runtime (CLR) exécutera les threads managés en tant que fibres dans le contexte de threads réels qui sont détenus par SQL. Ces threads peuvent être partagés entre les domaines d’application et les bases de données dans le processus SQL Server. Fonctionnement du stockage local des threads managés, mais vous ne pouvez pas utiliser le stockage local de thread non managé ou supposent que votre code s’exécutera à nouveau sur le thread de système d’exploitation actuel. Ne modifiez pas les paramètres, tels que les paramètres régionaux du thread. N’appelez pas CreateCriticalSection ou CreateMutex via P/Invoke, car elles nécessitent que le thread qui accède à un verrou doit aussi être déverrouillé. Étant donné que ce ne sera pas le cas lorsque vous utilisez des fibres, les mutex et les sections critiques Win32 sera inutiles dans SQL. Vous pouvez en toute sécurité utiliser la majeure partie de l’état d’un objet System.Thread managé. Cela inclut le stockage local des threads managés et la culture d’interface utilisateur utilisateur actuelle du thread. Toutefois, pour des raisons de modèle de programmation, vous serez pas en mesure de modifier la culture actuelle d’un thread lorsque vous utilisez SQL ; Cela est appliquée via une nouvelle autorisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre utilisation des threads et modifiez votre code en conséquence.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cette règle.



