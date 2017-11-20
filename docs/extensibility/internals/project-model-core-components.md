---
title: "Composants de modèle de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7759a2394f2cda19f875a85a22c4a674fee8964
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="project-model-core-components"></a>Composants de modèle de projet
Les tableaux suivants décrivent le modèle de projet. Les tables présentent des brèves descriptions des interfaces et des services identifiés dans le modèle et les interfaces et les services associés à des objets spécifiques. En outre, les tables de détaillent des autres interfaces qui sont facultatifs dans la création du projet et de maintenance selon les besoins de votre type de projet spécifique.  
  
 Pour plus d’informations, consultez [outils de consultation du symbole de prise en charge](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objet de package  
  
|Interface|Commentaires|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialise un VSPackage dans l’IDE et met à disposition ses services à l’IDE.|  
  
### <a name="project-factory-object"></a>Objet de fabrique de projet  
  
|Interface|Commentaires|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gère la création de projets et ouvrir des projets existants.|  
  
### <a name="project-objects"></a>Objets du projet  
  
|Interfaces|Commentaires|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gère l’ajout et la suppression d’éléments de projet, ouvre les éditeurs et maintient le mappage entre le moniker de chaque document et `VSITEMID`. Hérite de `IVsProject` et `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gère les propriétés de navigation et l’affichage et fournit des événements.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Permet de commande d’exécution similaire à celle de `IOleCommandTarget` pour les commandes telles que couper et changement de nom qui s’appliquent uniquement lorsque le focus est dans l’Explorateur de solutions.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sert d’interface de cible de commande principal pour une hiérarchie de projet. Il est l’interface standard pour interroger des objets pour leurs commandes d’état ou état et en cours d’exécution de commande. Disponible lorsque vous vous intéressez pas dans la fenêtre du projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordonnées de la persistance de l’état du projet. En règle générale, l’état du projet est stocké sous forme de fichier projet, mais peut être adaptée à des systèmes de stockage qui ne sont pas basées sur le fichier.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permet au projet gérer tous les aspects de la persistance pour ses éléments de projet en tant que fichiers sur disque ou des objets dans d’autres systèmes de stockage. Le `IVsPeristHierarchyItem2` interface est utilisée pour les éléments qui n’implémentent pas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordonne les interactions avec le contrôle de code source.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permet aux projets gérer les informations de configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gère les objets de configuration de projet, telles que les configurations Debug/Release. Générer, déployer et déboguer les opérations sont coordonnées par le biais des objets de configuration de projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implémenté par les hiérarchies pour contrôler la suppression (destructeur) ou de supprimer des options (non destructrice) pour les éléments de la hiérarchie. Appeler l’Interface de requête sur le `IVsHierarchyDeleteHandler` de l’interface à partir de la `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fournit la possibilité de mise en œuvre de l’objet qui prend en charge la `IVsCfgProvider2` interface sur une autre identité COM à l’objet de projet qui implémente le `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface facultative mise en œuvre pour que votre projet extensible par d’autres développeurs. Le `IVsProjectStartupServices` interface permet à un VSPackage tiers inscrire un GUID qui demeurent dans votre fichier projet afin que chaque fois que votre projet se charge, vous chargez le GUID de service tiers dans votre fichier projet et l’appel `QueryService` pour ce GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implémenté par les hiérarchies source dans un `UIHierarchy` fenêtre pour coordonner les opérations du Presse-papiers telles que couper, copier et coller. Utilisez le `AdviseClipboardHelperEvents` interface pour enregistrer les événements du Presse-papiers.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fournit des informations sur un élément glissé par rapport à sa source de données pendant une opération de glisser-déposer dans une fenêtre de hiérarchie de l’interface utilisateur. Appelée à partir de la `IVsHierarchy` interface.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fournit des informations sur un élément glissé par rapport à sa cible pendant une opération de glisser-déposer dans une fenêtre de hiérarchie de l’interface utilisateur. Appelée à partir de la `IVsHierarchy` interface.|  
  
### <a name="configuration-object"></a>Objet de configuration  
  
|Interfaces|Commentaires|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fournit des informations sur une configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permet aux projets gérer les informations de configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permet à un projet à exécuter sous le contrôle du débogueur.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implémenté par les projets de déploiement qui effectuent des opérations de déploiement pour les autres projets.|  
  
### <a name="configuration-builder-object"></a>Objet de configuration de générateur  
  
|Interfaces|Commentaires|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gère l’opération de création d’une configuration de projet.|  
  
### <a name="additional-project-objects"></a>Objets de projet supplémentaires  
  
|Interfaces|Commentaires|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Affiche d’élément de propriétés dans le **propriétés** fenêtre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Affiche des sorties pour le déploiement.|  
  
 Le tableau suivant présente des brèves descriptions de services identifiés dans le modèle de projet.  
  
### <a name="services"></a>Services  
  
|Service|Commentaires|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilisé par les VSPackages qui implémentent les types de projets pour inscrire que la fabrique de projet existe à l’IDE. Votre VSPackage doit appeler `QueryService` pour ce service et inscrire la fabrique de projet lorsque `IVsPackage::SetSite` méthode est appelée. Si le `SetSite` méthode n’est pas appelée, votre projet n’est pas instancié.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit l’accès à la notion de l’IDE interne et intégrée de la solution actuelle, notamment la possibilité d’énumérer les projets, créer des projets, prendre en compte les modifications de projet et ainsi de suite.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Appelée par les projets que vous souhaitent participer au contrôle de code source.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gère une table de documents ouverts pour déterminer si un ou plusieurs de vos éléments de projet sont déjà ouverts.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contient les interfaces et les méthodes appelées pour ouvrir un élément de projet à l’aide de l’éditeur standard ou un éditeur spécifique.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Doit être appelée par tous les projets lors de leur ajouter, supprimer ou renommer les éléments.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gère les modifications apportées à un fichier ou un répertoire et notifie les clients lorsque les fichiers sélectionnés ont été modifiés sur le disque.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Doit être appelé par tous les projets et les éditeurs avant leur incorrectes d’éléments ou les enregistrent.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gère l’ordre des opérations de génération et de déploiement pour les configurations de projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fournit l’accès aux services de débogueur de bas niveau utilisés pour la plupart des contrôles de débogage.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Permet l’accès de VSPackages à plus d’informations sur les sélections en cours et Active la communication avec le **propriétés** fenêtre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit les fonctionnalités IDE de dépendant de l’interface utilisateur de base, telles que la capacité de créer et d’énumérer les fenêtres de document ou les fenêtres Outil ou pour signaler une erreur à l’utilisateur.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fournit l’accès à la barre d’état de l’IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilisé pour implémenter le modèle automation. Dans votre modèle de projet, vous retourne un objet de propriétés qui vous permet de crée une instance de cet objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilisé pour implémenter des événements de Presse-papiers de l’objet de projet dans la hiérarchie. `SVsUIHierWinClipboardHelper`vous permet de correctement handle couper, copier et coller.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Pas dans la génération : à l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Prise en charge des outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)