---
title: Suspension automatique de fonctionnalités
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431239"
---
# <a name="automatic-feature-suspension"></a>Suspension automatique de fonctionnalités

Si votre mémoire système disponible tombe à 200 Mo ou moins, Visual Studio affiche le message suivant dans l’éditeur de code :

![Texte d’alerte suspendant l’analyse complète de solution](../code-quality/media/fsa_alert.png)

Lorsque Visual Studio détecte une faible état de mémoire, il suspend automatiquement certaines fonctionnalités avancées pour l’aider à rester stable. Visual Studio continue de fonctionner comme avant, mais sa performance est dégradée.

Dans un état de mémoire basse, les actions suivantes ont lieu :

- L’analyse de code en direct pour Visual CMD et Visual Basic est réduite à une portée minimale.

- [Le](/dotnet/standard/garbage-collection/index) mode de collecte des ordures (GC) à faible latence pour Visual C et Visual Basic est désactivé.

- Les caches Visual Studio sont rincées.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio

Pour des conseils et astuces sur la façon d’améliorer les performances visual Studio lorsqu’il s’agit de grandes solutions ou des conditions de faible mémoire, voir [les considérations de performance pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L’analyse du code en direct est réduite à une portée minimale

Par défaut, l’analyse de code en direct s’exécute pour les documents et projets ouverts. Vous pouvez personnaliser cette portée d’analyse pour être réduite au document actuel ou augmentée à une solution entière. Pour plus d’informations, voir [Comment configurer la portée d’analyse de code en direct pour le code géré](./configure-live-code-analysis-scope-managed-code.md). Dans un état de mémoire basse, Visual Studio force la portée d’analyse en direct à être réduite au document actuel. Toutefois, vous pouvez ré-activer votre portée d’analyse préférée en choisissant le bouton **Re-enable** dans la barre d’information quand il apparaît ou en redémarrant Visual Studio. La boîte de dialogue Options affiche toujours les paramètres actuels de portée d’analyse de code en direct.

## <a name="gc-low-latency-disabled"></a>GC faible latence désactivé

Pour ré-activer le mode GC à faible latence, redémarrez Visual Studio. Par défaut, Visual Studio permet au mode GC à faible latence chaque fois que vous tapez pour s’assurer que votre dactylographie ne bloque aucune opération GC. Toutefois, si une affection de faible mémoire provoque Visual Studio à afficher l’avertissement de suspension automatique, le mode GC à faible latence est désactivé pour cette session. Le redémarrage de Visual Studio permet le comportement GC par défaut. Pour plus d’informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches Visual Studio rincés

Si vous continuez votre session de développement en cours ou redémarrez Visual Studio, toutes les caches Visual Studio sont immédiatement vidées, mais commencez à repeupler. Les caches rincées comprennent des caches pour les fonctionnalités suivantes :

- Rechercher toutes les références

- Naviguer vers

- Ajouter à l’aide

En outre, les caches utilisées pour les opérations internes visual Studio sont également effacées.

> [!NOTE]
> L’avertissement automatique de suspension de fonction ne se produit qu’une seule fois par solution, et non par session. Cela signifie que si vous passez de Visual Basic à Visual C (ou vice-versa) et que vous rencontrez une autre affection de faible mémoire, vous pouvez éventuellement obtenir un autre avertissement automatique de suspension de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Comment : Configurer la portée d’analyse de code en direct pour le code géré](./configure-live-code-analysis-scope-managed-code.md)
- [Principes de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considérations de performance pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
