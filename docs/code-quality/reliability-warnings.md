---
title: avertissements liés à la fiabilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252585"
---
# <a name="reliability-warnings"></a>Avertissements liés à la fiabilité

Les avertissements de fiabilité prennent en charge la fiabilité des bibliothèques et des applications, telles que la mémoire et l’utilisation des threads. Les règles de fiabilité sont les suivantes :

|Règle|Description|
|----------|-----------------|
|@NO__T 0CA2000 : Supprimer les objets avant de perdre l’étendue @ no__t-0|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|
|@NO__T 0CA2001 : Évitez d’appeler les méthodes problématiques @ no__t-0|Un membre appelle une méthode potentiellement dangereuse ou problématique.|
|@NO__T 0CA2002 : Ne pas verrouiller sur les objets avec une identité faible @ no__t-0|Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|
|@NO__T 0CA2003 : Ne pas traiter les fibres comme des threads @ no__t-0|Un thread managé est traité comme un thread Win32.|
|@NO__T 0CA2004 : Supprimez les appels à GC. KeepAlive @ no__t-0|Si vous effectuez une conversion en utilisation SafeHandle, supprimez tous les appels à GC. KeepAlive (objet). Dans ce cas, les classes n’ont pas besoin d’appeler GC. KeepAlive, en supposant qu’ils n’ont pas de finaliseur, mais qu’ils reposent sur SafeHandle pour finaliser le handle du système d’exploitation.|
|@NO__T 0CA2006 : Utiliser SafeHandle pour encapsuler les ressources natives @ no__t-0|L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s'il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place.|
|@NO__T 0CA2007 : Ne pas attendre directement une tâche @ no__t-0|Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directement.|
