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
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 236a95cd8d4af8da91199bf79e7c9fe3aa0d49af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769488"
---
# <a name="automatic-feature-suspension"></a>Suspension automatique de fonctionnalités

Si la mémoire système disponible tombe à 200 Mo ou moins, Visual Studio affiche le message suivant dans l’éditeur de code :

![Texte d’alerte interruption de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)

Lorsque Visual Studio détecte une condition de mémoire insuffisante, il suspend automatiquement certaines fonctionnalités avancées pour l’aider à rester stable. Visual Studio continue de fonctionner comme avant, mais ses performances sont détériorées.

Dans une condition de mémoire insuffisante, les actions suivantes se produisent :

- L’analyse du code en temps réel pour Visual C# et Visual Basic est réduite à une portée minimale.

- Le mode de latence faible de [garbage collection](/dotnet/standard/garbage-collection/index) (GC) pour Visual C# et Visual Basic est désactivé.

- Les caches Visual Studio sont vidés.

## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio

Pour obtenir des conseils et des astuces sur la façon d’améliorer les performances de Visual Studio quand vous travaillez avec des solutions volumineuses ou des conditions de mémoire insuffisante, consultez [Considérations sur les performances pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>L’analyse du code en temps réel est réduite à une étendue minimale

Par défaut, l’analyse du code en direct s’exécute pour les documents et projets ouverts. Vous pouvez personnaliser cette étendue d’analyse pour qu’elle soit réduite au document actif ou augmentée dans la solution complète. Pour plus d’informations, consultez [Comment : configurer l’étendue de l’analyse du code en temps réel pour le code managé](./configure-live-code-analysis-scope-managed-code.md). Dans une condition de mémoire insuffisante, Visual Studio force l’étendue de l’analyse dynamique à être réduite au document actif. Toutefois, vous pouvez réactiver votre étendue d’analyse par défaut en choisissant le bouton **réactiver** dans la barre d’informations lorsqu’elle apparaît ou en redémarrant Visual Studio. La boîte de dialogue Options affiche toujours les paramètres actuels de l’étendue de l’analyse du code en direct.

## <a name="gc-low-latency-disabled"></a>Faible latence GC désactivée

Pour réactiver le mode de faible latence GC, redémarrez Visual Studio. Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre saisie ne bloque pas les opérations GC. Toutefois, si une condition de mémoire insuffisante entraîne l’affichage de l’avertissement de suspension automatique par Visual Studio, le mode de latence faible GC est désactivé pour cette session. Le redémarrage de Visual Studio réactive le comportement de GC par défaut. Pour plus d'informations, consultez <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches Visual Studio vidés

Si vous continuez votre session de développement actuelle ou si vous redémarrez Visual Studio, tous les caches Visual Studio sont immédiatement vidés, mais ils commencent à être remplis. Les caches vidés incluent des caches pour les fonctionnalités suivantes :

- Rechercher toutes les références

- Naviguer vers

- Ajouter using

En outre, les caches utilisés pour les opérations internes de Visual Studio sont également effacés.

> [!NOTE]
> L’avertissement de suspension automatique des fonctionnalités ne se produit qu’une seule fois par solution, et non par session. Cela signifie que si vous passez de Visual Basic à Visual C# (ou vice versa) et que vous exécutez dans une autre condition de mémoire insuffisante, vous pouvez éventuellement recevoir un autre avertissement de suspension automatique de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Comment : configurer l’étendue de l’analyse du code en temps réel pour le code managé](./configure-live-code-analysis-scope-managed-code.md)
- [Principes de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Considérations sur les performances pour les grandes solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
