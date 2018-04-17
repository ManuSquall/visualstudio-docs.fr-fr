---
title: L’Interface utilisateur personnalisée (VSPackage de contrôle de code Source) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd2361e94e9b1430f5bac99f2e71dc53a02ebf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface utilisateur personnalisée (VSPackage de contrôle de code Source)
Un VSPackage déclare ses éléments de menu et leur état par défaut via le fichier Visual Studio Command Table (.vsct). Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) affiche les éléments de menu dans leur état par défaut jusqu'à ce que le VSPackage est chargé. Par la suite, le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est appelée pour activer ou désactiver des éléments de menu.  
  
 Un VSPackage peut définir une clé de Registre pour le VSPackage peut être chargé automatiquement en fonction d’un contexte d’interface utilisateur commande utilisateur, bien qu’en général, une contrôle de code source VSPackage doit charger à la demande au lieu de simplement passer à un contexte de l’interface utilisateur spécifique. Pour plus d’informations sur la clé de Registre AutoLoadPackages, consultez [la gestion des VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interface utilisateur du VSPackage  
 Un package de contrôle de code source est implémenté comme un VSPackage et n’utilise pas d’interface utilisateur à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Chaque contrôle de code source VSPackage doit spécifier ses propres éléments d’interface utilisateur tels que les éléments de menu, les groupes de menus, les fenêtres Outil, les barres d’outils et toute interface utilisateur requis pour définir des options spécifiques pour le contrôle de code source VSPackage. Ces éléments d’interface utilisateur peuvent être activées de manière statique ou dynamique. Éléments d’interface utilisateur statiques sont définis dans un fichier .vsct et sont affichés si le VSPackage est chargé ou non. Éléments d’interface utilisateur dynamiques peuvent être visibles en fonction d’un contexte de l’interface utilisateur de commande particulière, tel que <xref:EnvDTE.Constants.vsContextNoSolution>, ou en tant que le résultat d’un appel à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode). La visibilité des éléments d’interface utilisateur dynamiques est conforme à la stratégie pour le chargement différé des VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Contraintes d’interface utilisateur sur les packages de contrôle de Source  
 Car le contrôle de code source VSPackage ne peut pas être supprimée à partir de l’IDE après le chargement, le VSPackage doit être en mesure de les entrer dans un état inactif. Quand un VSPackage reçoit une notification qu’il n’est plus active, le VSPackage désactive son interface utilisateur et ignore l’interaction externe de l’IDE. Implémentation du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode doit masquer les commandes quand le VSPackage n’est pas actif.  
  
 Chaque contrôle de code source VSPackage doit implémenter la `IVsSccProvider` interface. Deux méthodes de l’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, doit être implémentée par le VSPackage.  
  
 Le contrôle de code source VSPackage peut-être êtes abonné à différents événements IDE, qui sont implémentées par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, et ainsi de suite. En outre, le VSPackage a peut-être implémenté les interfaces compatibles sur le Registre de rappel, tels que le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Ces doivent tous être ignorés lorsqu’elle est inactive.  
  
 La liste suivante montre les interfaces affectés par l’état actif d’un contrôle de code source VSPackage :  
  
-   Suivre les événements de Documents du projet.  
  
-   Événements de la solution.  
  
-   Interfaces de persistance de solution. Lorsqu’elle est inactive, les packages ne doivent pas écrire dans les fichiers .sln et .suo.  
  
-   Extensions de la propriété.  
  
 Requis <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, et également les interfaces facultatif associés au contrôle de code source, ne sont pas appelés lorsque le contrôle de code source VSPackage est inactif.  
  
 Lorsque le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE démarre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] définit le contexte de l’interface utilisateur de commande à l’ID du VSPackage ID du contrôle de source de valeur par défaut en cours Cela entraîne l’interface utilisateur statique du contrôle source active VSPackage apparaissent dans l’IDE sans réellement charger le VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Suspend pour le VSPackage auprès [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> avant qu’il effectue des appels pour le VSPackage.  
  
 Le tableau suivant décrit les détails spécifiques sur la façon dont [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE masque les différents éléments d’interface utilisateur.  
  
|Élément d’interface utilisateur|Description|  
|-------------|-----------------|  
|Menus et barres d’outils|Le package de contrôle de code source doit définir les états initiaux de visibilité des menus et barre d’outils à l’ID de package de contrôle de code source dans le [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section du fichier .vsct. Cela permet la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pour définir l’état des éléments de menu de manière appropriée sans charger le VSPackage et appeler une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode).|  
|Fenêtres d’outil|Le contrôle de code source VSPackage masque toutes les fenêtres Outil qu'il est propriétaire lorsqu’il est rendu inactif.|  
|Pages d’options de contrôle de code source spécifiques VSPackage|La clé de Registre HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts permet à un VSPackage de définir les contextes dans lesquels il requiert ses pages d’options à afficher. Une entrée de Registre sous cette clé devra être créée à l’aide de l’ID (SID) du service de contrôle de source de service et lui assigner une valeur DWORD de 1. Chaque fois qu’un événement de l’interface utilisateur produit dans un contexte le VSPackage est inscrit auprès du contrôle de code source, le VSPackage sera appelé si elle est active.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gestion de VSPackages](../../extensibility/managing-vspackages.md)