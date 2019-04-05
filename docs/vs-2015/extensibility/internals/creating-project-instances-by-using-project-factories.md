---
title: Création d’Instances de projet à l’aide de fabriques de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b33d5d1a09425a18f0c9489b15147e3355e45c99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949633"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Création d’instances de projets à l’aide de fabriques de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Types de projets dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utiliser un *fabrique de projet* pour créer des instances d’objets du projet. Une fabrique de projet est similaire à une fabrique de classe standard pour les objets COM cocreatable. Toutefois, les objets du projet ne sont pas cocreatable : ils peuvent uniquement être créés à l’aide d’une fabrique de projet.  
  
 Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE appelle la fabrique de projets implémentée dans votre VSPackage lorsqu’un utilisateur charge un projet existant ou crée un nouveau projet dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Le nouvel objet de projet fournit l’IDE avec suffisamment d’informations pour remplir l’Explorateur de solutions. Le nouvel objet de projet fournit également les interfaces requises pour prendre en charge toutes les actions d’interface utilisateur pertinentes initiées par l’IDE.  
  
 Vous pouvez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface dans une classe dans votre projet. En règle générale, il se trouve dans son propre module.  
  
 Pour obtenir un exemple d’implémentation de la `IVsProjectFactory` l’interface, consultez PrjFac.cpp qui est contenue dans le [projet de base](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) répertoire d’exemple.  
  
 Les projets qui prennent en charge l’agrégation par un propriétaire doivent conserver une clé de propriétaire dans leur fichier projet. Lorsque le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> méthode est appelée sur un projet avec une clé de propriétaire, le projet détenu convertit sa clé de propriétaire à une fabrique de projet GUID appelle ensuite la `CreateProject` méthode sur cette fabrique de projet pour effectuer la création réelle.  
  
## <a name="creating-an-owned-project"></a>Création d’un projet détenu  
 Un propriétaire crée un projet détenu en deux phases :  
  
1. En appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> (méthode). Cela donne au projet détenu la possibilité de créer un objet de projet agrégé en fonction de l’entrée contrôlant `IUnknown`. Le projet détenu passe interne `IUnknown` et l’objet agrégé dans le projet propriétaire. Cela permet au projet détenu un magasin interne `IUnknown`.  
  
2. En appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> (méthode). Le projet détenu effectue tout son instanciation lorsque cette méthode est appelée au lieu d’appeler `IVsProjectFactory::CreateProject` comme ce serait le cas pour les projets qui n’appartiennent pas. L’entrée `VSOWNEDPROJECTOBJECT` énumération est généralement le projet détenu agrégé. Le projet détenu peut utiliser cette variable pour déterminer si son objet de projet a déjà été créé (cookie différent de NULL) ou doit être créé (cookie égal à NULL).  
  
   Types de projets sont identifiés par un GUID, similaire au CLSID d’un objet COM cocreatable unique du projet. En règle générale, un projet fabrique gère la création d’instances d’un type de projet unique, bien qu’il soit possible d’avoir une fabrique de projet gérer plusieurs GUID de type de projet.  
  
   Types de projets sont associés à une extension de nom de fichier particulier. Lorsqu’un utilisateur tente d’ouvrir un fichier de projet existant ou tente de créer un nouveau projet en clonant un modèle, l’IDE utilise l’extension sur le fichier pour déterminer le GUID du projet correspondant.  
  
   Dès que l’IDE détermine que s’il doit créer un nouveau projet ou ouvrez un projet existant d’un type particulier, l’IDE utilise les informations dans le Registre système sous [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] pour rechercher l' VSPackage implémente la fabrique de projet requis. L’IDE charge ce VSPackage. Dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (méthode), le VSPackage doit inscrire ses fabrique de projet avec l’IDE en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> (méthode).  
  
   La méthode principale de la `IVsProjectFactory` interface est <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> qui doit gérer deux scénarios : ouvrez un projet existant et la création d’un nouveau projet. La plupart des projets stockent leur état de projet dans un fichier projet. En règle générale, les nouveaux projets sont créés en utilisant une copie du fichier de modèle passée à la `CreateProject` (méthode), puis en ouvrant la copie. Projets existants sont instanciés par directement de l’ouverture du fichier de projet passé à `CreateProject` (méthode). Le `CreateProject` méthode peut afficher les fonctionnalités d’interface utilisateur supplémentaires à l’utilisateur en fonction des besoins.  
  
   Un projet peut également n’utiliser aucun fichier et, au lieu de cela, stocker son état de projet dans un mécanisme de stockage autre que le système de fichiers, comme une base de données ou d’un serveur Web. Dans ce cas, le paramètre de nom de fichier passé à la `CreateProject` méthode n’est pas réellement un chemin d’accès de système de fichiers, mais une chaîne unique, une URL, pour identifier les données de projet. Vous n’avez pas besoin de copier les fichiers de modèle qui sont passées à `CreateProject` pour déclencher la séquence de construction approprié doit être exécuté.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)
