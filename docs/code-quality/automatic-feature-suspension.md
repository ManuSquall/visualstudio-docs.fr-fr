---
title: Suspension automatique de fonctionnalités
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606537"
---
# <a name="automatic-feature-suspension"></a>Suspension automatique de fonctionnalités

Si la mémoire système disponible tombe à 200 Mo ou moins, Visual Studio affiche le message suivant dans l’éditeur de code :

![Texte d’alerte interruption de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)

Lorsque Visual Studio détecte une condition de mémoire insuffisante, il suspend automatiquement certaines fonctionnalités avancées pour l’aider à rester stable. Visual Studio continue de fonctionner comme avant, mais ses performances sont détériorées.

Dans une condition de mémoire insuffisante, les actions suivantes se produisent :

- L’analyse complète de la C# solution pour Visual et Visual Basic est désactivée.

- Le mode de latence faible de [garbage collection](/dotnet/standard/garbage-collection/index) (GC) pour C# Visual et Visual Basic est désactivé.

- Les caches Visual Studio sont vidés.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio

Pour obtenir des conseils et des astuces sur la façon d’améliorer les performances de Visual Studio quand vous travaillez avec des solutions volumineuses ou des conditions de mémoire insuffisante, consultez [Considérations sur les performances pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analyse complète de la solution suspendue

Par défaut, l’analyse complète de la solution est activée pour Visual Basic et C#désactivée pour Visual. Toutefois, dans une condition de mémoire insuffisante, l’analyse complète de la solution est automatiquement C#désactivée pour Visual Basic et visuel, quels que soient les paramètres de la boîte de dialogue Options. Toutefois, vous pouvez réactiver l’analyse complète de la solution en choisissant le bouton **réactiver** dans la barre d’informations quand elle apparaît, en activant la case à cocher **activer l’analyse complète** de la solution dans la boîte de dialogue Options ou en redémarrant Visual Studio. La boîte de dialogue Options affiche toujours les paramètres d’analyse complète de la solution en cours. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse complète de la solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Faible latence GC désactivée

Pour réactiver le mode de faible latence GC, redémarrez Visual Studio. Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre saisie ne bloque pas les opérations GC. Toutefois, si une condition de mémoire insuffisante entraîne l’affichage de l’avertissement de suspension automatique par Visual Studio, le mode de latence faible GC est désactivé pour cette session. Le redémarrage de Visual Studio réactive le comportement de GC par défaut. Pour plus d'informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches Visual Studio vidés

Si vous continuez votre session de développement actuelle ou si vous redémarrez Visual Studio, tous les caches Visual Studio sont immédiatement vidés, mais ils commencent à être remplis. Les caches vidés incluent des caches pour les fonctionnalités suivantes :

- Rechercher toutes les références

- Boîte de dialogue Naviguer vers

- Ajouter using

En outre, les caches utilisés pour les opérations internes de Visual Studio sont également effacés.

> [!NOTE]
> L’avertissement de suspension automatique des fonctionnalités ne se produit qu’une seule fois par solution, et non par session. Cela signifie que si vous passez de Visual Basic à visuel C# (ou vice versa) et que vous exécutez dans une autre condition de mémoire insuffisante, vous pouvez éventuellement recevoir un autre avertissement de suspension automatique de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour activer et désactiver l’analyse de solution complète](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principes de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considérations sur les performances pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
