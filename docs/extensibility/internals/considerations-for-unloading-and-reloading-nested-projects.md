---
title: "Considérations relatives à décharger et recharger imbriqués projets | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd45ebf8be2732cded5c84f18338f104b76840cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour décharger et recharger les projets imbriqués
Lorsque vous implémentez les types de projets imbriqués, vous devez effectuer des étapes supplémentaires lorsque vous déchargez et rechargez les projets. Afin d’informer correctement les écouteurs d’événements de la solution, vous devez augmenter au correctement le `OnBeforeUnloadProject` et `OnAfterLoadProject` les événements.  
  
 Vous devez déclencher ces événements de cette manière l’une des raisons sont que vous ne voulez pas de contrôle de code source (SCC) pour supprimer les éléments à partir du serveur et les ajouter en tant que quelque chose de nouveau s’il existe un `Get` opération à partir du contrôle de code source. Dans ce cas, un nouveau fichier serait chargé en dehors du contrôle de code source, et vous devez décharger et recharger tous les fichiers au cas où ils sont différents. Appels de contrôle de code source `ReloadItem`. Votre implémentation de cet appel consiste à supprimer le projet et recréez-la à nouveau en implémentant `IVsFireSolutionEvents` pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject`. Lorsque vous effectuez cette implémentation, le contrôle de code source est informé que le projet a été temporairement supprimé et ajouté de nouveau. Par conséquent, le contrôle de code source ne fonctionne pas sur le projet comme si le projet a été réellement supprimé à partir du serveur et ajouté de nouveau.  
  
## <a name="reloading-projects"></a>Recharger des projets  
 Pour prendre en charge le rechargement de projets imbriqués, vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode). Dans votre implémentation de `ReloadItem`, fermez les projets imbriqués et de recréer ensuite.  
  
 En général, lorsqu’un projet est rechargé, l’IDE génère le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> et `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` les événements. Toutefois, pour les projets imbriqués qui seront supprimés et rechargés, le projet parent lance le processus, pas dans l’IDE. Étant donné que le projet parent ne déclenche pas d’événements de la solution, et l’IDE n’a pas d’informations sur l’initialisation du processus, les événements ne sont pas déclenchés.  
  
 Pour gérer ce processus, les appels de projet parent `QueryInterface` sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface désactiver le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents`propose des fonctions qui indiquent à l’IDE pour déclencher le `OnBeforeUnloadProject` événement à décharger le projet imbriqué, puis déclenchez le `OnAfterLoadProject` à recharger le projet même événement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)