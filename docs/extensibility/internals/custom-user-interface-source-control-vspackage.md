---
title: L’Interface utilisateur personnalisée (VSPackage de contrôle de code Source) | Microsoft Docs
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
ms.openlocfilehash: 0de4c08857fd1d25c3dabdcdf06daad362dd13ad
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497576"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface utilisateur personnalisée (contrôle de source de package Visual Studio)
Un VSPackage déclare ses éléments de menu et leurs États par défaut par le biais du tableau de commandes de Visual Studio (*.vsct*) fichier. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) affiche les éléments de menu dans leur état par défaut jusqu'à ce que le VSPackage est chargé. Par la suite, le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est appelée pour activer ou désactiver des éléments de menu.  
  
 Un VSPackage peut définir une clé de Registre pour le VSPackage peut être chargé automatiquement en fonction d’un contexte d’interface (UI) de commande utilisateur, bien que généralement un contrôle de source VSPackage doit se charger à la demande au lieu de simplement passer à un contexte particulier de l’interface utilisateur. Pour plus d’informations sur la **AutoLoadPackages** Registre clé, consultez [gérer les VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interface utilisateur du VSPackage  
 Un package de contrôle de code source est implémenté comme un VSPackage et n’utilise pas d’interface utilisateur à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Chaque contrôle de code source VSPackage doit spécifier ses propres éléments d’interface utilisateur tels que les éléments de menu, les groupes de menus, les fenêtres Outil, les barres d’outils et les toute interface utilisateur requis pour définir des options spécifiques pour le VSPackage de contrôle de code source. Ces éléments d’interface utilisateur peuvent être activées de manière statique ou dynamique. Éléments d’interface utilisateur statiques sont définis dans un *.vsct* fichier et s’affichent si le VSPackage est chargé ou non. Éléments d’interface utilisateur dynamiques peuvent être visibles en fonction d’un contexte d’interface utilisateur de commande particulière, tel que <xref:EnvDTE.Constants.vsContextNoSolution>, ou en tant que le résultat d’un appel à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode). La visibilité des éléments d’interface utilisateur dynamiques est conforme à la stratégie pour un chargement différé de VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Contraintes d’interface utilisateur sur le contrôle de code source VSPackages  
 Étant donné que le VSPackage de contrôle de code source ne peut pas être supprimé à partir de l’IDE après que qu’il est chargé, le VSPackage doit être en mesure d’entrer dans un état inactif. Quand un VSPackage reçoit une notification qu’il n’est plus active, le VSPackage désactive son interface utilisateur et ignore toute interaction IDE externe. Implémentation du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode doit masquer les commandes lorsque le VSPackage n’est pas actif.  
  
 Chaque contrôle de code source VSPackage doit implémenter le `IVsSccProvider` interface. Deux méthodes sur l’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, doit être implémentée par le VSPackage.  
  
 Le contrôle de code source VSPackage peut-être être abonnés à divers événements IDE, qui sont implémentées par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, et ainsi de suite. En outre, le VSPackage a peut-être implémenté les interfaces de rappel prenant en charge le Registre, tel que le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Ces interfaces doivent être tous ignorés lorsqu’elle est inactive.  
  
 La liste suivante présente les interfaces affectés par l’état actif d’un VSPackage de contrôle de code source :  
  
-   Suivre les événements de documents de projet.  
  
-   Événements de solution.  
  
-   Interfaces de persistance de solution. Lorsqu’elle est inactive, les packages ne doivent pas écrire dans *.sln* et *.suo* fichiers.  
  
-   Extendeurs de propriété.  
  
 Requis <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, et également toutes les interfaces facultatifs associés au contrôle de code source, ne sont pas appelés lorsque le contrôle de code source VSPackage est inactif.  
  
 Lorsque le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE démarre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] définit le contexte de l’interface utilisateur de commande à l’ID du contrôle de source par défaut actuel ID de package Visual Studio. Cela entraîne l’interface utilisateur statique du contrôle source active VSPackage apparaissent dans l’IDE sans réellement charger le VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] met en pause pour le VSPackage à inscrire avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> avant qu’il effectue des appels au VSPackage.  
  
 Le tableau suivant décrit les détails spécifiques sur la façon dont [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE masque les différents éléments d’interface utilisateur.  
  
|Élément d’interface utilisateur|Description|  
|-------------|-----------------|  
|Menus et barres d’outils|Le package de contrôle de code source doit définir les États de visibilité initiales de menu et barre d’outils à l’ID de package de contrôle de source dans le [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section de la *.vsct* fichier. Cela permet la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pour définir l’état des éléments de menu de manière appropriée sans charger le VSPackage et appeler une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (méthode).|  
|Fenêtres d’outil|Le VSPackage de contrôle de code source masque toutes les fenêtres Outil qu’il détient lorsqu’elle est convertie inactive.|  
|Pages d’options de contrôle de code source spécifiques VSPackage|La clé de Registre **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** permet un VSPackage définie les contextes dans lesquels il requiert ses pages d’options à afficher. Une entrée de Registre sous cette clé devra être créée à l’aide de l’ID (SID) du service de contrôle de source de service et lui assigner une valeur DWORD de 1. Chaque fois qu’un événement d’interface utilisateur produit dans un contexte VSPackage est inscrit avec le contrôle de code source, le VSPackage est appelé si elle est active.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gérer les packages VS](../../extensibility/managing-vspackages.md)