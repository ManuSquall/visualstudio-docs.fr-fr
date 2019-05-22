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
ms.openlocfilehash: 009422eaf9ac81af6e8f9d48732655b2528c85a0
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976147"
---
# <a name="reliability-warnings"></a>Avertissements liés à la fiabilité

Avertissements de fiabilité prennent en charge la fiabilité de bibliothèque et d’application, tels que l’utilisation de mémoire et le thread correcte. Les règles de fiabilité sont les suivantes :

|Règle|Description|
|----------|-----------------|
|[CA2000 : Supprimez les objets avant de portée](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|
|[CA2001 : Évitez d’appeler des méthodes](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membre appelle une méthode potentiellement dangereuse ou problématique.|
|[CA2002 : Ne verrouillez pas sur des objets à identité faible](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|
|[CA2003 : Ne traitez pas les fibres comme des threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread managé est traité comme un thread Win32.|
|[CA2004 : Supprimez les appels à GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Si vous convertissez d’utiliser SafeHandle, supprimez tous les appels à GC. KeepAlive (objet). Dans ce cas, les classes ne devez pas appeler GC. KeepAlive, en supposant qu’ils n’ont pas de finaliseur, mais dépendent de SafeHandle pour finaliser le système d’exploitation gérer pour eux.|
|[CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s’il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place.|
|[CA2007 : N’attend pas directement d’une tâche](../code-quality/ca2007-do-not-directly-await-task.md)|Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directement.|