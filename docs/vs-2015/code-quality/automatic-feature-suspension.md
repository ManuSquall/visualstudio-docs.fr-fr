---
title: Suspension automatique de fonctionnalités | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 281a4cbfb7bb1564af698cf4e745d56207f3e58e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495487"
---
# <a name="automatic-feature-suspension"></a>Suspension automatique de fonctionnalités
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [suspension automatique de fonctionnalités](https://docs.microsoft.com/visualstudio/code-quality/automatic-feature-suspension).

Si votre mémoire système disponible est inférieure ou égale à 200 Mo, Visual Studio affiche le message suivant dans l’éditeur de code.

 ![Texte de l’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa-alert.png "FSA_Alert")

 Lorsque Visual Studio détecte une condition de mémoire insuffisante, il suspend automatiquement certaines fonctionnalités avancées pour l’aider à rester stable. Lorsque cela advanced fonctionnalité suspension avertissement s’affiche, Visual Studio continueront à fonctionner comme avant, mais ses performances seront légèrement détérioré.

 Dans une condition de mémoire insuffisante, les événements suivants se produisent :

-   Analyse de la solution complète pour Visual c# et Visual Basic est désactivée.

-   [Le Garbage Collection](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) mode de faible latence (GC) pour Visual c# et Visual Basic sont désactivées.

-   Visual Studio caches soient vidés le.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio
 Pour des conseils et astuces sur la façon d’améliorer les performances de Visual Studio lorsque vous traitez des solutions de grande taille ou de conditions de mémoire insuffisante, consultez [considérations sur les performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Analyse complète de la solution suspendu
 Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#. Toutefois, dans une condition de mémoire insuffisante, analyse complète de la solution est automatiquement désactivé pour Visual Basic et Visual c#, quels que soient leurs paramètres dans la boîte de dialogue Options. Toutefois, vous pouvez réactiver l’analyse complète de la solution en choisissant le **réactiver** bouton dans les informations de la barre quand il s’affiche, en sélectionnant le **activer l’analyse complète de la solution** case à cocher dans la boîte de dialogue Options, ou en le redémarrage de Visual Studio. Paramètres d’analyse, la boîte de dialogue Options affiche toujours la solution complète en cours. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse complète la Solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC à faible latence désactivée
 Pour réactiver le mode de faible latence GC, redémarrez Visual Studio.  Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre frappe ne bloque pas les opérations de GC. Toutefois, si une condition de mémoire insuffisante entraîne Visual Studio afficher l’avertissement de suspension automatique, mode de faible latence GC est désactivé pour cette session. Le redémarrage de Visual Studio activer de nouveau le comportement de catalogue global par défaut. Pour plus d'informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches de Visual Studio vidés

Tous les caches de Visual Studio sont vidés immédiatement, mais va commencer à remplir à nouveau si vous continuez votre session en cours de développement ou redémarrez Visual Studio. Les caches vidées incluent des caches pour les fonctionnalités suivantes.

-   Rechercher toutes les références

-   Boîte de dialogue Naviguer vers

-   Ajouter à l’aide de

En outre, les caches utilisés pour les opérations internes de Visual Studio sont également désactivées.

> [!NOTE]
> L’avertissement de suspension de fonctionnalité automatique se produit qu’une seule fois sur une base par solution, pas sur une base par session. Cela signifie que si vous basculez à partir de Visual Basic vers Visual c# (ou vice versa) et que vous rencontrez une autre condition de mémoire insuffisante, vous pouvez éventuellement obtenir un autre avertissement de suspension de fonctionnalité automatique.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour activer et désactiver l’analyse de solution complète](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Principes de base du Garbage Collection](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)