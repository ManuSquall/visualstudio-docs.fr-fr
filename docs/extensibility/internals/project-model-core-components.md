---
title: "Composants de mod&#232;le de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces, les objets et les modèles de projet"
  - "modèles de projet, services"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Composants de mod&#232;le de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les tableaux suivants présentent le modèle de projet.  Les descriptions brèves actuelles de tables les interfaces et les services identifiés dans le modèle, et les interfaces et les services associés à des objets spécifiques.  En outre, les tableaux détaillent les autres interfaces qui sont facultatives dans la création et la maintenance de projet en fonction de les spécifications de votre type de projet spécifique.  
  
 Pour plus d'informations, consultez [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### objet de package  
  
|Interface|Commentaires|  
|---------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialise un VSPackage dans l'IDE et rend ses services disponibles dans l'IDE de.|  
  
### objet de fabrique de projet  
  
|Interface|Commentaires|  
|---------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gère créer des projets et ouvrir des projets existants.|  
  
### objets Project  
  
|Interfaces|Commentaires|  
|----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gère l'ajout et la suppression des éléments de projet, ouvre des éditeurs, et gère le mappage entre chaque moniker du document et `VSITEMID`.  hérite d' `IVsProject` et d' `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|gère la navigation et les propriétés d'affichage et fournit des événements.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Autorise l'exécution de la commande similaire à celle d' `IOleCommandTarget` pour les commandes telles que couper et la renomme qui s'appliquent uniquement lorsque le focus est dans l'explorateur de solutions.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sert d'interface de cible de commande primaire à une hiérarchie de projet.  Il s'agit de l'interface standard pour interroger des objets pour leur état de la commande ou état et commandes en cours de exécution.  Disponible lorsque vous n'êtes pas centré dans la fenêtre de projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|coordonne la persistance de l'état de projet.  En général, l'état du projet est enregistré en tant que fichier projet mais peut être adapté aux systèmes de stockage qui ne sont pas basés sur des fichiers.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Active le projet de gérer tous les aspects de la persistance pour ses éléments de projet, en tant que fichiers sur le disque ou les objets dans d'autres systèmes de stockage.  l'interface d' `IVsPeristHierarchyItem2` est utilisée pour les éléments qui n'implémentent pas l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|interactions de coordonnées avec le contrôle de code source.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permet aux projets pour gérer les données de configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gère les objets de configuration de projet, tels que le débogage\/configuration Release.  La génération, déployer, et les opérations de débogage sont coordonnées via des objets de configuration de projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implémentée par les hiérarchies de contrôler la suppression \(destructive\) ou pour supprimer des options \(non destructrices\) pour les éléments de la hiérarchie.  interface de requête d'appel sur l'interface d' `IVsHierarchyDeleteHandler` de l'interface d' `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fournit la possibilité d'implémentation d'avoir l'objet qui prend en charge l'interface d' `IVsCfgProvider2` sur une identité différente COM que l'objet de projet qui implémente l'interface d' `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|interface facultative implémentée pour rendre votre projet extensible par d'autres développeurs.  L'interface d' `IVsProjectStartupServices` permet à un tiers VSPackage pour stocker GUID que vous rendez persistantes dans votre fichier projet afin que chaque fois votre projet charge, vous devez charger le service tiers GUID dans votre fichier projet et appelez `QueryService` pour ce GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implémentée par les hiérarchies de source dans une fenêtre d' `UIHierarchy` pour coordonner les opérations du presse\-papiers telles que couper, copier, puis collez.  Utilisez l'interface d' `AdviseClipboardHelperEvents` pour enregistrer les événements du presse\-papiers.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fournit des informations sur un élément déplacé par rapport à sa source de données pendant une opération de glisser\-déplacer dans une fenêtre hiérarchie d'interface utilisateur.  Appelé à partir de l'interface d' `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fournit des informations sur un élément déplacé par rapport à sa cible de déplacement pendant une opération de glisser\-déplacer dans une fenêtre hiérarchie d'interface utilisateur.  Appelé à partir de l'interface d' `IVsHierarchy` .|  
  
### Objet de configuration  
  
|Interfaces|Commentaires|  
|----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fournit des informations sur une configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permet aux projets pour gérer les données de configuration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permet à un projet d'être exécuté sous le contrôle du débogueur.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implémentée par les projets de déploiement qui exécutent des opérations de déploiement pour d'autres projets.|  
  
### Objet de configuration  
  
|Interfaces|Commentaires|  
|----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|gère l'opération de la génération d'une configuration de projet.|  
  
### objets Project supplémentaires  
  
|Interfaces|Commentaires|  
|----------------|------------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Affiche les propriétés de l'élément dans la fenêtre de **Propriétés** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Sorties d'affiche pour le déploiement.|  
  
 Le tableau suivant répertorie des descriptions brèves des services identifiés dans le modèle de projet.  
  
### Services  
  
|Service|Commentaires|  
|-------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilisé par les VSPackages qui implémentent des types de projet pour mémoriser que leur fabrique de projet existe avec l'IDE.  Votre VSPackage doit appeler `QueryService` pour ce service et stocker ses fabriques de projet lorsque la méthode d' `IVsPackage::SetSite` est appelée.  si la méthode d' `SetSite` n'est pas appelée, votre projet n'est pas instancié.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Permet d'accéder à l'IDE interne, notion intégrée de la solution actuelle, telle que la possibilité d'énumérer les projets, crée des projets, noter de prise des modifications de projet, et ainsi de suite.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|appelé par les projets qui souhaitent participer au contrôle de code source.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Contient un tableau des documents ouverts pour déterminer si un ou plusieurs de vos éléments de projet sont déjà ouverts.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contient les interfaces et les méthodes appelées pour ouvrir en fait un élément de projet à l'aide de l'éditeur standard ou un éditeur spécifique.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Qui doivent être appelé par tous les projets lorsqu'ils ajouter, supprimer ou renommer leurs éléments.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gère les modifications apportées à un fichier ou répertoire et notifie les clients lorsque les fichiers sélectionnés ont été modifiés sur le disque.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Qui doivent être appelé par tous les projets et les éditeurs avant de les éléments modifiés ou les enregistrer.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gère l'ordre des opérations de génération et de déploiement pour les configurations de projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Permet d'accéder aux services de bas niveau du débogueur utilisés pour la plupart des contrôles de débogage.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Active l'accès aux données de VSPackages sur les sélections actuelles et permet la communication avec la fenêtre de **Propriétés** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit la fonctionnalité Interface utilisateur\-mise en relation de base de l'IDE, telle que la possibilité de créer et énumérer des fenêtres Outil ou fenêtres de document ou d'enregistrer une erreur à l'utilisateur.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Permet d'accéder à la barre d'état de l'IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|utilisé pour implémenter le modèle Automation.  Dans votre modèle de projet, vous retournerez un objet de propriétés qui vous permet de créer une instance de cet objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilisé pour implémenter des événements du presse\-papiers dans l'objet de projet dans la hiérarchie.  `SVsUIHierWinClipboardHelper` vous permet d'exécuter correctement couper, copier, et les opérations de copier\-coller.|  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/fr-fr/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Éléments d'un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)