---
title: Services et interfaces associés (VSPackage de contrôle de code source)
titleSuffix: ''
description: Découvrez les interfaces associées au contrôle de code source dans le kit de développement logiciel (SDK) Visual Studio. Le package implémente certaines interfaces et utilise d’autres pour le contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6385307c91541204d58228b489160888f79dec85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903331"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Services et interfaces associés (VSPackage de contrôle de code source)

Cette section répertorie toutes les interfaces associées au VSPackage de contrôle de code source dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Le VSPackage de contrôle de code source implémente certaines de ces interfaces et en utilise d’autres pour accomplir des tâches de contrôle de code source.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implémentées par et pour les VSPackages de contrôle de code source

 Les interfaces suivantes sont décrites dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , et le VSPackage de contrôle de code source implémente un sous-ensemble de celles-ci en fonction de l’ensemble de fonctionnalités souhaité. Certaines interfaces sont marquées comme obligatoires et doivent être implémentées par chaque VSPackage de contrôle de code source.

 Pour les interfaces qui ne sont pas implémentées par un package, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit une implémentation par défaut. Notez que l’implémentation par défaut est conçue pour le cas où aucun VSPackage n’est inscrit et qu’aucun projet n’est contrôlé. Un VSPackage de contrôle de code source correctement écrit implémente toutes les interfaces nécessaires plutôt que de le laisser à l’implémentation par défaut de ces interfaces.

 Un VSPackage de contrôle de code source doit implémenter un service privé qui encapsule une partie ou la totalité des interfaces suivantes.

 Les interfaces sont les suivantes :

- Obligatoire : l’entité appropriée (VSPackage de contrôle de code source, stub de contrôle de code source, projet) doit implémenter l’interface.

- Recommandé : l’entité doit implémenter cette interface ; dans le cas contraire, la fonctionnalité de contrôle de code source peut être limitée.

- Facultatif : l’entité peut implémenter cette interface pour fournir un ensemble de fonctionnalités plus riche.

| Interface | Objectif | Implémenté par | Applique? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Les éditeurs appellent cette interface avant de modifier ou d’enregistrer un fichier. Le VSPackage de contrôle de code source peut extraire le fichier ou refuser l’opération en cas d’échec de l’extraction. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Cette interface fournit des fonctionnalités de contrôle de code source de base pour les projets, telles que l’inscription et l’annulation de l’inscription de projets avec le contrôle de code source et la prise en charge des glyphes de contrôle de code source de base. | VSPackage de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Cette interface est obtenue à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> aide de la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> fonction, ou simplement en effectuant un cast de l’objet qui implémente `IVsHierarchy` `IVsSccProject2` . Elle est utilisée pour obtenir les fichiers sous contrôle de code source dans un projet ou pour informer le projet de l’État ou de l’emplacement du contrôle de code source actuel. | Project | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Le module d’intégration utilise cette interface pour définir le VSPackage actif actuel. | VSPackage de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Cette interface est basée sur un modèle d’abonnement. Tout VSPackage peut signaler qu’il souhaite recevoir des événements de document et être avisé par le Shell sur les événements qui sont sur le lieu de se produire. Elle est implémentée et gérée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui, à son tour, passe les événements implémentant le `IVsTrackProjectDocumentsEvents2` au VSPackage. | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Cette interface fournit le traitement par lots, les opérations de lecture/écriture synchronisées et une `OnQueryAddFiles` méthode avancée. | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | Les **Explorateur de solutions** et les projets appellent cette interface lorsque de nouveaux fichiers sont ajoutés aux projets, ou lorsque des fichiers et des dossiers sont renommés ou supprimés de projets. Le VSPackage de contrôle de code source peut extraire le fichier projet ou annuler l’opération. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | Les **Explorateur de solutions** et les projets appellent cette interface en réponse aux appels effectués aux méthodes de l’interface IVstrackProjectDocuments3. Le VSPackage de contrôle de code source peut suivre des opérations par lots, synchroniser des opérations de lecture/écriture et utiliser une méthode plus avancée `OnQueryAddFiles` . | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Cette interface fournit la prise en charge de la gestion de l’inscription pour les projets Web. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Cette interface est utilisée pour récupérer des info-bulles pour les fichiers sous contrôle de code source dans les projets. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Cette interface fournit la prise en charge de l’extension d’espace de noms. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Le VSPackage utilise cette interface pour intégrer une extension d’espace de noms dans les boîtes **de dialogue Nouveau**, **ouvrir** ou **Enregistrer** . Par conséquent, les projets peuvent être automatiquement ajoutés au contrôle de code source lors de la création ou ajoutés au contrôle de code source lorsqu’une opération d’enregistrement est en vigueur. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Le VSPackage utilise cette interface pour définir des glyphes supplémentaires en tant que glyphes de contrôle de code source pour les nœuds dans **Explorateur de solutions**. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | La boîte de dialogue **Ajouter** pour les projets Web utilise cette interface. Il fournit des méthodes pour rechercher un emplacement de contrôle de code source et pour ouvrir un projet Web précédemment ajouté dans le référentiel de contrôle de code source à cet emplacement. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Cette interface fournit la prise en charge du chargement asynchrone (arrière-plan) des projets à partir du contrôle de code source. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Cette interface permet aux projets de suivre la progression du chargement asynchrone initié par <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Cette interface permet à l’IDE d’interroger le VSPackage de contrôle de code source actif. L’IDE interroge la valeur des paramètres de contrôle de code source qui ont une signification même lorsqu’aucun VSPackage de contrôle de code source actif n’est inscrit. Cette interface est implémentée et gérée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Cette interface est utilisée pour inscrire le VSPackage de contrôle de code source. | Stub de contrôle de code source | Obligatoire |
| <xref:EnvDTE.SourceControl> | Cette interface est utilisée dans Automation. Par conséquent, elle expose uniquement les fonctions qui peuvent être exécutées sans afficher d’interface utilisateur. | VSPackage de contrôle de code source | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Cette interface est utilisée pour enregistrer les paramètres de contrôle de code source dans le fichier solution (. sln). Les paramètres incluent l’emplacement du contrôle de code source et les indicateurs d’État du contrôle de code source. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Cette interface est utilisée pour enregistrer les paramètres de contrôle de code source dans le fichier d’options de solution (. suo). Cela peut inclure des paramètres de contrôle de code source spécifiques à l’utilisateur, tels que l’emplacement d’inscription de l’utilisateur actuel. | VSPackage de contrôle de code source | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Cette interface permet de surveiller les événements afin d’effectuer des opérations telles que l’archivage des fichiers projet avant la fermeture de solutions ou l’obtention de nouveaux fichiers à partir du contrôle de code source lors de l’ouverture d’un projet. | VSPackage de contrôle de code source | Recommandé |

## <a name="see-also"></a>Voir aussi
- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
