---
title: Considérations pour décharger et recharger imbriqués projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a45cf72f09ddf4e5ac1d68b59c2b13e64982744
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335539"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour décharger et recharger les projets imbriqués

Lorsque vous implémentez des types de projets imbriqués, vous devez effectuer les étapes supplémentaires lorsque vous déchargez et rechargez les projets. Pour informer correctement les écouteurs pour les événements de solution, vous devez correctement augmenter la `OnBeforeUnloadProject` et `OnAfterLoadProject` événements.

Une des raisons pour déclencher ces événements est pour le contrôle de code source (SCC). Vous ne souhaitez pas SCC pour supprimer les éléments à partir du serveur, puis les ajouter en tant que *nouveau* s’il existe un `Get` opération à partir du contrôle de code source. Dans ce cas, un nouveau fichier était chargé SCC. Vous seriez obligé de décharger et recharger tous les fichiers dans le cas où ils sont différents.

Appels de contrôle de code de la source `ReloadItem`. Implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface à appeler `OnBeforeUnloadProject` et `OnAfterLoadProject` à supprimer le projet, puis le recréer. Lorsque vous implémentez l’interface de cette façon, SCC est informé que le projet a été temporairement supprimé et rajouté. Par conséquent, SCC ne travaille pas sur le projet comme si le projet a été *réellement* supprimé et rajouté.

## <a name="reload-projects"></a>Recharger les projets

Pour prendre en charge le rechargement de projets imbriqués, vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode). Dans votre implémentation de `ReloadItem`, fermez les projets imbriqués et de la recréer ensuite.

Déclenche en général lorsqu’un projet est rechargé, l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> événements. Toutefois, pour les projets imbriqués qui sont supprimés et rechargés, le projet parent lance le processus, pas l’IDE. Étant donné que le projet parent ne déclenche des événements de solution, et l’IDE dispose d’aucune information sur l’initialisation du processus, les événements ne sont pas déclenchés.

Pour gérer ce processus, les appels de projet parent `QueryInterface` sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents` propose des fonctions qui indiquent à l’IDE pour déclencher le `OnBeforeUnloadProject` événement à décharger le projet imbriqué, puis déclenchez le `OnAfterLoadProject` événement à recharger le projet même.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projets imbriqués](../../extensibility/internals/nesting-projects.md)