---
title: Essentials du Type de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cdb6aabe2e7379c063e7347389deb467d724be3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952849"
---
# <a name="project-type-essentials"></a>Éléments fondamentaux sur le type de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] inclut plusieurs types de projets pour les langages tels que [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vous permet également de créer vos propres types de projet.  
  
 Si vous souhaitez simplement ajouter des commandes personnalisées, des éditeurs ou des fenêtres Outil pour [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vous pouvez le faire sans créer un nouveau type de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Extensions de l’éditeur et du service de langage](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Extension et personnalisation des fenêtres d’outils](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  De même, si vous souhaitez personnaliser le comportement de l’élément [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] types de projets, vous pouvez effectuer à l’aide de sous-types de projet. Pour plus d’informations, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
  Vous devez créer un nouveau type de projet pour les projets qui reposent sur une langue autre que [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] si vous souhaitez prendre en charge un ou plusieurs des opérations suivantes :  
  
- Build  
  
- Déploiement  
  
- Plusieurs configurations  
  
- Contrôle de code source  
  
- Débogage  
  
- Éléments de projet dans l’Explorateur de solutions  
  
- Le **ouvrir un projet** ou **nouveau projet** boîtes de dialogue  
  
- Imbrication de projet  
  
- Pour plus d’informations sur les fonctionnalités des types de projets, consultez les rubriques suivantes :  
  
- Types de projets sont des objets dans un VSPackage qui implémentent l’ensemble des interfaces [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] attend. Si vous utilisez C# pour développer un type de projet, les classes de projet Managed Package Framework implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, consultez [à l’aide de Managed Package Framework pour implémenter un Type de projet (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Pour les développeurs C++, les classes dans la bibliothèque HierUtil fonctionnent de manière similaire. Pour plus d’informations, consultez [pas dans la génération : À l’aide des Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Types de projets peuvent prendre en charge les données autres que les fichiers de code source typique qui s’appuient dans un assembly .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] des projets de base de données contiennent des références aux fichiers de script et de requête stockés sur le disque et ajouter des commandes à **l’Explorateur de solutions** pour exécuter les scripts et les requêtes sur une base de données, mais les projets ne gèrent pas générer un comportement. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Un type de projet n’a pas utiliser les fichiers. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] donne aux types de projet de contrôle total sur la façon dont ils conserver les données pour les projets et éléments de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
- Types de projets doivent fournir un *fabrique de projet*, qui est un objet qui crée une instance du projet tapez chaque fois que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est informée pour ouvrir ou créer un projet basé sur ce type de projet. Pour plus d’informations, consultez [création projet Instances par à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Types de projets doivent fournir des modèles de projets et éléments de projet. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilise les modèles lorsque les utilisateurs, créer des projets et ajouter de nouveaux éléments à des projets existants. Pour plus d’informations, consultez [Ajout d’un projet et des modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Types de projets peuvent prendre en charge plusieurs configurations, telles que Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet à l’aide des pages de propriétés que vous fournissez. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)
