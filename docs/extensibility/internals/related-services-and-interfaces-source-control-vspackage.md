---
title: Les Services associés et les Interfaces (VSPackage de contrôle de code Source) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9aa9dd59a568ae766a7cd0939c41a4bcd97f640
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337299"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Services et interfaces associés (VSPackage de contrôle de code source)
Cette section répertorie toutes les interfaces associées à un VSPackage dans contrôle de la source de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Le contrôle de code source VSPackage implémente certaines de ces interfaces et d’autres utilise pour accomplir les tâches de contrôle de code source.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implémentées par et pour les VSPackages de contrôle de code Source
 Les interfaces suivantes sont décrites dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], et le contrôle de code source VSPackage implémente un sous-ensemble d'entre elles en fonction de son jeu de fonctionnalités souhaitées. Certaines interfaces sont marqués comme obligatoire et doit être implémentée par chaque VSPackage de contrôle de code source.

 Pour ces interfaces un package n’implémente pas, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit une implémentation par défaut. Notez que l’implémentation par défaut est conçue pour le cas lorsque aucun VSPackage n’est enregistré et aucun projet n’est pas contrôlé. Un contrôle de source correctement écrites VSPackage implémente les interfaces nécessaires plutôt que de le laisser à l’implémentation par défaut de ces interfaces.

 Un VSPackage de contrôle de code source doit implémenter un service privé qui encapsule tout ou partie des interfaces suivantes.

 Les interfaces sont :

- Obligatoire : L’entité appropriée (contrôle de code source VSPackage, Stub de contrôle de code Source, de projet) doit implémenter l’interface.

- Recommandé : L’entité doit implémenter cette interface ; Sinon, les fonctionnalités de contrôle de code source peuvent être limitées.

- Facultatif : l’entité peut implémenter cette interface pour fournir un ensemble de fonctionnalités plus riches.

| Interface | Objectif | Implémenté par | Implémenter ? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Éditeurs appellent cette interface avant de modifier ou de l’enregistrement d’un fichier. Le contrôle de code source VSPackage peut extraire le fichier ou refuser l’opération si l’extraction échoue. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Cette interface fournit des fonctionnalités de contrôle de source de base pour les projets, tels que l’inscription et désinscription des projets avec contrôle de code source et prise en charge pour les glyphes de contrôle de source de base. | Contrôle de code source VSPackage | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Cette interface est obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> à l’aide de la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> (fonction), ou en simplement effectuant un cast de l’objet implémentant `IVsHierarchy` à `IVsSccProject2`. Il est utilisé pour obtenir les fichiers sous contrôle de code source dans un projet ou pour informer le projet de l’état actuel du contrôle de source ou l’emplacement. | Projet | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Le module d’intégration utilise cette interface pour définir le VSPackage actif actuels. | Contrôle de code source VSPackage | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Cette interface est basée sur un modèle d’abonnement. Un VSPackage peut signaler qu’il souhaite recevoir des événements de document et être avertie par le shell sur les événements qui sont sur le point de se produire. Il est implémenté et géré par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], qui passe à son tour les événements implémentant le `IVsTrackProjectDocumentsEvents2` au VSPackage. | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Cette interface fournit le traitement par lots, les opérations de lecture/écriture synchronisé et avancée `OnQueryAddFiles` (méthode). | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **L’Explorateur de solutions** et projets appellent cette interface lorsque de nouveaux fichiers sont ajoutés aux projets, ou lorsque les fichiers et dossiers sont renommés ou supprimés à partir de projets. Le VSPackage de contrôle de code source peut extraire le fichier projet ou annuler l’opération. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **L’Explorateur de solutions** et projets appellent cette interface en réponse aux appels passés aux méthodes de l’interface IVstrackProjectDocuments3. Le contrôle de code source VSPackage peut effectuer le suivi des opérations par lots, synchronisées opérations de lecture/écriture et travailler avec un plus avancés `OnQueryAddFiles` (méthode). | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Cette interface fournit la gestion de l’inscription prend en charge pour les projets Web. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Cette interface est utilisée pour récupérer des info-bulles pour les fichiers sous contrôle de code source dans les projets. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Cette interface fournit l’extension de prise en charge. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Le VSPackage utilise cette interface pour intégrer une extension de l’espace de noms dans le **New**, **Open**, ou **enregistrer** boîtes de dialogue. Par conséquent, les projets peuvent être automatiquement ajoutés au contrôle de code source lors de la création ou ajoutés au contrôle de code source lorsqu’une sauvegarde opération est en vigueur. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Le VSPackage utilise cette interface pour définir des glyphes supplémentaires comme des glyphes de contrôle de code source pour les nœuds dans **l’Explorateur de solutions**. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Le **ajouter** boîte de dialogue pour les projets Web utilise cette interface. Il fournit des méthodes permettant de parcourir un emplacement de contrôle de code source et pour l’ouverture d’un projet Web ajouté précédemment dans le référentiel de contrôle de code source à cet emplacement. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Cette interface prend en charge pour le chargement asynchrone (en arrière-plan) des projets de contrôle de code source. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Cette interface permet aux projets de surveiller la progression du chargement asynchrone lancée par <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Projet | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Cette interface permet à l’IDE interroger le VSPackage de contrôle source active. L’IDE interroge la valeur de paramètres de contrôle de source qui ont une signification même lorsqu’il n’existe aucun contrôle de source active que VSPackage inscrit. Cette interface est implémentée et gérée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Stub de contrôle de code source | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Cette interface est utilisée en inscrivant le VSPackage de contrôle de code source. | Stub de contrôle de code source | Obligatoire |
| <xref:EnvDTE.SourceControl> | Cette interface est utilisée dans automation. Par conséquent, il expose uniquement les fonctions qui peuvent être exécutées sans afficher d’interface utilisateur. | Contrôle de code source VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Cette interface est utilisée pour enregistrer des paramètres de contrôle de la source dans le fichier solution (.sln). Les paramètres incluent l’emplacement de contrôle de source et les indicateurs d’état de contrôle de code source. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Cette interface est utilisée pour enregistrer les paramètres de contrôle de source dans le fichier d’options (.suo) de solution. Cela peut inclure des paramètres de contrôle de source de spécifiques à l’utilisateur comme emplacement de l’inscription de l’utilisateur actuel. | Contrôle de code source VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Cette interface est utilisée pour surveiller les événements afin d’effectuer des opérations telles que l’archivage des fichiers projet avant de fermer les solutions, ou bien les nouveaux fichiers à partir du contrôle de code source lors de l’ouverture d’un projet. | Contrôle de code source VSPackage | Recommandé |

## <a name="see-also"></a>Voir aussi
- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)