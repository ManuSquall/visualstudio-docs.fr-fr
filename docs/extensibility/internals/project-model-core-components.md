---
title: Composants de base du modèle de projet | Microsoft Docs
description: Cet article contient des descriptions des interfaces et des services identifiés dans le modèle de projet Core, ainsi que des interfaces et des services associés aux objets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dc53378e7e06d0a7d4ad362f7bb3876e186c80
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899704"
---
# <a name="project-model-core-components"></a>Principaux composants d’un modèle de projet
Les tableaux suivants s’étendent sur le modèle de projet. Les tableaux présentent de brèves descriptions des interfaces et des services identifiés dans le modèle, ainsi que les interfaces et les services associés à des objets spécifiques. En outre, les tables détaillent les autres interfaces facultatives lors de la création et de la maintenance du projet en fonction des exigences de votre type de projet spécifique.

 Pour plus d’informations, consultez [prise en charge des outils de Symbol-Browsing](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objet de package

|Interface|Commentaires|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialise un VSPackage dans l’IDE et met ses services à la disposition de l’IDE.|

### <a name="project-factory-object"></a>Objet de fabrique de projets

|Interface|Commentaires|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gère la création de projets et l’ouverture de projets existants.|

### <a name="project-objects"></a>Objets de projet

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gère l’ajout et la suppression d’éléments de projet, ouvre les éditeurs et conserve le mappage entre chaque moniker de document et le `VSITEMID` . Hérite de `IVsProject` et `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gère les propriétés de navigation et d’affichage et fournit des événements.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Active l’exécution d’une commande similaire à celle de `IOleCommandTarget` pour les commandes telles que couper et renommer qui s’appliquent uniquement lorsque le focus se trouve dans Explorateur de solutions.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sert d’interface cible de la commande principale pour une hiérarchie de projet. Il s’agit de l’interface standard pour interroger des objets en fonction de leur état de commande ou de leurs commandes d’exécution. Disponible lorsque vous n’êtes pas concentré dans la fenêtre du projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordonne la persistance de l’état du projet. En règle générale, l’état du projet est stocké sous la forme d’un fichier projet, mais il peut être adapté à des systèmes de stockage qui ne sont pas basés sur des fichiers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permet au projet de gérer tous les aspects de la persistance pour ses éléments de projet, soit en tant que fichiers sur le disque, soit en tant qu’objets dans d’autres systèmes de stockage. L' `IVsPersistHierarchyItem2` interface est utilisée pour les éléments qui n’implémentent pas l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordonne les interactions avec le contrôle de code source.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permet aux projets de gérer les informations de configuration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gère les objets de configuration de projet, tels que les configurations Debug/Release. Les opérations de génération, de déploiement et de débogage sont coordonnées par le biais d’objets de configuration de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implémenté par les hiérarchies pour contrôler les options de suppression (destructrice) ou de suppression (non destructrice) des éléments de la hiérarchie. Appeler l’interface de requête sur l' `IVsHierarchyDeleteHandler` interface à partir de l' `IVsHierarchy` interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fournit l’option d’implémentation de l’objet qui prend en charge l' `IVsCfgProvider2` interface sur une identité com différente de celle de l’objet de projet qui implémente l' `IVsHierarchy` interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface facultative implémentée pour que votre projet soit extensible par d’autres développeurs. L' `IVsProjectStartupServices` interface permet à un VSPackage tiers d’enregistrer un GUID que vous conservez dans votre fichier projet. ainsi, chaque fois que votre projet se charge, vous chargez le GUID de service tiers dans votre fichier projet et appelez `QueryService` pour ce GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implémenté par les hiérarchies sources dans une `UIHierarchy` fenêtre pour coordonner les opérations du presse-papiers, telles que couper, copier et coller. Utilisez l' `AdviseClipboardHelperEvents` interface pour enregistrer les événements du presse-papiers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fournit des informations sur un élément déplacé par rapport à sa source de données pendant une opération de glisser-déplacer dans une fenêtre de hiérarchie d’interface utilisateur. Appelé à partir de l' `IVsHierarchy` interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fournit des informations sur un élément déplacé par rapport à sa cible de déplacement pendant une opération de glisser-déplacer dans une fenêtre de hiérarchie d’interface utilisateur. Appelé à partir de l' `IVsHierarchy` interface.|

### <a name="configuration-object"></a>Objet de configuration

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fournit des informations sur une configuration de.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permet aux projets de gérer les informations de configuration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permet à un projet d’être exécuté sous le contrôle du débogueur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implémenté par des projets de déploiement qui effectuent des opérations de déploiement pour d’autres projets.|

### <a name="configuration-builder-object"></a>Objet configuration Builder

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gère l'opération de génération d'une configuration de projet.|

### <a name="additional-project-objects"></a>Objets de projet supplémentaires

|Interfaces|Commentaires|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Affiche les propriétés de l’élément dans la fenêtre **Propriétés** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Affiche les sorties pour le déploiement.|

 Le tableau suivant présente une brève description des services identifiés dans le modèle de projet.

### <a name="services"></a>Services

|Service|Commentaires|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilisé par les VSPackages qui implémentent des types de projet pour s’inscrire que leur fabrique de projet existe avec l’IDE. Votre VSPackage doit appeler `QueryService` pour ce service et inscrire sa fabrique de projet lorsque la `IVsPackage::SetSite` méthode est appelée. Si la `SetSite` méthode n’est pas appelée, votre projet n’est pas instancié.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Donne accès à la notion interne intégrée de l’IDE de la solution actuelle, telle que la possibilité d’énumérer des projets, de créer de nouveaux projets, d’observer des modifications de projet, etc.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Appelée par les projets qui souhaitent participer au contrôle de code source.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gère une table de documents ouverts pour déterminer si un ou plusieurs de vos éléments de projet sont déjà ouverts.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contient les interfaces et les méthodes appelées pour ouvrir un élément de projet à l’aide de l’éditeur standard ou d’un éditeur spécifique.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Doit être appelé par tous les projets lorsqu’ils ajoutent, suppriment ou renomment leurs éléments.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gère les modifications apportées à un fichier ou à un répertoire et avertit les clients lorsque des fichiers sélectionnés ont été modifiés sur le disque.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Doit être appelé par tous les projets et éditeurs avant qu’ils n’aient modifié les éléments ou ne les enregistre pas.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gère l’ordre des opérations de génération et de déploiement pour les configurations de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fournit l’accès aux services de débogueur de bas niveau utilisés pour la plupart des contrôles de débogage.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Permet aux VSPackages d’accéder aux informations sur les sélections actuelles et permet la communication avec la fenêtre **Propriétés** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit les fonctionnalités IDE de base de l’interface utilisateur, telles que la possibilité de créer et d’énumérer des fenêtres outil ou des fenêtres de document ou de signaler une erreur à l’utilisateur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fournit l’accès à la barre d’état de l’IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilisé pour implémenter le modèle Automation. Dans votre modèle de projet, vous allez retourner un objet de propriétés qui vous permet de créer une instance de cet objet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilisé pour implémenter les événements du presse-papiers sur l’objet de projet dans la hiérarchie. `SVsUIHierWinClipboardHelper` vous permet de gérer correctement les opérations couper, copier et coller.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Not in Build : utilisation des classes de projet HierUtil7 pour implémenter un type de projet (C++)](/previous-versions/bb166212(v=vs.100))
- [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)