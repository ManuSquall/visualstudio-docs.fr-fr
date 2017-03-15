---
title: "Liste de v&#233;rification&#160;: Cr&#233;er de nouveaux Types de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "créer de nouveaux types de projets (Visual Studio SDK),"
  - "types de projets, liste de vérification pour la création"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Liste de v&#233;rification&#160;: Cr&#233;er de nouveaux Types de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. Liste de vérification suivante fournit un guide pour ces tâches.  
  
1.  La fonctionnalité pour votre nouveau type de projet de conception. Pour plus d'informations, consultez [Décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Déterminer les éditeurs sont utilisés pour le code et autres éléments de projet. Vous pouvez utiliser les éditeurs standards core, ou vous pouvez créer et utiliser les éditeurs spécifiques au projet. Pour plus d’informations, consultez [Création de concepteurs et éditeurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md) et [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Déterminer le niveau de participation de vos éléments de projet dans le **affichage de classes** et **Explorateur d’objets**. Pour plus d'informations, consultez [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Dériver de nouvelles classes basées sur les décisions de conception que vous avez effectuées précédemment pour votre projet et les éléments de projet.  
  
5.  Écrivez le code pour les composants de type de projet suivants :  
  
    -   Factory de projet, pour gérer la création de projets et l’ouverture de projets existants. Pour plus d'informations, consultez [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Hiérarchie de projet et la gestion des commandes. Pour plus d’informations, consultez [pas dans la génération : utilisation de Classes de projet HierUtil7 pour implémenter un Type de projet \(C\+\+\)](http://msdn.microsoft.com/fr-fr/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Éléments d'un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md) et [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Gestion d’éléments de projet, notamment l’ajout de votre projet pour le **Nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) et [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistance de l’état du projet et des éléments individuels. Pour plus d'informations, consultez [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance des informations sur la solution, consultez [Solutions](../../extensibility/internals/solutions.md).  
  
    -   Propriétés indépendantes de la configuration à afficher dans la fenêtre Propriétés. Pour plus d'informations, consultez [Étendre les propriétés](../../extensibility/internals/extending-properties.md).  
  
    -   Propriétés de configuration de projet tel qu’implémenté dans les pages de propriétés pour afficher les propriétés dépendantes de la configuration. Pour plus d'informations, consultez [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Énumération des sorties pour le déploiement. Pour plus d'informations, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Services de démarrage du projet. Pour plus d’informations, consultez [Éléments d'un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md) et [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
    -   Les objets ou les classes dérivées de `IDispatch`, disponible pour l’automatisation.  
  
    -   Fichiers de la Table de commande XML \(.vsct\). Pour plus d'informations, consultez [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Tester, déboguer et démarrer votre type de projet.  
  
7.  Afficher votre projet dans le **projet** onglet de la **Ajouter une référence** boîte de dialogue en définissant `VARIANT_TRUE` comme valeur pour `VSHPROPID_ShowProjInSolutionPage`. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Créer le fichier Microsoft Installer \(.msi\) pour installer vos packages VS. Pour plus d'informations, consultez [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [L'inscription d'un Type de projet](../../extensibility/internals/registering-a-project-type.md) et [Packages VS](../../extensibility/internals/vspackages.md).  
  
## Voir aussi  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Quand créer des Types de projets](../../extensibility/internals/when-to-create-project-types.md)   
 [Création de Types de projets](../../extensibility/internals/creating-project-types.md)