---
title: "CA2003 : Ne traitez pas les fibres comme des threads | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5afde6273a7730804746fe03446ea4c16c415302
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
 Ne supposez pas qu'un thread managé est un thread Win32. Il s’agit d’une fibre. Le common language runtime (CLR) exécutera les threads managés en tant que fibres sur les threads réels appartenant à SQL. Ces threads peuvent être partagés entre les domaines d’application et les bases de données dans le processus SQL Server. Fonctionnement du stockage local des threads managés, mais vous ne pouvez pas utiliser le stockage local des threads non managés ou supposer que votre code s’exécutera à nouveau sur le thread du système d’exploitation actuel. Ne modifiez pas les paramètres tels que les paramètres régionaux du thread. N’appelez pas CreateCriticalSection ou CreateMutex via P/Invoke, car ils requièrent que le thread qui accède à un verrou doit aussi être déverrouillé. Étant donné que ce ne sera pas le cas lorsque vous utilisez des fibres, les mutex et les sections critiques Win32 sera inutiles dans SQL. Vous pouvez utiliser en toute sécurité de la plupart de l’état d’un objet System.Thread managé. Cela inclut le stockage local des threads managés et la culture d’interface utilisateur utilisateur actuelle du thread. Toutefois, pour des raisons de modèle de programmation, vous ne serez pas être en mesure de modifier la culture actuelle d’un thread lorsque vous utilisez SQL ; Cela sera appliquée via une nouvelle autorisation.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Examinez votre utilisation des threads et modifiez votre code en conséquence.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous ne devez pas supprimer cette règle.