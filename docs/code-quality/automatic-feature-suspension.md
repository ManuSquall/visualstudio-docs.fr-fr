---
title: Suspension automatique de fonctionnalités
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe86e085e50dc0e72c00b7bbe7a313e689e0ee5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950979"
---
# <a name="automatic-feature-suspension"></a>Suspension automatique de fonctionnalités

Si votre mémoire système disponible est inférieure ou égale à 200 Mo, Visual Studio affiche le message suivant dans l’éditeur de code :

![Texte de l’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)

Lorsque Visual Studio détecte une condition de mémoire insuffisante, il suspend automatiquement certaines fonctionnalités avancées pour l’aider à rester stable. Visual Studio continue à fonctionner comme avant, mais ses performances sont dégradées.

Dans une condition de mémoire insuffisante, les actions suivantes se produisent :

- Analyse de la solution complète pour Visual c# et Visual Basic est désactivée.

- [Le Garbage Collection](/dotnet/standard/garbage-collection/index) mode de faible latence (GC) pour Visual C# et Visual Basic est désactivée.

- Visual Studio caches soient vidés le.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio

Pour des conseils et astuces sur la façon d’améliorer les performances de Visual Studio lorsque vous traitez des solutions de grande taille ou de conditions de mémoire insuffisante, consultez [considérations sur les performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analyse complète de la solution suspendu

Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#. Toutefois, dans une condition de mémoire insuffisante, analyse complète de la solution est automatiquement désactivé pour Visual Basic et Visual c#, quels que soient leurs paramètres dans la boîte de dialogue Options. Toutefois, vous pouvez réactiver l’analyse complète de la solution en choisissant le **réactiver** bouton dans les informations de la barre quand il s’affiche, en sélectionnant le **activer l’analyse complète de la solution** case à cocher dans la boîte de dialogue Options, ou en le redémarrage de Visual Studio. Paramètres d’analyse, la boîte de dialogue Options affiche toujours la solution complète en cours. Pour plus d'informations, voir [Procédure : Activer et désactiver l’analyse complète de la Solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC à faible latence désactivée

Pour réactiver le mode de faible latence GC, redémarrez Visual Studio. Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre frappe ne bloque pas les opérations de GC. Toutefois, si une condition de mémoire insuffisante entraîne Visual Studio afficher l’avertissement de suspension automatique, mode de faible latence GC est désactivé pour cette session. Le redémarrage de Visual Studio active de nouveau le comportement de catalogue global par défaut. Pour plus d'informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches de Visual Studio vidés

Si vous continuez votre session en cours de développement ou redémarrez Visual Studio, tous les caches de Visual Studio sont vidées immédiatement, mais commencent à remplir à nouveau. Les caches vidées incluent des caches pour les fonctionnalités suivantes :

- Rechercher toutes les références

- Boîte de dialogue Naviguer vers

- Ajouter à l’aide de

En outre, les caches utilisés pour les opérations internes de Visual Studio sont également désactivées.

> [!NOTE]
> L’avertissement de suspension de fonctionnalité automatique se produit qu’une seule fois sur une base par solution, pas sur une base par session. Cela signifie que si vous basculez à partir de Visual Basic vers Visual c# (ou vice versa) et que vous rencontrez une autre condition de mémoire insuffisante, vous pouvez éventuellement obtenir un autre avertissement de suspension de fonctionnalité automatique.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Activer et désactiver l’analyse complète de la Solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principes de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)