---
title: "Les Services associés et les Interfaces (Source contrôle VSPackage) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Les Services associés et les Interfaces (VSPackage du contrôle de code Source)
Cette section répertorie tous les la source de contrôler les interfaces associées aux VSPackage dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Le contrôle de code source VSPackage implémente certaines de ces interfaces et d’autres utilise pour accomplir les tâches de contrôle de code source.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implémentées par et pour les VSPackages de contrôle de code Source  
 Les interfaces suivantes sont décrites dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], et le contrôle de code source VSPackage implémente un sous-ensemble d'entre eux en fonction de son jeu de fonctionnalités souhaitées. Certaines interfaces sont marqués comme obligatoire et doit être implémentée par chaque contrôle de code source VSPackage.  
  
 Pour les interfaces qui n’implémente pas d’un package, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit une implémentation par défaut. Notez que l’implémentation par défaut est conçue pour les cas où aucun VSPackage n’est enregistré et aucun projet n’est contrôlée. Un contrôle de code source correctement écrites VSPackage implémente les interfaces nécessaires, plutôt que de laisser à l’implémentation par défaut de ces interfaces.  
  
 Un contrôle de code source VSPackage doit implémenter un service privé qui encapsule tout ou partie des interfaces suivantes.  
  
 Les interfaces sont :  
  
-   Requis : L’entité appropriée (contrôle de code source VSPackage, Stub du contrôle de code Source, project) doit implémenter l’interface.  
  
-   Recommandé : L’entité doit implémenter cette interface. dans le cas contraire, les fonctionnalités de contrôle de code source peuvent être limitées.  
  
-   Facultatif : l’entité peut implémenter cette interface pour fournir un ensemble de fonctionnalités plus riche.  
  
|Interface|Objectif|Implémenté par|Mettre en œuvre ?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Éditeurs appellent cette interface avant de modifier ou de l’enregistrement d’un fichier. Le contrôle de code source VSPackage peut extraire le fichier ou refuser l’opération si l’extraction échoue.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Cette interface fournit des fonctionnalités de contrôle de source de base pour les projets, telles que l’inscription et annuler l’inscription des projets de contrôle de code source et prise en charge pour les glyphes de contrôle de source de base.|Contrôle de code source VSPackage|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Cette interface est obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>à l’aide de la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>(fonction), ou simplement effectuer un cast de l’objet implémentant `IVsHierarchy` à `IVsSccProject2`.</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Il est utilisé pour obtenir les fichiers sous contrôle de code source dans un projet ou pour informer le projet de l’état actuel du contrôle source ou l’emplacement.|Projet|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Le module d’intégration utilise cette interface pour définir le VSPackage actif actuels.|Contrôle de code source VSPackage|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Cette interface est basée sur un modèle d’abonnement. Un VSPackage peut signaler qu’il souhaite recevoir des événements de document et avisé par l’interpréteur de commandes sur les événements qui sont sur le point de se produire. Elle est implémentée et gérée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], qui à son tour transmet les événements implémentant le `IVsTrackProjectDocumentsEvents2` pour le VSPackage.|Stub de contrôle de code source|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Cette interface fournit le traitement par lots, les opérations en lecture/écriture synchronisé et avancée `OnQueryAddFiles` méthode.|Stub de contrôle de code source|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**L’Explorateur de solutions** et projets appellent cette interface lorsque de nouveaux fichiers sont ajoutés aux projets, ou lorsque les fichiers et dossiers sont renommés ou supprimés à partir de projets. Le contrôle de code source VSPackage peut extraire le fichier projet ou annuler l’opération.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**L’Explorateur de solutions** et projets appellent cette interface en réponse aux appels aux méthodes de l’interface IVstrackProjectDocuments3. Le contrôle de code source VSPackage peut effectuer le suivi des opérations par lot, synchronisées les opérations de lecture/écriture et manipuler plus avancées `OnQueryAddFiles` méthode.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Cette interface fournit la prise en charge de gestion de l’inscription pour les projets Web.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Cette interface est utilisée pour récupérer des info-bulles pour les fichiers de contrôle de code source dans les projets.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Cette interface fournit des extensions de prise en charge.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|Le VSPackage utilise cette interface pour intégrer une extension de l’espace de noms dans le **nouveau**, **Open**, ou **enregistrer** boîtes de dialogue. Par conséquent, les projets peuvent être automatiquement ajoutés au contrôle de code source lors de la création ou ajoutés au contrôle de code source lorsqu’une sauvegarde opération est en vigueur.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|Le VSPackage utilise cette interface pour définir les glyphes supplémentaires comme des glyphes de contrôle de source pour les nœuds de **l’Explorateur de solutions**.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Le **ajouter** boîte de dialogue pour les projets Web utilise cette interface. Il fournit des méthodes pour la navigation d’un emplacement de contrôle de code source et pour l’ouverture d’un projet Web précédemment ajouté dans le référentiel de contrôle de code source à cet emplacement.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Cette interface prend en charge le chargement asynchrone (en arrière-plan) des projets de contrôle de code source.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Cette interface permet aux projets de surveiller la progression du chargement asynchrone lancée par <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Projet|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Cette interface permet à l’IDE interroger le contrôle de code source actif VSPackage. L’IDE interroge la valeur des paramètres de contrôle de source qui ont une signification même lorsqu’il n’existe aucun contrôle source active que VSPackage inscrit. Cette interface est implémentée et gérée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub de contrôle de code source|Obligatoire|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Cette interface est utilisée dans l’enregistrement du contrôle de code source VSPackage.|Stub de contrôle de code source|Obligatoire|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|Cette interface est utilisée dans automation. Par conséquent, elle expose uniquement les fonctions pouvant être exécutées sans afficher d’interface utilisateur.|Contrôle de code source VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Cette interface est utilisée pour enregistrer des paramètres de contrôle de la source dans le fichier solution (.sln). Les paramètres incluent l’emplacement du contrôle de code source et les indicateurs d’état de contrôle de code source.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Cette interface est utilisée pour enregistrer les paramètres de contrôle de code source dans le fichier d’options (.suo) de solution. Cela peut inclure des paramètres de contrôle spécifiques à l’utilisateur source comme emplacement de l’inscription de l’utilisateur actuel.|Contrôle de code source VSPackage|Recommandé|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Cette interface est utilisée pour contrôler des événements afin d’effectuer des opérations telles que l’archivage des fichiers de projet avant la fermeture des solutions, ou pour obtenir de nouveaux fichiers à partir du contrôle de code source lors de l’ouverture d’un projet.|Contrôle de code source VSPackage|Recommandé|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)
