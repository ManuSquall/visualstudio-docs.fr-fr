---
title: Composants de base du modèle de projet Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706536"
---
# <a name="project-model-core-components"></a>Principaux composants d’un modèle de projet
Les tableaux suivants s’étendent sur le modèle de projet. Les tableaux présentent de brèves descriptions des interfaces et des services identifiés dans le modèle, ainsi que des interfaces et des services associés à des objets spécifiques. En outre, les tables détaillent d’autres interfaces facultatives dans la création et la maintenance du projet en fonction des exigences de votre type de projet spécifique.

 Pour plus d’informations, voir [Outils de navigation de symbole de soutien](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objet de paquet

|Interface|Commentaires|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialise un VSPackage dans l’IDE et met ses services à la disposition de l’IDE.|

### <a name="project-factory-object"></a>Objet d’usine de projet

|Interface|Commentaires|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gère la création de nouveaux projets et l’ouverture de projets existants.|

### <a name="project-objects"></a>Objets de projet

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gère l’ajout et la suppression des éléments de projet, ouvre des `VSITEMID`éditeurs, et maintient la cartographie entre chaque surnom de document et le . Hérite `IVsProject` de `IVsProject2`et .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gère les propriétés de navigation et d’affichage et fournit des événements.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Permet l’exécution de `IOleCommandTarget` commande similaire à celle des commandes telles que Cut et Rename qui ne s’appliquent que lorsque l’accent est mis sur Solution Explorer.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sert d’interface cible de commande principale pour une hiérarchie de projet. C’est l’interface standard pour interroger les objets pour leur statut de commande ou de l’état et les commandes en cours d’exécution. Disponible lorsque vous n’êtes pas concentré dans la fenêtre du projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordonne la persistance de l’état du projet. En règle générale, l’état du projet est stocké comme un fichier de projet, mais peut être adapté à des systèmes de stockage qui ne sont pas basés sur des fichiers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permet au projet de gérer tous les aspects de la persistance de ses éléments de projet, que ce soit sous forme de fichiers sur disque ou d’objets dans d’autres systèmes de stockage. L’interface `IVsPersistHierarchyItem2` est utilisée pour les <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> éléments qui ne mettent pas en œuvre l’interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordonne les interactions avec le contrôle du code source.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permet aux projets de gérer les informations de configuration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gère les objets de configuration du projet, tels que les configurations Debug/Release. Les opérations de construction, de déploiement et de débagé sont coordonnées par des objets de configuration de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implémenté par les hiérarchies pour contrôler les options de suppression (destructrices) ou supprimer (non destructives) pour les éléments de hiérarchie. Appelez l’interface `IVsHierarchyDeleteHandler` requête sur `IVsHierarchy` l’interface à partir de l’interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fournit la possibilité de mise en `IVsCfgProvider2` œuvre d’avoir l’objet qui `IVsHierarchy` prend en charge l’interface sur une identité COM différente de l’objet du projet qui implémente l’interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface facultative mise en œuvre pour rendre votre projet extensible par d’autres développeurs. L’interface `IVsProjectStartupServices` permet à un TIERS VSPackage d’enregistrer un GUID que vous persistez dans votre fichier de projet de sorte `QueryService` que chaque fois que votre projet se charge, vous chargez le service tiers GUID dans votre fichier de projet et appelez pour ce GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Mise en œuvre `UIHierarchy` par des hiérarchies de source dans une fenêtre pour coordonner les opérations de presse-papiers telles que la coupe, la copie et la pâte. Utilisez `AdviseClipboardHelperEvents` l’interface pour enregistrer les événements du presse-papiers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fournit des informations sur un élément traîné par rapport à sa source de données lors d’une opération de drag-and-drop dans une fenêtre de hiérarchie d’interface utilisateur. Appelé à `IVsHierarchy` partir de l’interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fournit des informations sur un élément traîné par rapport à sa cible de chute lors d’une opération de drag-and-drop dans une fenêtre de hiérarchie d’interface utilisateur. Appelé à `IVsHierarchy` partir de l’interface.|

### <a name="configuration-object"></a>Objet de configuration

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fournit des informations sur une configuration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permet aux projets de gérer les informations de configuration.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permet de mener un projet sous le contrôle du débbuggeur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Mise en œuvre par des projets de déploiement qui effectuent des opérations de déploiement pour d’autres projets.|

### <a name="configuration-builder-object"></a>Objet De constructeur de configuration

|Interfaces|Commentaires|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gère l'opération de génération d'une configuration de projet.|

### <a name="additional-project-objects"></a>Objets de projet supplémentaires

|Interfaces|Commentaires|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Affiche les propriétés de l’élément dans la fenêtre **Propriétés.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Affiche les sorties pour le déploiement.|

 Le tableau suivant présente de brèves descriptions des services identifiés dans le modèle de projet.

### <a name="services"></a>Services

|Service|Commentaires|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilisé par VSPackages qui implémentent les types de projets pour enregistrer que leur usine de projet existe avec l’IDE. Votre VSPackage `QueryService` doit appeler pour ce service `IVsPackage::SetSite` et enregistrer son usine de projet lorsque la méthode est appelée. Si `SetSite` la méthode n’est pas appelée, votre projet n’est pas instantané.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Donne accès à la notion interne et intégrée de l’IDE de la solution actuelle, comme la capacité d’énumérer des projets, de créer de nouveaux projets, de prendre connaissance des changements de projets, et ainsi de suite.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Appelé par des projets qui souhaitent participer au contrôle des sources.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Maintient un tableau de documents ouverts pour déterminer si un ou plusieurs de vos éléments de projet sont déjà ouverts.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contient les interfaces et les méthodes appelées à ouvrir réellement un élément de projet à l’aide de l’éditeur standard ou d’un éditeur spécifique.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Nécessité d’être appelé par tous les projets lorsqu’ils ajoutent, suppriment ou renomment leurs articles.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gère les modifications apportées à un fichier ou à un répertoire et avise les clients lorsque certains fichiers ont été modifiés sur disque.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Nécessité d’être appelé par tous les projets et les éditeurs avant qu’ils sales articles ou les enregistrer.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gère l’ordre des opérations de construction et de déploiement pour les configurations de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Donne accès à des services de débogage de faible niveau utilisés pour la plupart des contrôles de débogage.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Permet AUXPackages d’accéder à des informations sur les sélections actuelles et permet la communication avec la fenêtre **Propriétés.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit des fonctionnalités IDE de base liées à l’interface utilisateur, telles que la possibilité de créer et d’énumérer des fenêtres d’outils ou de documenter des fenêtres ou de signaler une erreur à l’utilisateur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Donne accès à la barre d’état de l’IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilisé pour implémenter le modèle d’automatisation. Dans votre modèle de projet, vous retournerez un objet propriété qui vous permet de créer une instance de cet objet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilisé pour implémenter des événements de presse-papiers sur l’objet du projet dans la hiérarchie. `SVsUIHierWinClipboardHelper`vous permet de gérer correctement les opérations de coupe, de copie et de pâte.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Pas dans la construction : Utilisation des classes de projet HierUtil7 pour mettre en œuvre un type de projet (CMD)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Prise en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
