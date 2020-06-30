---
title: 'CA2003 : ne traitez pas les fibres comme des threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521172"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003 : Ne traitez pas les fibres comme des threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft. fiabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un thread managé est traité comme un thread Win32.

## <a name="rule-description"></a>Description de la règle
 Ne partez pas du principe qu’un thread managé est un thread Win32. Il s’agit d’une fibre. Le common language runtime (CLR) exécute des threads managés en tant que fibres dans le contexte de threads réels appartenant à SQL. Ces threads peuvent être partagés entre des AppDomains et même des bases de données dans le processus de SQL Server. L’utilisation du stockage local des threads managés fonctionne, mais vous ne pouvez pas utiliser le stockage local des threads non managés ou supposer que votre code s’exécutera à nouveau sur le thread de système d’exploitation actuel. Ne modifiez pas les paramètres tels que les paramètres régionaux du thread. N’appelez pas CreateCriticalSection ou CreateMutex via P/Invoke, car ils requièrent que le thread qui entre dans un verrou doive également quitter le verrou. Comme ce n’est pas le cas lorsque vous utilisez des fibres, les sections critiques et les mutex Win32 seront inutiles dans SQL. Vous pouvez utiliser en toute sécurité l’essentiel de l’État sur un objet System. thread géré. Cela comprend le stockage local des threads managés et la culture d’interface utilisateur (IU) actuelle du thread. Toutefois, pour des raisons de modèle de programmation, vous ne pourrez pas modifier la culture actuelle d’un thread quand vous utilisez SQL. cela sera appliqué par le biais d’une nouvelle autorisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre utilisation des threads et modifiez votre code en conséquence.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cette règle.
