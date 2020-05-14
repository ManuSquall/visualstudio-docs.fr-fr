---
title: Services et interfaces connexes (Source Control VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705624"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Services et interfaces associés (VSPackage de contrôle de code source)
Cette section répertorie toutes les interfaces [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]liées à VSPackage de contrôle source dans le . Le contrôle source VSPackage implémente certaines de ces interfaces et en utilise d’autres pour accomplir des tâches de contrôle des sources.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implémentées par et pour les VSPackages de contrôle des sources
 Les interfaces suivantes sont [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]décrites dans le , et le contrôle source VSPackage implémente un sous-ensemble d’entre eux en fonction de son ensemble de fonctionnalités souhaitées. Certaines interfaces sont marquées au besoin et doivent être implémentées par chaque contrôle source VSPackage.

 Pour les interfaces qu’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paquet ne met pas en œuvre, fournit une implémentation par défaut. Notez que la mise en œuvre par défaut est conçue pour le cas lorsqu’aucun VSPackage n’est enregistré et qu’aucun projet n’est contrôlé. Un contrôle source correctement écrit VSPackage implémente toutes les interfaces nécessaires plutôt que de le laisser à la mise en œuvre par défaut de ces interfaces.

 Un contrôle source VSPackage doit implémenter un service privé qui encapsule une partie ou la totalité des interfaces suivantes.

 Les interfaces sont les :

- Requis : L’entité appropriée (contrôle source VSPackage, Source Control Stub, projet) doit implémenter l’interface.

- Recommandé: L’entité doit implémenter cette interface; autrement, la fonctionnalité de contrôle des sources peut être limitée.

- Facultatif : l’entité peut implémenter cette interface pour fournir un ensemble de fonctionnalités plus riche.

| Interface | Objectif | Mis en œuvre par | Implémenter? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Les éditeurs appellent cette interface avant de modifier ou d’enregistrer un fichier. Le contrôle source VSPackage peut vérifier le fichier ou refuser l’opération si la caisse échoue. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Cette interface fournit des fonctionnalités de contrôle source de base pour les projets, tels que l’enregistrement et le non-enregistrement des projets avec le contrôle de la source et de fournir un soutien pour les glyphes de contrôle de source de base. | Contrôle des sources VSPackage | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Cette interface est obtenue <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> à <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> partir de l’utilisation de `IVsHierarchy` `IVsSccProject2`la fonction, ou simplement en jetant l’objet implémentant à . Il est utilisé pour obtenir les fichiers sous contrôle source dans un projet ou pour informer le projet de l’état ou de l’emplacement actuel du contrôle de la source. | Projet | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Le module d’intégration utilise cette interface pour définir le VSPackage actif actuel. | Contrôle des sources VSPackage | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Cette interface est basée sur un modèle d’abonnement. N’importe quel VSPackage peut signaler qu’il veut recevoir des événements de documents et être informé par la coquille sur les événements qui sont sur le point de se produire. Il est implémenté et géré par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], `IVsTrackProjectDocumentsEvents2` qui à son tour passe les événements de mise en œuvre de la VSPackage. | Contrôle des sources Stub | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Cette interface fournit le traitement par lots, les `OnQueryAddFiles` opérations synchronisées de lecture/écriture, et une méthode avancée. | Contrôle des sources Stub | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Solution Explorer** et les projets appellent cette interface lorsque de nouveaux fichiers sont ajoutés aux projets, ou lorsque les fichiers et dossiers sont renommés ou supprimés des projets. Le contrôle source VSPackage peut consulter le fichier du projet ou annuler l’opération. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Solution Explorer** et les projets appellent cette interface en réponse aux appels effectués aux méthodes de l’interface IVstrackProjectDocuments3. Le contrôle source VSPackage peut suivre les opérations en lots, les opérations `OnQueryAddFiles` synchronisées de lecture/écriture, et travailler avec une méthode plus avancée. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Cette interface fournit un soutien de gestion de l’enrôlement pour les projets Web. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Cette interface est utilisée pour récupérer ToolTips pour les fichiers contrôlés par la source dans les projets. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Cette interface fournit le support d’extension de l’espace de nom. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Le VSPackage utilise cette interface pour intégrer une extension de namespace dans les **boîtes de**dialogue New , **Open**, ou **Save.** Par conséquent, les projets peuvent être automatiquement ajoutés au contrôle des sources sur la création, ou ajoutés au contrôle des sources lorsqu’une opération d’enregistrement est en vigueur. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Le VSPackage utilise cette interface pour définir des glyphes supplémentaires comme glyphes de contrôle source pour les nœuds dans **Solution Explorer**. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | La boîte de dialogue **Add** pour les projets Web utilise cette interface. Il fournit des méthodes pour naviguer pour un emplacement de contrôle source et pour l’ouverture d’un projet Web précédemment ajouté dans le référentiel de contrôle source à cet endroit. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Cette interface fournit un support pour le chargement asynchrone (arrière-plan) des projets à partir du contrôle source. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Cette interface permet aux projets de suivre l’évolution du chargement asynchrone initié par <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Projet | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Cette interface permet à l’IDE d’interroger le contrôle source actif VSPackage. L’IDE interroge la valeur des paramètres de contrôle source qui ont un sens même lorsqu’il n’y a pas de contrôle source actif VSPackage enregistré. Cette interface est implémentée et manipulée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Contrôle des sources Stub | Obligatoire |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Cette interface est utilisée dans l’enregistrement du contrôle source VSPackage. | Contrôle des sources Stub | Obligatoire |
| <xref:EnvDTE.SourceControl> | Cette interface est utilisée dans l’automatisation. En tant que tel, il expose uniquement les fonctions qui peuvent être exécutées sans afficher d’interface utilisateur. | Contrôle des sources VSPackage | Facultatif |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Cette interface est utilisée pour enregistrer les paramètres de contrôle source dans le fichier solution (.sln). Les paramètres comprennent l’emplacement du contrôle source et les indicateurs d’état de contrôle des sources. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Cette interface est utilisée pour enregistrer les paramètres de contrôle source dans le fichier options de solution (.suo). Cela peut inclure des paramètres de contrôle source spécifiques à l’utilisateur tels que l’emplacement de l’enrôlement de l’utilisateur actuel. | Contrôle des sources VSPackage | Recommandé |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Cette interface est utilisée pour surveiller les événements afin d’effectuer des opérations telles que la vérification des fichiers de projet avant de fermer des solutions, ou d’obtenir de nouveaux fichiers à partir du contrôle source lors de l’ouverture d’un projet. | Contrôle des sources VSPackage | Recommandé |

## <a name="see-also"></a>Voir aussi
- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
