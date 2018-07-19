---
title: Considérations relatives à décharger et recharger imbriqués projets | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f22575c4affa6e6a13ea80b32674a3e517202fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127917"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour décharger et recharger les projets imbriqués

Lorsque vous implémentez les types de projets imbriqués, vous devez effectuer des étapes supplémentaires lorsque vous déchargez et rechargez les projets. Afin d’informer correctement les écouteurs d’événements de la solution, vous devez augmenter au correctement le `OnBeforeUnloadProject` et `OnAfterLoadProject` les événements.

Sont de l’une des raisons pour déclencher ces événements pour le contrôle de code source (SCC). Vous ne souhaitez pas obligé SCC à supprimer les éléments à partir du serveur, puis les ajouter en tant que *nouveau* s’il existe un `Get` opération à partir du contrôle de code source. Dans ce cas, un nouveau fichier était chargé en dehors du contrôle de code source. Vous devez décharger et recharger tous les fichiers dans le cas où ils sont différents.

Appels de contrôle de code source de `ReloadItem`. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject` pour supprimer le projet et le recréer. Lorsque vous implémentez l’interface de cette façon, contrôle de code source est informé que le projet a été temporairement supprimé et ajouté de nouveau. Par conséquent, contrôle de code source ne fonctionne sur le projet comme si le projet a été *réellement* supprimé et rajouté.

## <a name="reloading-projects"></a>Recharger des projets

Pour prendre en charge le rechargement de projets imbriqués, vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode). Dans votre implémentation de `ReloadItem`, fermez les projets imbriqués et de recréer ensuite.

En général, lorsqu’un projet est rechargé, l’IDE génère le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> les événements. Toutefois, pour les projets imbriqués qui sont supprimés et rechargés, le projet parent lance le processus, pas dans l’IDE. Étant donné que le projet parent ne déclenche des événements de la solution, et l’IDE n’a pas d’informations sur l’initialisation du processus, les événements ne sont pas déclenchés.

Pour gérer ce processus, les appels de projet parent `QueryInterface` sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents` propose des fonctions qui indiquent à l’IDE pour déclencher le `OnBeforeUnloadProject` événement à décharger le projet imbriqué, puis déclenchez le `OnAfterLoadProject` à recharger le projet même événement.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)