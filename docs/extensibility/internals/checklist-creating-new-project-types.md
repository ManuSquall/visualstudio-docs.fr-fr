---
title: 'Liste de vérification : Créer de nouveaux Types de projet | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: edd4c0a1bf4b6cbc76c2bc4bdbc597efd348799c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861583"
---
# <a name="checklist-create-new-project-types"></a>Liste de vérification : Créer des types de projet
Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. La liste de vérification suivante fournit un guide pour ces tâches :  
  
1.  Concevoir les fonctionnalités pour votre nouveau type de projet. Pour plus d’informations, consultez [décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Déterminer les éditeurs sont utilisés pour le code et d’autres éléments de projet. Vous pouvez utiliser le core ou des éditeurs standard, ou vous pouvez créer et utiliser des éditeurs spécifiques du projet. Pour plus d’informations, consultez [créer des concepteurs et éditeurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md) et [Comment : Ouvrir des éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Déterminer le niveau de participation de vos éléments de projet dans le **affichage de classes** et **Explorateur d’objets**. Pour plus d’informations, consultez [prennent en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Dériver les nouvelles classes selon les décisions de conception que vous avez effectuées précédemment pour votre projet et les éléments de projet.  
  
5.  Écrivez le code pour les composants de type de projet suivants :  
  
    -   Fabrique de projet, pour gérer la création de projets et ouvrir des projets existants. Pour plus d’informations, consultez [créer des instances de projet à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hiérarchie de projet et la gestion des commandes. Pour plus d’informations, consultez [HierUtil7 de l’utilisation des classes de projet pour implémenter un type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), [les composants de base de modèle de projet](../../extensibility/internals/project-model-core-components.md)et [ MenuCommands et OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Gestion d’éléments de projet, y compris l’ajout de votre projet pour le **nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [ajouter le projet et les modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) et [inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistance de l’état du projet et des éléments individuels. Pour plus d’informations, consultez [ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance des informations sur la solution, consultez [Solutions](../../extensibility/internals/solutions.md).  
  
    -   Propriétés indépendantes de la configuration à afficher dans la fenêtre Propriétés. Pour plus d’informations, consultez [étendre propriétés](../../extensibility/internals/extending-properties.md).  
  
    -   Propriétés de configuration de projet tel qu’implémenté dans les pages de propriétés pour afficher les propriétés dépendantes de la configuration. Pour plus d’informations, consultez [gérer les options de configuration](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Énumération des sorties pour le déploiement. Pour plus d’informations, consultez [configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Services de démarrage de projet. Pour plus d’informations, consultez [éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md) et [les composants de base de modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objets ou classes dérivées de `IDispatch`, disponible pour l’automatisation.  
  
    -   Table de commande XML (*.vsct*) les fichiers. Pour plus d’informations, consultez [fichiers Visual Studio command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Tester, déboguer et démarrer votre type de projet.  
  
7.  Afficher votre projet dans le **projet** onglet de la **ajouter une référence** boîte de dialogue en définissant `VARIANT_TRUE` comme valeur pour `VSHPROPID_ShowProjInSolutionPage`. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Créer Microsoft Installer (*.msi*) fichier d’installation de vos VSPackages. Pour plus d’informations, consultez [installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [inscrire un type de projet](../../extensibility/internals/registering-a-project-type.md), et [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quand créer des types de projets](../../extensibility/internals/when-to-create-project-types.md)   
 [Créer des types de projets](../../extensibility/internals/creating-project-types.md)