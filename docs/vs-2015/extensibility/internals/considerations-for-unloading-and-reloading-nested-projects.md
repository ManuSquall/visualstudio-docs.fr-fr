---
title: Considérations sur le déchargement et le rechargement des projets imbriqués | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197014"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considérations pour décharger et recharger des projets imbriqués
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous implémentez des types de projets imbriqués, vous devez effectuer des étapes supplémentaires lorsque vous déchargez et rechargez les projets. Pour notifier correctement les écouteurs aux événements de solution, vous devez déclencher correctement les `OnBeforeUnloadProject` `OnAfterLoadProject` événements et.  
  
 L’une des raisons pour lesquelles vous devez déclencher ces événements est que vous ne voulez pas que le contrôle de code source (SCC) supprime les éléments du serveur, puis les ajoute en tant que nouveau si une `Get` opération est effectuée à partir de SCC. Dans ce cas, un nouveau fichier est chargé à partir de SCC et vous devez décharger et recharger tous les fichiers en cas de différences. Appels SCC `ReloadItem` . Votre implémentation de cet appel consiste à supprimer le projet et à le recréer en implémentant `IVsFireSolutionEvents` pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject` . Lorsque vous effectuez cette implémentation, le SCC est informé que le projet a été supprimé temporairement et rajouté. Par conséquent, le SCC ne fonctionne pas sur le projet comme si le projet avait été réellement supprimé du serveur, puis rajouté.  
  
## <a name="reloading-projects"></a>Recharger des projets  
 Pour prendre en charge le rechargement des projets imbriqués, vous devez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> méthode. Dans votre implémentation de `ReloadItem` , fermez les projets imbriqués, puis recréez-les.  
  
 En général, lorsqu’un projet est rechargé, l’IDE déclenche les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` événements et. Toutefois, pour les projets imbriqués qui seront supprimés et rechargés, le projet parent initie le processus, et non l’IDE. Étant donné que le projet parent ne déclenche pas d’événements de solution et que l’IDE n’a pas d’informations sur l’initialisation du processus, les événements ne sont pas déclenchés.  
  
 Pour gérer ce processus, le projet parent appelle `QueryInterface` sur l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interface à partir de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents` possède des fonctions qui indiquent à l’IDE de déclencher l' `OnBeforeUnloadProject` événement pour décharger le projet imbriqué, puis déclencher l' `OnAfterLoadProject` événement pour recharger le même projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Imbriquer des projets](../../extensibility/internals/nesting-projects.md)
