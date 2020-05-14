---
title: Considérations pour le déchargement et le rechargement des projets nested (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709292"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour le déchargement et le rechargement des projets imbriqués

Lorsque vous implémentez des types de projets imbriqués, vous devez effectuer des étapes supplémentaires lorsque vous déchargez et rechargez les projets. Pour aviser correctement les auditeurs des `OnBeforeUnloadProject` événements `OnAfterLoadProject` de solution, vous devez correctement soulever le et les événements.

L’une des raisons de soulever ces événements est le contrôle du code source (CSC). Vous ne voulez pas que SCC supprime les éléments du serveur, puis `Get` les additionne comme *neufs* s’il y a une opération de SCC. Dans ce cas, un nouveau fichier serait chargé hors de SCC. Vous auriez à décharger et recharger tous les fichiers au cas où ils sont différents.

Appels de `ReloadItem`contrôle de code source . Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> `OnBeforeUnloadProject` l’interface pour appeler et `OnAfterLoadProject` supprimer le projet et le recréer. Lorsque vous implémentez l’interface de cette façon, SCC est informé que le projet a été temporairement supprimé et ajouté à nouveau. Par conséquent, SCC ne fonctionne pas sur le projet comme si le projet avait *été effectivement* supprimé et réin ajouté.

## <a name="reload-projects"></a>Recharger les projets

Pour soutenir le rechargement des projets <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> imbriqués, vous implémentez la méthode. Dans votre `ReloadItem`mise en œuvre de , vous fermez les projets imbriqués, puis les recréez.

Typiquement, lorsqu’un projet est rechargé, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> l’IDE soulève les événements et les événements. Toutefois, pour les projets imbriqués qui sont supprimés et rechargés, le projet parent lance le processus, et non l’IDE. Étant donné que le projet parent ne soulève pas d’événements de solution et que l’IDE n’a aucune information sur l’initialisation du processus, les événements ne sont pas soulevés.

Pour gérer ce processus, `QueryInterface` le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> projet parent fait appel à l’interface. `IVsFireSolutionEvents`a des fonctions qui disent `OnBeforeUnloadProject` à l’IDE d’élever l’événement pour décharger le projet imbriqué, puis soulever l’événement `OnAfterLoadProject` pour recharger le même projet.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projets nest](../../extensibility/internals/nesting-projects.md)
