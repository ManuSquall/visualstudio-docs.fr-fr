---
title: 'Liste de vérification : Créer de nouveaux Types de projet | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737355"
---
# <a name="checklist-creating-new-project-types"></a>Liste de vérification : création de nouveaux types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. La liste de vérification suivante fournit un guide pour ces tâches.  
  
1.  Concevoir les fonctionnalités pour votre nouveau type de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Déterminer les éditeurs sont utilisés pour le code et d’autres éléments de projet. Vous pouvez utiliser le core ou des éditeurs standard, ou vous pouvez créer et utiliser des éditeurs spécifiques du projet. Pour plus d’informations, consultez [création des éditeurs personnalisés et les concepteurs](../../extensibility/creating-custom-editors-and-designers.md) et [Comment : ouvrir éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Déterminer le niveau de participation de vos éléments de projet dans le **affichage de classes** et **Explorateur d’objets**. Pour plus d’informations, consultez [outils de consultation du symbole de prise en charge](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Dériver les nouvelles classes selon les décisions de conception que vous avez effectuées précédemment pour votre projet et les éléments de projet.  
  
5.  Écrivez le code pour les composants de type de projet suivants :  
  
    -   Fabrique de projet, pour gérer la création de projets et ouvrir des projets existants. Pour plus d’informations, consultez [création projet Instances par à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hiérarchie de projet et la gestion des commandes. Pour plus d’informations, consultez [pas dans la génération : à l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md)et [MenuCommands et. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Gestion d’éléments de projet, y compris l’ajout de votre projet pour le **nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [Ajout d’un projet et des modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) et [l’inscription de Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistance de l’état du projet et des éléments individuels. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance des informations sur la solution, consultez [Solutions](../../extensibility/internals/solutions.md).  
  
    -   Propriétés indépendantes de configuration à afficher dans la fenêtre Propriétés. Pour plus d’informations, consultez [étendre les propriétés](../../extensibility/internals/extending-properties.md).  
  
    -   Propriétés de configuration de projet tel qu’implémenté dans les pages de propriétés pour afficher les propriétés dépendantes de la configuration. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Énumération des sorties pour le déploiement. Pour plus d’informations, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Services de démarrage de projet. Pour plus d’informations, consultez [éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md) et [composants principaux du modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objets ou classes dérivées de `IDispatch`, disponible pour l’automatisation.  
  
    -   Fichiers XML Command Table (.vsct). Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Tester, déboguer et démarrer votre type de projet.  
  
7.  Afficher votre projet dans le **projet** onglet de la **ajouter une référence** boîte de dialogue en définissant `VARIANT_TRUE` comme valeur pour `VSHPROPID_ShowProjInSolutionPage`. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Créez le fichier Microsoft Installer (.msi) pour l’installation de vos VSPackages. Pour plus d’informations, consultez [installation les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [l’inscription d’un Type de projet](../../extensibility/internals/registering-a-project-type.md), et [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quand créer des Types de projets](../../extensibility/internals/when-to-create-project-types.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)

