---
title: Projet Type Essentials (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706387"
---
# <a name="project-type-essentials"></a>Éléments fondamentaux sur le type de projet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comprend plusieurs types de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projets pour des langues telles que ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vous permet également de créer vos propres types de projets.

 Si vous voulez simplement ajouter des commandes personnalisées, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]des éditeurs ou des fenêtres d’outils à , vous pouvez le faire sans créer un nouveau type de projet. Pour plus d'informations, voir les rubriques suivantes :

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)

- [Extension et personnalisation des fenêtres d’outils](../../extensibility/extending-and-customizing-tool-windows.md)

  De même, si vous voulez personnaliser [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] le [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] comportement des types fournis et de projet, vous pouvez le faire en utilisant des sous-types de projet. Pour plus d’informations, voir [Project Subtypes](../../extensibility/internals/project-subtypes.md).

  Vous devez créer un nouveau type de projet pour [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] les projets qui sont basés sur une langue autre que et si vous voulez soutenir un ou plusieurs des suivants:

- Générer

- Déploiement

- Configurations multiples

- Contrôle de code source

- Débogage

- Articles de projet dans Solution Explorer

- Les boîtes de dialogue **Open Project** ou New **Project**

- Nidification de projet

- Pour plus d’informations sur les capacités des types de projets, voir ce qui suit :

- Les types de projets sont des objets d’un VSPackage qui implémentent l’ensemble d’interfaces. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Si vous utilisez C pour développer un type de projet, les classes de projets De projets De paquet géré implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, voir [Utiliser le cadre de paquet géré pour mettre en œuvre un type de projet](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Pour les développeurs de C, les cours de la bibliothèque HierUtil fonctionnent de la même manière. Pour plus d’informations, voir [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (CMD)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Les types de projets peuvent prendre en charge des données autres que les fichiers de code source typiques qui s’intègrent dans un assemblage .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les projets de base de données contiennent des références aux fichiers de script et de requête stockés sur disque et ajoutent des commandes à **Solution Explorer** pour exécuter les scripts et les requêtes contre une base de données, mais les projets ne prennent pas en charge le comportement de construction. Pour plus d’informations, voir [Les éléments du projet d’ouverture et d’économie](../../extensibility/internals/opening-and-saving-project-items.md).

- Un type de projet n’a pas à utiliser de fichiers du tout. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]donne aux types de projets un contrôle complet sur la façon dont ils persistent les données sur les projets et les éléments du projet. Pour plus d’informations, voir [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

- Les types de projets doivent fournir une usine de *projet,* qui est un objet qui crée une instance du type de projet chaque fois qu’on [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lui dit d’ouvrir ou de créer un projet qui est basé sur ce type de projet. Pour plus d’informations, voir [Créer des instances de projet en utilisant des usines de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Les types de projets doivent fournir des modèles pour les projets et les éléments du projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise les modèles lorsque les utilisateurs créent de nouveaux projets et ajoutent de nouveaux éléments aux projets existants. Pour plus d’informations, voir [Ajout de modèles d’éléments de projet et de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Les types de projets peuvent prendre en charge plusieurs configurations, telles que Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet en utilisant les pages de propriété que vous fournissez. Pour plus d’informations, voir [Options de configuration de gestion](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Voir aussi
- [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)
