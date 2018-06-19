---
title: Suspension automatique des fonctionnalités dans Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31893925"
---
# <a name="automatic-feature-suspension"></a>Suspension de la fonctionnalité automatique

Si votre mémoire système disponible est inférieure ou égale à 200 Mo, Visual Studio affiche le message suivant dans l’éditeur de code :

![Texte d’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)

Lorsque Visual Studio détecte une condition de mémoire insuffisante, il interrompt automatiquement certaines fonctionnalités avancées pour aider à rester stable. Visual Studio continue de fonctionner comme avant, mais ses performances sont dégradées.

Dans une condition de mémoire insuffisante, les actions suivantes se produisent :

- Analyse de la solution complète pour Visual c# et Visual Basic est désactivée.

- [Le Garbage Collection](/dotnet/standard/garbage-collection/index) en mode de faible latence (GC) pour Visual c# et Visual Basic est désactivé.

- Les caches de Visual Studio sont vidées.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio

Pour obtenir des conseils et astuces sur la façon d’améliorer les performances de Visual Studio lorsque vous traitez des solutions de grande taille ou des conditions de mémoire insuffisante, consultez [considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analyse complète de la solution suspendu

Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#. Toutefois, dans une condition de mémoire insuffisante, analyse complète de la solution est automatiquement désactivé pour Visual Basic et Visual c#, quels que soient leurs paramètres dans la boîte de dialogue Options. Toutefois, vous pouvez réactiver l’analyse complète de la solution en choisissant le **réactiver** bouton dans les informations de la barre lorsqu’il apparaît, en sélectionnant le **activer l’analyse de la solution complète** case à cocher dans la boîte de dialogue Options, ou le redémarrage de Visual Studio. La boîte de dialogue Options affiche toujours les paramètres d’analyse à la solution complète en cours. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse de Solution complète](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Dans le catalogue global à faible latence désactivée

Pour réactiver le mode de faible latence GC, redémarrez Visual Studio. Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre saisie ne bloque pas les opérations de catalogue global. Toutefois, si une condition de mémoire insuffisante entraîne Visual Studio afficher l’avertissement de la suspension automatique, en mode de faible latence GC est désactivé pour cette session. Le redémarrage de Visual Studio active de nouveau le comportement de catalogue global par défaut. Pour plus d'informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches de Visual Studio vidés

Si vous continuez votre session en cours de développement ou redémarrez Visual Studio, tous les caches de Visual Studio sont immédiatement supprimées, mais commencent à remplir à nouveau. Les caches vidées incluent des caches pour les fonctionnalités suivantes :

- Rechercher toutes les références

- Boîte de dialogue Naviguer vers

- Ajouter Using

En outre, les caches utilisés pour des opérations internes de Visual Studio sont également désélectionnés.

> [!NOTE]
> L’avertissement de suspension de fonctionnalité automatique se produit une seule fois sur une base par solution, pas sur une base par session. Cela signifie que si vous basculez à partir de Visual Basic, Visual c# (ou vice versa) et s’exécuter dans une autre condition de mémoire insuffisante, vous pouvez éventuellement obtenir une autre avertissement de suspension automatique de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Comment : activer et désactiver l’analyse complète de la Solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principes de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)