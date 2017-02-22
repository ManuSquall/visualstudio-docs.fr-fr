---
title: "Comment : impl&#233;menter des projets imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets imbriqués, l'implémentation"
  - "imbrication de projets (Visual Studio SDK),"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment : impl&#233;menter des projets imbriqu&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous créez un type imbriqué de projet plusieurs étapes supplémentaires qui doivent être implémentées.  Prend parentes d'un projet pour certaines des mêmes responsabilités que la solution a de ses projets \(enfant\) imbriqués.  le projet parent est un conteneur de projets semblables à une solution.  En particulier, il existe plusieurs événements qui doivent être déclenchés par la solution et par les projets parents de générer la hiérarchie des projets imbriqués.  ces événements sont décrits dans le processus suivant pour créer des projets imbriqués.  
  
### pour créer des projets imbriqués  
  
1.  L'environnement \(IDE\) de développement intégré charge les informations parentes du fichier projet et le démarrage du projet en appelant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> .  le projet parent est créé et ajouté à la solution.  
  
    > [!NOTE]
    >  À ce stade, il est trop tôt dans le processus du projet parent crée le projet imbriqué parce que le projet parent doit être créé avant les projets enfants puissent être créés.  En suivant cette séquence, le projet parent peut appliquer des paramètres aux projets enfants et les projets enfants peuvent obtenir les informations les projets parents si nécessaire.  Cette séquence est si elle est activée nécessaire par les clients tels que le contrôle et \(SCC\) l'explorateur de solutions de code source.  
  
     Le projet parent doit attendre que la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> à appeler par l'IDE avant de pouvoir créer son projets \(enfant\) imbriqués.  
  
2.  L'IDE appelle `QueryInterface` sur le projet parent pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>.  Si cet appel réussit, l'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> de parent pour ouvrir tous les projets imbriqués pour le projet parent.  
  
3.  Le projet parent appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> pour informer les écouteurs que les projets imbriqués sont sur le point d'être créé.  Le SCC, par exemple, écoutent ces événements pour savoir si les étapes du processus de création de solution et de projet se produisent dans l'ordre.  Si les étapes se produisent en panne, la solution ne peut pas être enregistrée avec le contrôle de code source correctement.  
  
4.  le projet parent appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> ou la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> sur chacun de ses projets enfants.  
  
     Vous passez <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> à la méthode d' `AddVirtualProject` pour indiquer que le projet \(imbriqué\) virtuel doit être ajouté à la fenêtre de projet, exclue de la génération, ajoutée au contrôle de code source, et ainsi de suite.  `VSADDVPFLAGS` vous permet de contrôler la visibilité du projet imbriqué et indiquer quelle fonctionnalité est associée.  
  
     Si vous rechargez un projet enfant précédemment existant dont un GUID du projet stocké dans le fichier projet parent du projet, le projet parent appelle `AddVirtualProjectEx`.  La seule différence entre `AddVirtualProject` et `AddVirtualProjectEX` est qu' `AddVirtualProjectEX` possède un paramètre pour activer le projet parent de spécifier par instance `guidProjectID` pour le projet enfant permette à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> et à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> pour fonctionner correctement.  
  
     S'il n'y a aucun GUID disponible, par exemple lorsque vous ajoutez un nouveau projet imbriqué, la solution crée un pour le projet lorsqu'elle est ajoutée au parent.  Il est de la responsabilité du projet parent de rendre ce GUID du projet dans son fichier projet.  Si vous supprimez un projet imbriqué, un GUID pour ce projet peut également être supprimé.  
  
5.  L'IDE appelle la méthode d' `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` sur chaque projet enfant du projet parent.  
  
     le projet parent doit implémenter `IVsParentProject` si vous souhaitez imbriquer des projets.  Mais le projet parent n'appelle jamais `QueryInterface` pour `IVsParentProject` même si elle a des projets parents au\-dessous.  La solution traite l'appel à `IVsParentProject` et, si elle est implémentée, appelle `OpenChildren` pour créer des projets imbriqués.  `AddVirtualProjectEX` est toujours appelé d' `OpenChildren`.  Il ne doit jamais être appelé par le projet parent de conserver les événements de création de hiérarchie de la commande.  
  
6.  L'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> sur le projet enfant.  
  
7.  Le projet parent appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> pour informer les écouteurs que les projets enfants pour le parent ont été créés.  
  
8.  L'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> sur le projet parent après que tous les projets qu'enfants ont été ouverts.  
  
     S'il n'existe pas, le projet parent crée un GUID pour chaque projet imbriqué en appelant `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid` est une API COM appelée lorsque le GUID doit être créé.  Pour plus d'informations, consultez `CoCreateGuid` et les GUID dans MSDN Library.  
  
     Le projet parent enregistre ce GUID dans son fichier projet à récupérer la prochaine fois qu'il est ouvert dans l'IDE.  Consultez l'étape 4 pour plus d'informations sur l'appel d' `AddVirtualProjectEX` pour récupérer `guidProjectID` pour le projet enfant.  
  
9. La méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> est ensuite appelée pour l'ItemID parent que par convention vous déléguez au projet imbriqué.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> récupère les propriétés du nœud qui imbrique un projet dans lequel vous souhaitez déléguer lorsqu'il est appelé le parent.  
  
     Étant donné que les projets parents et enfants sont instanciés par programme, vous pouvez définir des propriétés pour les projets imbriqués à ce stade.  
  
    > [!NOTE]
    >  Non seulement recevez\-vous les informations de contexte du projet imbriqué, mais vous pouvez également demander si le projet parent a tout contexte pour cet élément en activant <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  De cette façon, vous pouvez ajouter des attributs supplémentaires et des options de menu d'Aide dynamique spécifiques aux projets imbriqués individuels.  
  
10. La hiérarchie est créée pour l'explorateur d'affichage en solution avec un appel à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .  
  
     Vous passez la hiérarchie à l'environnement via `GetNestedHierarchy` pour générer la hiérarchie de l'explorateur d'affichage en solution.  De cette manière, la solution sait que le projet existe et peut être géré pour générer par le gestionnaire de génération, ou peut autoriser les fichiers dans le projet doit être mis sous contrôle de code source.  
  
11. Lorsque tous les projets imbriqués pour Project1 ont été créés, le contrôle est repassé à la solution et le processus se répète pour Project2.  
  
     Ce même processus pour créer des projets imbriqués se produit pour un projet enfant ayant un enfant.  Dans ce cas, si BuildProject1, qui est un enfant de Project1, contenait des projets enfants, ils sont créés après BuildProject1 et avant Project2.  Le processus est récurrente et la hiérarchie est générée de haut en bas.  
  
     Lorsqu'un projet imbriqué est fermé parce que l'utilisateur a fermé la solution ou le projet spécifique elle\-même, l'autre méthode sur `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, est appelée.  Le projet parent encapsule des appels à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> avec l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> et les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> pour informer les écouteurs aux événements de solution que les projets imbriqués sont fermés.  
  
 Les rubriques suivantes traitent plusieurs autres concepts à prendre en considération lorsque vous implémentez des projets imbriqués :  
  
 [Considérations pour décharger et recharger les projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Prise en charge de l'Assistant de projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Mise en œuvre de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Filtrage de la boîte de dialogue AddItem de projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## Voir aussi  
 [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)