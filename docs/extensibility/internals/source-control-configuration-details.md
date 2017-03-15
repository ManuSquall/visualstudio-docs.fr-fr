---
title: "D&#233;tails de Configuration de contr&#244;le de code source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), les détails de configuration"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# D&#233;tails de Configuration de contr&#244;le de code source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour implémenter le contrôle de code source, vous devez configurer correctement votre système de projet ou un éditeur pour effectuer les opérations suivantes :  
  
-   Demander l'autorisation à la transition vers l'état modifié  
  
-   Demander l'autorisation d'enregistrer un fichier  
  
-   Demander l'autorisation d'ajouter, de supprimer, ou renommer des fichiers du projet  
  
## Demander l'autorisation à la transition vers l'état modifié  
 un projet ou un éditeur doit demander l'autorisation à la transition vers l'état \(modifié\) modifié en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>.  Chaque éditeur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> doit appeler l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et recevoir l'approbation pour le modifier de l'environnement avant de retourner `True` pour `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`.  Un projet est essentiellement un éditeur pour un fichier projet, et par conséquent, a la même responsabilité d'implémenter le modifier\-état suivant du fichier projet comme un éditeur de texte fait pour ses fichiers.  Les handles d'environnement l'état modifié de la solution, mais vous devez gérer l'état modifié de tout objet les références de solution mais ne vous inscrivez pas, comme un fichier projet ou ses éléments.  Généralement si votre projet ou éditeur est chargé de gérer la persistance d'un élément, il est chargée d'implémenter le suivi de modifier\-état.  
  
 En réponse à l'appel d' `IVsQueryEditQuerySave2::QueryEditFiles` , l'environnement peut effectuer les opérations suivantes :  
  
-   Refuser l'appel pour modifier, auquel cas l'éditeur ou le projet doit rester dans l'état \(propre\) inchangé.  
  
-   Indiquez que les données du document doivent être rechargées.  Pour un projet, l'environnement recharge les données du projet.  Un éditeur doit recharger les données à partir de le disque via son implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> .  Dans le cas, le contexte dans le projet ou l'éditeur peut changer lorsque les données sont rechargement.  
  
 Il s'agit d'une tâche complexe et difficile à rattraper des appels adaptés d' `IVsQueryEditQuerySave2::QueryEditFiles` sur une base de code.  Par conséquent, ces appels doivent être intégrés pendant la création du projet ou dans l'éditeur.  
  
## Demander l'autorisation d'enregistrer un fichier  
 avant un projet ou un éditeur enregistre un fichier, il doit appeler l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> ou l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>.  Pour les fichiers projet, ces appels sont automatiquement remplis par la solution, qui sait lorsque enregistrer un fichier projet.  Les éditeurs sont chargées de créer ces appels à moins que l'implémentation d'un éditeur d' `IVsPersistDocData2` utilise l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>de fonction d'assistance.  Si votre éditeur implémente `IVsPersistDocData2` de cette façon, l'appel à `IVsQueryEditQuerySave2::QuerySaveFile` ou à `IVsQueryEditQuerySave2::QuerySaveFiles` est effectuée pour vous.  
  
> [!NOTE]
>  Faites toujours ces appels de préemption\-qu'est, à un moment où votre éditeur peut accepter une annulation.  
  
## Demander l'autorisation d'ajouter, de supprimer, ou renommer des fichiers du projet  
 Avant qu'un projet puisse ajouter, renommer, ou supprimer un fichier ou un répertoire, il doit appeler la méthode appropriée d' `IVsTrackProjectDocuments2::OnQuery*` pour demander l'autorisation de l'environnement.  Si l'autorisation est accordée, le projet doit effectuer l'opération et appeler la méthode appropriée d' `IVsTrackProjectDocuments2::OnAfter*` pour informer l'environnement que l'opération est terminée.  Le projet doit appeler les méthodes d'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> pour tous les fichiers \(par exemple, les fichiers spécifiques\) et pas seulement les fichiers parents.  les appels de fichier sont obligatoires, mais les appels de répertoire sont facultatifs.  Si votre projet contient des informations sur le répertoire, il doit appeler les méthodes appropriées d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> , mais s'il n'a pas ces informations, l'environnement déduit des informations sur le répertoire.  
  
 Le projet ne doit pas appeler les méthodes d' `IVsTrackProjectDocuments2` au projet ouvertes ou se ferment.  Les écouteurs qui souhaitent ces informations au démarrage peuvent attendre l'événement d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> et pour itérer la solution pour rechercher les informations dont ils ont besoin.  Lors de l'arrêt, ces informations ne sont pas nécessaires.  `IVsTrackProjectDocuments2` est fourni d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Pour chaque ajoutez, renommer, et supprimez l'action, il existe une méthode d' `OnQuery*` et une méthode d' `OnAfter*` .  Appelez la méthode d' `OnQuery*` pour demander l'autorisation d'ajouter, renommer, ou supprimer le fichier ou le répertoire.  Appelez la méthode d' `OnAfter*` après le fichier ou le répertoire a été ajouté, renommé, ou supprimé et l'état du projet reflète le nouvel état.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Prise en charge du contrôle de code Source](../../extensibility/internals/supporting-source-control.md)