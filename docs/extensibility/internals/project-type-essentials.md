---
title: Essentials du Type de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>Essentials de Type de projet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]inclut plusieurs types de projet pour les langages tels que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vous permet également de créer vos propres types de projet.  
  
 Si vous souhaitez simplement ajouter des commandes personnalisées, éditeurs ou des fenêtres Outil à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez le faire sans créer un nouveau type de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Commandes, Menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Extension et personnalisation des fenêtres Outil](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 De même, si vous souhaitez personnaliser le comportement de l’élément [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] des types de projets, vous pouvez effectuer à l’aide de sous-types de projets. Pour plus d’informations, consultez [sous-types de projets](../../extensibility/internals/project-subtypes.md).  
  
 Vous devez créer un nouveau type de projet pour les projets qui sont basées sur une langue autre que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] si vous souhaitez prendre en charge un ou plusieurs des opérations suivantes :  
  
-   Build  
  
-   Déploiement  
  
-   Plusieurs configurations  
  
-   Contrôle de code source  
  
-   Débogage  
  
-   Éléments de projet dans l’Explorateur de solutions  
  
-   Le **ouvrir un projet** ou **nouveau projet** boîtes de dialogue  
  
-   Imbrication de projet  
  
-   Pour plus d’informations sur les fonctionnalités des types de projet, consultez les rubriques suivantes :  
  
-   Types de projets sont des objets qui implémentent l’ensemble des interfaces dans un VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attend. Si vous utilisez c# pour développer un type de projet, les classes du projet Managed Package Framework implémentent les interfaces nécessaires pour vous et vous permettent d’hériter de cette implémentation. Pour plus d’informations, consultez [à l’aide de Managed Package Framework pour implémenter un Type de projet (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Pour les développeurs C++, les classes de la bibliothèque HierUtil fonctionnent de manière similaire. Pour plus d’informations, consultez [pas dans la génération : utilisation de Classes de projet HierUtil7 pour implémenter un Type de projet (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Types de projets peuvent prendre en charge les données autres que des fichiers de code source typique générer dans un assembly .exe ou .dll. Par exemple, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des projets de base de données contient des références aux fichiers de script et de requête stockés sur disque et ajouter des commandes à **l’Explorateur de solutions** pour exécuter les scripts et les requêtes sur une base de données, mais les projets ne gèrent pas le comportement de génération. Pour plus d’informations, consultez [d’ouverture et l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Un type de projet n’a pas d’utiliser des fichiers. Par exemple, un type de projet peut stocker toutes ses données dans une base de données. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fournit des types de projets contrôler comment les conserver les données pour les projets et éléments de projet. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Types de projet doivent fournir un *factory de projet*, qui est un objet qui crée une instance du projet tapez chaque fois que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est invité à ouvrir ou créer un projet basé sur ce type de projet. Pour plus d’informations, consultez [création de projet Instances par à l’aide de projet fabriques](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Les types de projet doivent fournir des modèles de projets et des éléments de projet. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise les modèles lorsque les utilisateurs, créer des projets et ajouter de nouveaux éléments à des projets existants. Pour plus d’informations, consultez [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Types de projets peuvent prendre en charge plusieurs configurations, par exemple Debug et Release. Les utilisateurs peuvent modifier les différentes configurations d’un projet à l’aide des pages de propriétés que vous fournissez. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de projets de déploiement](../../extensibility/internals/deploying-project-types.md)
