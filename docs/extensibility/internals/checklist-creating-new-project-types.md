---
title: 'Liste de contrôle : Création de nouveaux types de projets (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709749"
---
# <a name="checklist-create-new-project-types"></a>Liste de contrôle : Créer de nouveaux types de projets
Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. La liste de contrôle suivante fournit un guide pour ces tâches :

1. Concevez la fonctionnalité de votre nouveau type de projet. Pour plus d’informations, voir [décisions de conception de type projet](../../extensibility/internals/project-type-design-decisions.md).

2. Déterminez quels éditeurs sont utilisés pour le code et d’autres éléments de projet. Vous pouvez utiliser les éditeurs de base ou standard, ou vous pouvez créer et utiliser des éditeurs spécifiques au projet. Pour plus d’informations, voir [Créer des éditeurs et des designers personnalisés](../../extensibility/creating-custom-editors-and-designers.md) et [comment : Ouvrir des éditeurs spécifiques au projet.](../../extensibility/how-to-open-project-specific-editors.md)

3. Déterminez le niveau de participation que vos éléments de projet auront dans la **vue de classe** et le navigateur **d’objets**. Pour plus d’informations, voir [outils de navigation des symboles support](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Dérivez de nouvelles classes basées sur les décisions de conception que vous avez prises précédemment pour vos éléments de projet et de projet.

5. Rédigez le code pour les composants suivants du type de projet :

    - Usine de projet, pour gérer la création de nouveaux projets et l’ouverture de projets existants. Pour plus d’informations, voir [Les instances du projet Créer en utilisant des usines de projet.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

    - Hiérarchie du projet et maniabilité des commandes. Pour plus d’informations, voir [Utilisez les classes de projet HierUtil7 pour mettre en œuvre un type](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)de projet , éléments [d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), composants de base du modèle de [projet,](../../extensibility/internals/project-model-core-components.md)et [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Gestion des éléments de projet, y compris l’ajout de votre projet à la boîte de dialogue **du nouveau projet.** Pour plus d’informations, consultez [les modèles d’éléments de projet et de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) Add et [inscrivez-vous et enregistrez les modèles de projets et d’éléments](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistance de l’état du projet et des éléments individuels. Pour plus d’informations, voir [Ouvrez et enregistrez les éléments du projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance de l’information de solution, voir [Solutions](../../extensibility/internals/solutions-overview.md).

    - Propriétés indépendantes de configuration à afficher dans la fenêtre Propriétés. Pour plus d’informations, voir [Propriétés Extend](../../extensibility/internals/extending-properties.md).

    - Propriétés de configuration de projet telles qu’implémentées dans les pages de propriété pour afficher les propriétés dépendantes de la configuration. Pour plus d’informations, voir [Options de configuration Gérer](../../extensibility/internals/managing-configuration-options.md).

    - Énumérer les extrants pour le déploiement. Pour plus d’informations, voir [configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

    - Services de démarrage de projet. Pour plus d’informations, voir [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md) et des composants de base du modèle de [projet.](../../extensibility/internals/project-model-core-components.md)

    - Objets, ou classes `IDispatch`dérivées de , disponibles pour l’automatisation.

    - Fichiers XML de tableau de commande *(.vsct).* Pour plus d’informations, consultez [les fichiers visual Studio table de commande (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Testez, déboçonner et démarrez votre type de projet.

7. Affichez votre projet dans **l’onglet Projet** de `VARIANT_TRUE` la boîte `VSHPROPID_ShowProjInSolutionPage`de dialogue **Add Reference** en définissant comme valeur pour . Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Créez le fichier Microsoft Installer (*.msi*) pour l’installation de vos VSPackages. Pour plus d’informations, voir [Installer VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), Enregistrer un type de [projet](../../extensibility/internals/registering-a-project-type.md), et [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Voir aussi
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quand créer des types de projets](../../extensibility/internals/when-to-create-project-types.md)
- [Créer des types de projets](../../extensibility/internals/creating-project-types.md)
