---
title: "Consid&#233;rations pour d&#233;charger et recharger les projets imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets imbriqués, décharger et recharger"
  - "projets (Visual Studio SDK), décharger et recharger imbriqués"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Consid&#233;rations pour d&#233;charger et recharger les projets imbriqu&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous implémentez des types imbriqués de projet, vous devez exécuter des étapes supplémentaires lorsque vous déchargez et rechargez les projets.  Pour signaler correctement des écouteurs aux événements de solution, vous devez correctement déclencher des événements d' `OnBeforeUnloadProject` et d' `OnAfterLoadProject` .  
  
 Une raison que vous devez déclencher ces événements est de cette manière que vous ne souhaitez pas que le contrôle de \(SCC\) code source pour supprimer des éléments du serveur et les ajouter ultérieurement sous forme d'un nouvel élément s'il existe une opération d' `Get` de SCC.  Dans ce cas, un nouveau fichier est chargé à partir de le SCC et vous devez décharger et recharger tous les fichiers au cas où elles sont différents.  Le SCC appelle `ReloadItem`.  votre implémentation de cet appel est de supprimer le projet et de le recréer de nouveau en implémentant `IVsFireSolutionEvents` pour appeler `OnBeforeUnloadProject` et `OnAfterLoadProject`.  Lorsque vous exécutez cette implémentation, le SCC est informé que le projet a été temporairement supprimé et à nouveau ajouté.  Par conséquent, le SCC ne traite le projet comme si le projet a été supprimé du serveur et de nouveau ensuite ajouté réellement.  
  
## recharger des projets  
 Pour prendre en charge se recharger des projets imbriqués, vous implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> .  Dans votre implémentation d' `ReloadItem`, fermez les projets imbriqués puis les recréer.  
  
 Généralement lorsqu'un projet est rechargé, l'IDE déclenche l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> et les événements d' `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` .  Toutefois, pour les projets imbriqués qui seront supprimés et rechargés, le projet parent initialise le processus, pas l'IDE.  Étant donné que le projet parent ne déclenche pas d'événements de solution, puis l'IDE n'a aucune information sur l'initialisation du processus, les événements ne sont pas déclenchés.  
  
 Pour exécuter ce processus, les appels parents `QueryInterface` de projet à l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> en dehors de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> .  `IVsFireSolutionEvents` a des fonctions qui indiquent l'IDE déclencher l'événement d' `OnBeforeUnloadProject` pour décharger le projet imbriqué, puis déclenche l'événement d' `OnAfterLoadProject` pour recharger le même projet.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Projets d'imbrication](../../extensibility/internals/nesting-projects.md)