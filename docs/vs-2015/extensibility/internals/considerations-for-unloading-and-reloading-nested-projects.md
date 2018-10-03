---
title: Considérations pour décharger et recharger imbriqués projets | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d932096d209d8e39b5d218ceb868453fa9a8a6f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516613"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour décharger et recharger des projets imbriqués
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [considérations pour le déchargement et rechargement de projets imbriqués](https://docs.microsoft.com/visualstudio/extensibility/internals/considerations-for-unloading-and-reloading-nested-projects).  
  
Lorsque vous implémentez des types de projets imbriqués, vous devez effectuer les étapes supplémentaires lorsque vous déchargez et rechargez les projets. Pour informer correctement les écouteurs pour les événements de solution, vous devez correctement augmenter la `OnBeforeUnloadProject` et `OnAfterLoadProject` événements.  
  
 Vous devez déclencher ces événements de cette manière l’une des raisons sont que vous ne souhaitez pas que le contrôle de code source (SCC) pour supprimer les éléments à partir du serveur et les ajouter en tant que quelque chose de nouveau s’il existe un `Get` opération à partir du contrôle de code source. Dans ce cas, un nouveau fichier serait chargé SCC, et vous devez décharger et recharger tous les fichiers dans le cas où ils sont différents. Appels de contrôle de code source `ReloadItem`. Votre implémentation de cet appel consiste à supprimer le projet et recréez-la à nouveau en implémentant `IVsFireSolutionEvents` pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject`. Lorsque vous effectuez cette implémentation, le SCC est informé que le projet a été temporairement supprimé et rajouté. Par conséquent, le contrôle de code source ne fonctionne pas sur le projet comme si le projet a été réellement supprimé à partir du serveur et ajouté de nouveau.  
  
## <a name="reloading-projects"></a>Rechargement de projets  
 Pour prendre en charge le rechargement de projets imbriqués, vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode). Dans votre implémentation de `ReloadItem`, fermez les projets imbriqués et de la recréer ensuite.  
  
 Déclenche en général lorsqu’un projet est rechargé, l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> et `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` événements. Toutefois, pour les projets imbriqués qui seront supprimés et rechargés, le projet parent lance le processus, pas l’IDE. Étant donné que le projet parent ne déclenche pas d’événements de solution, et l’IDE dispose d’aucune information sur l’initialisation du processus, les événements ne sont pas déclenchés.  
  
 Pour gérer ce processus, les appels de projet parent `QueryInterface` sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface désactivé le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents` propose des fonctions qui indiquent à l’IDE pour déclencher le `OnBeforeUnloadProject` événement à décharger le projet imbriqué, puis déclenchez le `OnAfterLoadProject` événement à recharger le projet même.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)

