---
title: Essentials du Type de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc60ae68f008cefd468af8a688e9aae9241ca3be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318956"
---
# <a name="project-type-essentials"></a>Éléments fondamentaux sur le type de projet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inclut plusieurs types de projets pour les langages tels que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet également de créer vos propres types de projet.

 Si vous souhaitez simplement ajouter des commandes personnalisées, des éditeurs ou des fenêtres Outil pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez le faire sans créer un nouveau type de projet. Pour plus d’informations, consultez les rubriques suivantes :

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)

- [Extension et personnalisation des fenêtres d’outils](../../extensibility/extending-and-customizing-tool-windows.md)

  De même, si vous souhaitez personnaliser le comportement de l’élément [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] types de projets, vous pouvez effectuer à l’aide de sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).

  Vous devez créer un nouveau type de projet pour les projets qui reposent sur une langue autre que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] si vous souhaitez prendre en charge un ou plusieurs des opérations suivantes :

- Build

- Déploiement

- Plusieurs configurations

- Contrôle de code source

- Débogage

- Éléments de projet dans l’Explorateur de solutions

- Le **ouvrir un projet** ou **nouveau projet** boîtes de dialogue

- Imbrication de projet

- Pour plus d’informations sur les fonctionnalités des types de projets, consultez les rubriques suivantes :

- Types de projets sont des objets dans un VSPackage qui implémentent l’ensemble des interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attend. Si vous utilisez c# pour développer un type de projet, les classes de projet Managed Package Framework implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, consultez [à l’aide de Managed Package Framework pour implémenter un Type de projet (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Pour les développeurs C++, les classes dans la bibliothèque HierUtil fonctionnent de manière similaire. Pour plus d’informations, consultez [pas dans la génération : À l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Types de projets peuvent prendre en charge les données autres que les fichiers de code source typique qui s’appuient dans un assembly .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des projets de base de données contiennent des références aux fichiers de script et de requête stockés sur le disque et ajouter des commandes à **l’Explorateur de solutions** pour exécuter les scripts et les requêtes sur une base de données, mais les projets ne gèrent pas générer un comportement. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

- Un type de projet n’a pas utiliser les fichiers. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] donne aux types de projet de contrôle total sur la façon dont ils conserver les données pour les projets et éléments de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).

- Types de projets doivent fournir un *fabrique de projet*, qui est un objet qui crée une instance du projet tapez chaque fois que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est informée pour ouvrir ou créer un projet basé sur ce type de projet. Pour plus d’informations, consultez [création projet Instances par à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Types de projets doivent fournir des modèles de projets et éléments de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les modèles lorsque les utilisateurs, créer des projets et ajouter de nouveaux éléments à des projets existants. Pour plus d’informations, consultez [Ajout d’un projet et des modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Types de projets peuvent prendre en charge plusieurs configurations, telles que Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet à l’aide des pages de propriétés que vous fournissez. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Voir aussi
- [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)