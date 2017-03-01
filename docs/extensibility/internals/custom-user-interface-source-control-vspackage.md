---
title: "L’Interface utilisateur personnalisée (Source contrôle VSPackage) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface utilisateur personnalisée (VSPackage du contrôle de code Source)
Un VSPackage déclare ses éléments de menu et leur état par défaut via le fichier de la Table de commandes de Visual Studio (.vsct). Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) affiche les éléments de menu dans leur état par défaut jusqu'à ce que le VSPackage est chargé. Par la suite, le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>méthode est appelée pour activer ou désactiver des éléments de menu.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Un VSPackage peut définir une clé de Registre pour le VSPackage peut être chargé automatiquement en fonction d’un contexte d’interface graphique utilisateur commande, bien qu’en général, un contrôle de source VSPackage doit se charger à la demande au lieu de simplement passer à un contexte de l’interface utilisateur spécifique. Pour plus d’informations sur la clé de Registre AutoLoadPackages, consultez [la gestion de packages VS](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interface utilisateur du package VS  
 Un package de contrôle de code source est implémenté comme un VSPackage et n’utilise pas d’interface utilisateur à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Chaque contrôle de code source VSPackage doit spécifier ses propres éléments d’interface utilisateur tels que les éléments de menu, groupes de menus, fenêtres d’outils, barres d’outils et d’interface utilisateur requis pour définir des options spécifiques pour le contrôle de code source VSPackage. Ces éléments d’interface utilisateur peuvent être activées de manière statique ou dynamique. Éléments d’interface utilisateur statiques sont définis dans un fichier .vsct et sont affichés le VSPackage est chargé ou non. Éléments d’interface utilisateur dynamiques peuvent être visibles en fonction d’un contexte de l’interface utilisateur de commande particulière, tels que <xref:EnvDTE.Constants.vsContextNoSolution>, ou à la suite d’un appel à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>méthode.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> La visibilité des éléments d’interface utilisateur dynamiques est conforme à la stratégie pour le chargement différé des VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Contraintes de l’interface utilisateur sur les VSPackages de contrôle de code Source  
 Comme le contrôle de code source VSPackage ne peut pas être supprimé à partir de l’IDE après son chargement, le VSPackage doit être en mesure d’entrer dans un état inactif. Lorsqu’un VSPackage reçoit une notification qu’il n’est plus active, le VSPackage désactive son interface utilisateur et ignore l’interaction externe de l’IDE. Implémentation du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>méthode doit masquer les commandes lorsque le VSPackage n’est pas actif.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Chaque contrôle de code source VSPackage doit implémenter le `IVsSccProvider` interface. Deux méthodes de l’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, doit être implémentée par le VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 Le contrôle de code source VSPackage peut-être être abonnés à divers événements IDE, qui sont implémentées par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, et ainsi de suite.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> En outre, le VSPackage a peut-être implémenté les interfaces de rappel activé de Registre, telles que le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Ces doivent tous être ignorés lorsqu’elle est inactive.  
  
 La liste suivante affiche les interfaces affectés par l’état actif d’un contrôle de source de package VS :  
  
-   Suivre les événements de Documents du projet.  
  
-   Événements de la solution.  
  
-   Interfaces de persistance de solution. Lorsqu’elle est inactive, les packages ne doivent pas écrire dans les fichiers .sln et .suo.  
  
-   Extendeurs de propriétés.  
  
 Requis <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, et également des interfaces facultatives associées au contrôle de code source, ne sont pas appelés lorsque le contrôle de code source VSPackage est inactive.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 Lors de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE démarre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] définit le contexte de l’interface utilisateur de commande à l’ID du contrôle de source par défaut actuel VSPackage ID. Ainsi, l’interface utilisateur statique du contrôle source active VSPackage apparaissent dans l’IDE sans réellement charger le VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]s’interrompt pendant le VSPackage auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>avant d’effectuer des appels vers le VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 Le tableau suivant décrit les détails spécifiques sur la façon dont [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE masque les différents éléments de l’interface utilisateur.  
  
|Élément d’interface utilisateur|Description|  
|-------------|-----------------|  
|Menus et barres d’outils|Le package de contrôle de code source doit définir les États de visibilité initiales de menu et barre d’outils à l’ID de package de contrôle de code source dans le [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section du fichier .vsct. Cela permet la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pour définir l’état des éléments de menu de façon appropriée sans le chargement du package VS et appeler une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>méthode.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|Fenêtres d’outil|Le contrôle de code source VSPackage masque toutes les fenêtres Outil qu’il détient lorsqu’elle devient inactive.|  
|Page d’options de contrôle de code source spécifiques VSPackage|La clé de Registre HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts permet de définir les contextes dans lesquels il requiert ses pages d’options à afficher un VSPackage. Une entrée de Registre sous cette clé devra être créé en utilisant le service ID (SID) du service de contrôle de source et en lui assignant une valeur DWORD de 1. Chaque fois qu’un événement d’interface utilisateur produit dans un contexte VSPackage est enregistré avec le contrôle de code source, le VSPackage sera appelé si elle est active.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [La gestion de packages VS](../../extensibility/managing-vspackages.md)
