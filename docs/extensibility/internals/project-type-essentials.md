---
title: Type de projet Essentials | Microsoft Docs
description: En savoir plus sur le moment où vous devez créer un type de projet et le moment où vous pouvez étendre un type de projet existant à l’aide des sous-types de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903554"
---
# <a name="project-type-essentials"></a>Éléments fondamentaux sur le type de projet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comprend plusieurs types de projets pour les langages tels que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous permet également de créer vos propres types de projets.

 Si vous souhaitez simplement ajouter des commandes personnalisées, des éditeurs ou des fenêtres outil à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous pouvez le faire sans créer un nouveau type de projet. Pour plus d'informations, voir les rubriques suivantes :

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)

- [Extension et personnalisation des fenêtres d’outils](../../extensibility/extending-and-customizing-tool-windows.md)

  De même, si vous souhaitez personnaliser le comportement des types de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet et fournis [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , vous pouvez le faire à l’aide des sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).

  Vous devez créer un nouveau type de projet pour les projets basés sur une langue autre que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] si vous souhaitez prendre en charge un ou plusieurs des éléments suivants :

- Build

- Déploiement

- Configurations multiples

- Contrôle de code source

- Débogage

- Éléments de projet dans Explorateur de solutions

- Boîtes de dialogue **ouvrir un projet** ou **nouveau projet**

- Imbrication de projets

- Pour plus d’informations sur les fonctionnalités des types de projet, consultez les rubriques suivantes :

- Les types de projets sont des objets d’un VSPackage qui implémentent l’ensemble d’interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attendu. Si vous utilisez C# pour développer un type de projet, les classes de projet de l’infrastructure de package managée implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, consultez [utilisation de l’infrastructure de package managé pour implémenter un type de projet (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Pour les développeurs C++, les classes de la bibliothèque HierUtil fonctionnent de la même manière. Pour plus d’informations, consultez [not in Build : utilisation des classes de projet HierUtil7 pour implémenter un type de projet (C++)](/previous-versions/bb166212(v=vs.100)).

- Les types de projet peuvent prendre en charge des données autres que des fichiers de code source classiques qui sont générés dans un assembly .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les projets de base de données contiennent des références à des fichiers de script et de requête stockés sur disque et ajoutent des commandes à **Explorateur de solutions** pour exécuter les scripts et les requêtes sur une base de données, mais les projets ne prennent pas en charge le comportement de génération. Pour plus d’informations, consultez [ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

- Un type de projet n’a pas besoin d’utiliser de fichiers. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] donne aux types de projets un contrôle total sur la façon dont ils rendent les données persistantes pour les projets et les éléments de projet. Pour plus d’informations, consultez [décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md).

- Les types de projets doivent fournir une *fabrique de projet*, qui est un objet qui crée une instance du type de projet chaque fois que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est invité à ouvrir ou à créer un projet basé sur ce type de projet. Pour plus d’informations, consultez [création d’instances de projet à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Les types de projets doivent fournir des modèles pour les projets et les éléments de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les modèles lorsque les utilisateurs créent de nouveaux projets et ajoutent de nouveaux éléments aux projets existants. Pour plus d’informations, consultez [Ajout de modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Les types de projet peuvent prendre en charge plusieurs configurations, telles que Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet à l’aide des pages de propriétés que vous fournissez. Pour plus d’informations, consultez [gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Voir aussi
- [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)