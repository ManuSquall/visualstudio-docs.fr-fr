---
title: Interface utilisateur personnalisée (VSPackage de contrôle de code source) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708931"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interface utilisateur personnalisée (VSPackage de contrôle de code source)
Un VSPackage déclare ses éléments de menu et leurs États par défaut par le biais du fichier de table de commandes Visual Studio (*. vsct*). L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) affiche les éléments de menu dans leur état par défaut jusqu’à ce que le VSPackage soit chargé. Par la suite, la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode est appelée pour activer ou désactiver les éléments de menu.

 Un VSPackage peut définir une clé de Registre afin que le VSPackage puisse être chargé automatiquement en fonction d’un contexte d’interface utilisateur de commande, même si un VSPackage de contrôle de code source doit généralement être chargé à la demande au lieu de basculer simplement vers un contexte d’interface utilisateur particulier. Pour plus d’informations sur la clé de Registre **AutoLoadPackages** , consultez [gérer les VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interface utilisateur du VSPackage
 Un package de contrôle de code source est implémenté en tant que VSPackage et n’utilise pas d’interface utilisateur à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Chaque VSPackage de contrôle de code source doit spécifier ses propres éléments d’interface utilisateur, tels que les éléments de menu, les groupes de menus, les fenêtres outil, les barres d’outils et toute interface utilisateur requise pour définir des options spécifiques au VSPackage de contrôle de code source. Ces éléments d’interface utilisateur peuvent être activés de manière statique ou dynamique. Les éléments d’interface utilisateur statiques sont définis dans un fichier *. vsct* et sont affichés si le VSPackage est chargé ou non. Les éléments d’interface utilisateur dynamiques peuvent être visibles en fonction d’un contexte d’interface utilisateur de commande particulier, tel que <xref:EnvDTE.Constants.vsContextNoSolution> , ou du résultat d’un appel à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode. La visibilité des éléments d’interface utilisateur dynamiques est conforme à la stratégie de chargement différé des VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Contraintes de l’interface utilisateur sur les VSPackages de contrôle de code source
 Étant donné que le VSPackage de contrôle de code source ne peut pas être supprimé de l’IDE après son chargement, le VSPackage doit être en mesure d’entrer dans un état inactif. Lorsqu’un VSPackage reçoit une notification indiquant qu’il n’est plus actif, le VSPackage désactive son interface utilisateur et ignore toute interaction de l’IDE externe. L’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode doit masquer les commandes lorsque le VSPackage n’est pas actif.

 Chaque VSPackage de contrôle de code source doit implémenter l' `IVsSccProvider` interface. Deux méthodes sur l’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , doivent être implémentées par le VSPackage.

 Le VSPackage de contrôle de code source peut s’être abonné à différents événements IDE, qui sont implémentés par <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> , et ainsi de suite. En outre, le VSPackage peut avoir implémenté des interfaces de rappel compatibles avec le registre, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Ces interfaces doivent toutes être ignorées lorsqu’elles sont inactives.

 La liste suivante répertorie les interfaces affectées par l’état actif d’un VSPackage de contrôle de code source :

- Effectue le suivi des événements de documents de projet.

- Événements de la solution.

- Interfaces de persistance de solution. Lorsqu’ils sont inactifs, les packages ne doivent pas écrire dans les fichiers *. sln* et *. suo* .

- Extendeurs de propriété.

  Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> interfaces requises et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , ainsi que toutes les interfaces facultatives associées au contrôle de code source, ne sont pas appelées lorsque le VSPackage de contrôle de code source est inactif.

  Au démarrage de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] définit le contexte de l’interface utilisateur de la commande sur l’ID de l’ID du VSPackage de contrôle de code source par défaut actuel. Cela entraîne l’affichage de l’interface utilisateur statique du VSPackage de contrôle de code source actif dans l’IDE sans le chargement du VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] met en pause le VSPackage pour s’inscrire auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> avant de procéder à des appels au VSPackage.

  Le tableau suivant décrit des détails spécifiques sur la façon dont l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE masque les différents éléments d’interface utilisateur.

| Élément d’interface utilisateur | Description |
| - | - |
| Menus et barres d’outils | Le package de contrôle de code source doit définir les États de visibilité initiale des menus et des barres d’outils sur l’ID du package de contrôle de code source dans la section [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) du fichier *. vsct* . Cela permet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’IDE de définir correctement l’état des éléments de menu sans charger le VSPackage et appeler une implémentation de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode. |
| Fenêtres d’outil | Le VSPackage de contrôle de code source masque toutes les fenêtres d’outils qu’il détient lorsqu’il est rendu inactif. |
| Pages d’options spécifiques au VSPackage de contrôle de code source | La clé de Registre **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** permet à un VSPackage de définir les contextes dans lesquels les pages d’options doivent être affichées. Une entrée de Registre sous cette clé doit être créée à l’aide de l’ID de service (SID) du service de contrôle de code source et en lui assignant une valeur DWORD de 1. Chaque fois qu’un événement d’interface utilisateur se produit dans un contexte avec lequel le VSPackage de contrôle de code source est inscrit, le VSPackage est appelé s’il est actif. |

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Gérer VSPackages](../../extensibility/managing-vspackages.md)
