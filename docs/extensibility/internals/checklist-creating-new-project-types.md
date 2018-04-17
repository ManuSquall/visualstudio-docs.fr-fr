---
title: 'Liste de vérification : Créer de nouveaux Types de projet | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11707e62e99dd6a7920ad627d02e6e418c002e80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="checklist-creating-new-project-types"></a>Liste de vérification : Créer de nouveaux Types de projet
Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. La liste de vérification suivante fournit un guide sur ces tâches.  
  
1.  Concevoir les fonctionnalités pour votre nouveau type de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Déterminer les éditeurs sont utilisés pour le code et d’autres éléments de projet. Vous pouvez utiliser les éditeurs standards core, ou vous pouvez créer et utiliser les éditeurs de spécifique au projet. Pour plus d’informations, consultez [créer des éditeurs personnalisés et les concepteurs](../../extensibility/creating-custom-editors-and-designers.md) et [Comment : ouvrir les éditeurs spécifique au projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Déterminer le niveau de participation ont des éléments de votre projet dans le **affichage de classes** et **Explorateur d’objets**. Pour plus d’informations, consultez [outils de consultation du symbole de prise en charge](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Dériver de nouvelles classes basées sur des décisions de conception que vous avez apportées précédemment pour votre projet et les éléments de projet.  
  
5.  Écrivez le code pour les composants de type de projet suivants :  
  
    -   Fabrique de projet, pour gérer la création de projets et ouvrir des projets existants. Pour plus d’informations, consultez [création de projet d’Instances par à l’aide de projet fabriques](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hiérarchie de projet et la gestion des commandes. Pour plus d’informations, consultez [pas dans la Build : utilisation de Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [les éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md)et [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Gestion d’éléments de projet, y compris l’ajout de votre projet pour le **nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) et [enregistrement de modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistance de l’état du projet et des éléments individuels. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance des informations sur la solution, consultez [Solutions](../../extensibility/internals/solutions.md).  
  
    -   Propriétés indépendantes de la configuration à afficher dans la fenêtre Propriétés. Pour plus d’informations, consultez [étendre les propriétés](../../extensibility/internals/extending-properties.md).  
  
    -   Les propriétés de configuration de projet tel qu’implémenté dans les pages de propriétés pour afficher les propriétés dépendantes de la configuration. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Énumération des sorties pour le déploiement. Pour plus d’informations, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Services de démarrage du projet. Pour plus d’informations, consultez [les éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md) et [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objets ou classes dérivées de `IDispatch`, disponible pour l’automatisation.  
  
    -   Fichiers XML Command Table (.vsct). Pour plus d’informations, consultez [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Tester et déboguer votre type de projet de démarrage.  
  
7.  Afficher votre projet dans le **projet** onglet de la **ajouter une référence** boîte de dialogue en définissant `VARIANT_TRUE` comme valeur pour `VSHPROPID_ShowProjInSolutionPage`. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Créer le fichier Microsoft Installer (.msi) pour l’installation de vos VSPackages. Pour plus d’informations, consultez [l’installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [l’inscription d’un Type de projet](../../extensibility/internals/registering-a-project-type.md), et [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quand créer des Types de projets](../../extensibility/internals/when-to-create-project-types.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)