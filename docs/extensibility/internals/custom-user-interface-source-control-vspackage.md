---
title: Interface utilisateur personnalisée (Source Control VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708931"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface utilisateur personnalisée (contrôle source VSPackage)
Un VSPackage déclare ses éléments de menu et leurs états par défaut par le biais de la table de commande Visual Studio *(.vsct)* fichier. L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) affiche les éléments du menu dans leurs états par défaut jusqu’à ce que le VSPackage soit chargé. Par la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> suite, la méthode est appelée pour activer ou désactiver les éléments du menu.

 Un VSPackage peut définir une clé de registre de sorte que le VSPackage peut être automatiquement chargé en fonction d’une interface utilisateur de commande (interface utilisateur) contexte, bien qu’en général un contrôle source VSPackage devrait charger sur demande au lieu de simplement passer à un contexte particulier d’interface utilisateur. Pour plus d’informations sur la clé du registre **AutoLoadPackages,** voir [Gérer VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>ASSURANCE-chômage VSPackage
 Un paquet de contrôle source est implémenté comme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]un VSPackage et n’utilise aucune interface utilisateur à partir de . Chaque contrôle source VSPackage doit spécifier ses propres éléments d’interface utilisateur tels que les éléments de menu, les groupes de menu, les fenêtres d’outils, les barres d’outils, et toute interface utilisateur requise pour définir les options spécifiques au contrôle source VSPackage. Ces éléments d’interface utilisateur peuvent être activés de façon statique ou dynamique. Les éléments statiques de l’interface utilisateur sont définis dans un fichier *.vsct* et sont affichés si le VSPackage est chargé ou non. Les éléments dynamiques de l’interface utilisateur peuvent être <xref:EnvDTE.Constants.vsContextNoSolution>visibles en fonction d’un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> contexte particulier d’interface utilisateur de commande, tel que, ou à la suite d’un appel à la méthode. La visibilité des éléments d’interface utilisateur dynamique est conforme à la stratégie de chargement retardé des VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Contraintes d’assurance-chômage sur le contrôle des sources VSPackages
 Étant donné que le contrôle source VSPackage ne peut pas être retiré de l’IDE une fois qu’il est chargé, le VSPackage doit être en mesure d’entrer dans un état inactif. Lorsqu’un VSPackage reçoit une notification indiquant qu’il n’est plus actif, le VSPackage désactive son interface utilisateur et ignore toute interaction externe IDE. La mise en œuvre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> de la méthode par le VSPackage doit masquer les commandes lorsque le VSPackage n’est pas actif.

 Chaque contrôle source VSPackage `IVsSccProvider` doit implémenter l’interface. Deux méthodes sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> l’interface, et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, doit être mis en œuvre par le VSPackage.

 Le contrôle source VSPackage peut avoir souscrit à divers <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>événements <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>IDE, qui sont mis en œuvre par le , , et ainsi de suite. En outre, le VSPackage peut avoir mis en œuvre des interfaces de rappel compatibles avec le registre, telles que le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Ces interfaces doivent toutes être ignorées lorsqu’elles sont inactives.

 La liste suivante montre les interfaces affectées par l’état actif d’un contrôle source VSPackage :

- Suivre les événements des documents de projet.

- Événements de solution.

- Interfaces de persistance de la solution. Lorsqu’ils sont inactifs, les paquets ne doivent pas écrire aux fichiers *.sln* et *.suo.*

- Extensions de propriété.

  Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> interfaces requises et, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>ainsi que toutes les interfaces facultatives associées au contrôle de la source, ne sont pas appelées lorsque le contrôle source VSPackage est inactif.

  Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] démarre, définit le contexte de l’interface utilisateur de commande à l’ID de l’ID de contrôle source par défaut actuel VSPackage ID. Cela provoque l’interface utilisateur statique du contrôle source actif VSPackage à apparaître dans l’IDE sans réellement charger le VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pauses pour le VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> s’inscrire à travers l’avant qu’il ne fait tous les appels à la VSPackage.

  Le tableau suivant décrit des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détails spécifiques sur la façon dont l’IDE cache différents éléments d’interface utilisateur.

| Article d’interface utilisateur | Description |
| - | - |
| Menus et barres d’outils | Le paquet de contrôle source doit définir le menu initial et les états de visibilité de la barre d’outils à l’ID du paquet de contrôle source dans la section [VisibilitéConstraints](../../extensibility/visibilityconstraints-element.md) du fichier *.vsct.* Cela permet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’IDE de définir l’état des éléments du menu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> de manière appropriée sans charger le VSPackage et appeler une mise en œuvre de la méthode. |
| Fenêtres d’outil | Le contrôle source VSPackage cache toutes les fenêtres d’outils qu’il possède lorsqu’il est rendu inactif. |
| Ressources d’options spécifiques à VSPackage | La clé du registre **HKLM-SOFTWARE-Microsoft-VisualStudio-X.Y-ToolsOptionsPages-VisibilityCmdUIContexts** permet à un VSPackage de définir les contextes dans lesquels il nécessite l’affichage de ses pages d’options. Une inscription au registre sous cette clé devrait être créée en utilisant l’ID de service (SID) du service de contrôle à la source et en lui attribuant une valeur DWORD de 1. Chaque fois qu’un événement d’interface utilisateur se produit dans un contexte avec lequel le contrôle source VSPackage est enregistré, le VSPackage sera appelé s’il est actif. |

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Gérer VSPackages](../../extensibility/managing-vspackages.md)
