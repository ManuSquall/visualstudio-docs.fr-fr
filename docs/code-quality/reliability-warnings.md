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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d45deadc48445e043535e84b36718a14f5b391f6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182805"
---
# <a name="reliability-warnings"></a>Avertissements liés à la fiabilité

Les avertissements de fiabilité prennent en charge la fiabilité des bibliothèques et des applications, telles que la mémoire et l’utilisation des threads. Les règles de fiabilité sont les suivantes :

|Règle|Description|
|----------|-----------------|
|[CA2000 : Supprimer les objets avant la mise hors de portée](../code-quality/ca2000.md)|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|
|[CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes](../code-quality/ca2001.md)|Un membre appelle une méthode potentiellement dangereuse ou problématique.|
|[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](../code-quality/ca2002.md)|Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|
|[CA2003 : Ne traitez pas les fibres comme des threads](../code-quality/ca2003.md)|Un thread managé est traité comme un thread Win32.|
|[CA2004 : Supprimez les appels à GC.KeepAlive](../code-quality/ca2004.md)|Si vous effectuez une conversion en utilisation SafeHandle, supprimez tous les appels à GC. KeepAlive (objet). Dans ce cas, les classes n’ont pas besoin d’appeler GC. KeepAlive, en supposant qu’ils n’ont pas de finaliseur, mais qu’ils reposent sur SafeHandle pour finaliser le handle du système d’exploitation.|
|[CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives](../code-quality/ca2006.md)|L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s’il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place.|
|[CA2007 : N’attendez pas directement une Tâche](../code-quality/ca2007.md)|Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) directement un <xref:System.Threading.Tasks.Task> .|
|[CA2009 : N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable`la méthode était inutilement appelée sur une collection immuable de l' <xref:System.Collections.Immutable> espace de noms.|
|[Ca2011 : ne pas assigner la propriété dans son accesseur Set](../code-quality/ca2011.md) | Une valeur a été assignée par erreur à une propriété dans son propre [accesseur Set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager &lt; T&gt;](../code-quality/ca2015.md) | L’ajout d’un finaliseur à un type dérivé de <xref:System.Buffers.MemoryManager%601> peut permettre la libération de la mémoire pendant qu’il est toujours utilisé par un <xref:System.Span%601> . |
