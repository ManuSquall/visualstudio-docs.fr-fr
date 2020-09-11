---
title: 'Liste de vérification : création de nouveaux types de projets | Microsoft Docs'
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
ms.openlocfilehash: f166e0b3280783dac891b3b582acd7822a3974c0
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011916"
---
# <a name="checklist-create-new-project-types"></a>Liste de vérification : créer des types de projets
Vous devez effectuer plusieurs tâches pour créer un nouveau type de projet. La liste de vérification suivante fournit un guide pour ces tâches :

1. Concevez les fonctionnalités pour votre nouveau type de projet. Pour plus d’informations, consultez [décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md).

2. Déterminez les éditeurs utilisés pour le code et d’autres éléments de projet. Vous pouvez utiliser les éditeurs de base ou standard, ou vous pouvez créer et utiliser des éditeurs spécifiques à un projet. Pour plus d’informations, consultez [créer des éditeurs et des concepteurs personnalisés](../../extensibility/creating-custom-editors-and-designers.md) et [Comment : ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md).

3. Déterminez le niveau de participation de vos éléments de projet dans la **affichage de classes** et dans l' **Explorateur d’objets**. Pour plus d’informations, consultez [prise en charge des outils de navigation de symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Dérivez les nouvelles classes en fonction des décisions de conception que vous avez prises précédemment pour vos projets et éléments de projet.

5. Écrivez le code pour les composants de type de projet suivants :

    - La fabrique de projets, pour gérer la création de projets et l’ouverture de projets existants. Pour plus d’informations, consultez [créer des instances de projet à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Gestion de la hiérarchie de projet et des commandes. Pour plus d’informations, consultez [utiliser les classes de projet HierUtil7 pour implémenter un type de projet (C++)](/previous-versions/bb166212(v=vs.100)), les [éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md), les [composants de base du modèle de projet](../../extensibility/internals/project-model-core-components.md)et [MenuCommands vs. OleMenuCommands](../../vs-2015/misc/menucommands-vs-olemenucommands.md?view=vs-2015).

    - Gestion des éléments de projet, y compris l’ajout de votre projet à la boîte de dialogue **nouveau projet** . Pour plus d’informations, consultez [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md) et inscrire des modèles de [projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistance de l’état du projet et des éléments individuels. Pour plus d’informations, consultez [ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md). Pour la persistance des informations de solution, consultez [solutions](../../extensibility/internals/solutions-overview.md).

    - Propriétés indépendantes de la configuration à afficher dans la Fenêtre Propriétés. Pour plus d’informations, consultez [étendre les propriétés](../../extensibility/internals/extending-properties.md).

    - Propriétés de configuration de projet telles qu’elles sont implémentées dans les pages de propriétés pour afficher les propriétés dépendantes de la configuration. Pour plus d’informations, consultez [gérer les options de configuration](../../extensibility/internals/managing-configuration-options.md).

    - Énumération des sorties pour le déploiement. Pour plus d’informations, consultez [configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

    - Services de démarrage de projet. Pour plus d’informations, consultez [éléments d’un modèle de projet et des composants de base du modèle de](../../extensibility/internals/elements-of-a-project-model.md) [projet](../../extensibility/internals/project-model-core-components.md).

    - Les objets, ou les classes dérivées de `IDispatch` , sont disponibles pour l’automatisation.

    - Fichiers de table de commandes XML (*. vsct*). Pour plus d’informations, consultez [fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Testez, déboguez et démarrez votre type de projet.

7. Affichez votre projet sous l’onglet **projet** de la boîte de dialogue **Ajouter une référence** en définissant `VARIANT_TRUE` comme valeur pour `VSHPROPID_ShowProjInSolutionPage` . Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Créez le fichier Microsoft Installer (*. msi*) pour l’installation de vos VSPackages. Pour plus d’informations, consultez [installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [inscrire un type de projet](../../extensibility/internals/registering-a-project-type.md)et [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Voir aussi
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Quand créer des types de projet](../../extensibility/internals/when-to-create-project-types.md)
- [Créer des types de projet](../../extensibility/internals/creating-project-types.md)