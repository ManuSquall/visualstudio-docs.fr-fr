---
title: Déchargement et rechargement des projets imbriqués
description: Découvrez les étapes supplémentaires qui doivent être effectuées lors du déchargement et du rechargement des projets imbriqués dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9852454d487ab2a7ee08218c9712aa0afc1467ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057069"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations sur le déchargement et le rechargement des projets imbriqués

Lorsque vous implémentez des types de projets imbriqués, vous devez effectuer des étapes supplémentaires lorsque vous déchargez et rechargez les projets. Pour notifier correctement les écouteurs aux événements de solution, vous devez déclencher correctement les `OnBeforeUnloadProject` `OnAfterLoadProject` événements et.

L’une des raisons pour déclencher ces événements est le contrôle de code source (SCC). Vous ne souhaitez pas que SCC supprime les éléments du serveur, puis les ajoute en tant que *nouveau* si une `Get` opération est effectuée à partir de SCC. Dans ce cas, un nouveau fichier est chargé à partir de SCC. Vous devez décharger et recharger tous les fichiers en cas de différence.

Les appels de contrôle de code source `ReloadItem` . Implémentez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject` supprimer le projet, puis recréez-le. Lorsque vous implémentez l’interface de cette manière, SCC est informé que le projet a été supprimé temporairement et rajouté. Par conséquent, SCC ne fonctionne pas sur le projet comme si le projet était *réellement* supprimé et rajouté.

## <a name="reload-projects"></a>Recharger les projets

Pour prendre en charge le rechargement des projets imbriqués, vous devez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> méthode. Dans votre implémentation de `ReloadItem` , fermez les projets imbriqués, puis recréez-les.

En général, lorsqu’un projet est rechargé, l’IDE déclenche <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> événements et. Toutefois, pour les projets imbriqués qui sont supprimés et rechargés, le projet parent lance le processus, et non l’IDE. Étant donné que le projet parent ne déclenche pas d’événements de solution et que l’IDE n’a pas d’informations sur l’initialisation du processus, les événements ne sont pas déclenchés.

Pour gérer ce processus, le projet parent appelle `QueryInterface` sur l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface. `IVsFireSolutionEvents` possède des fonctions qui indiquent à l’IDE de déclencher l' `OnBeforeUnloadProject` événement pour décharger le projet imbriqué, puis déclencher l' `OnAfterLoadProject` événement pour recharger le même projet.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
