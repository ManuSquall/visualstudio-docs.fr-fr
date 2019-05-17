---
title: Création d’Instances de projet à l’aide de fabriques de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3680af73c281a01a7938805f859e0ff88c1ba44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909982"
---
# <a name="create-project-instances-by-using-project-factories"></a>Créer des instances de projet à l’aide de fabriques de projet
Types de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliser un *fabrique de projet* pour créer des instances d’objets du projet. Une fabrique de projet est similaire à une fabrique de classe standard pour les objets COM cocreatable. Toutefois, les objets du projet ne sont pas cocreatable ; ils peuvent uniquement être créés à l’aide d’une fabrique de projet.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE appelle la fabrique de projets implémentée dans votre VSPackage lorsqu’un utilisateur charge un projet existant ou crée un nouveau projet dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Le nouvel objet de projet fournit l’IDE avec suffisamment d’informations pour remplir **l’Explorateur de solutions**. Le nouvel objet de projet fournit également les interfaces requises pour prendre en charge toutes les actions d’interface utilisateur pertinentes initiées par l’IDE.

 Vous pouvez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface dans une classe dans votre projet. En règle générale, il se trouve dans son propre module.

 Les projets qui prennent en charge l’agrégation par un propriétaire doivent conserver une clé de propriétaire dans leur fichier projet. Lorsque le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> méthode est appelée sur un projet avec une clé de propriétaire, le projet détenu convertit sa clé de propriétaire à une fabrique de projet GUID appelle ensuite la `CreateProject` méthode sur cette fabrique de projet pour effectuer la création réelle.

## <a name="create-an-owned-project"></a>Créer un projet détenu
 Un propriétaire crée un projet détenu en deux phases :

1. En appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> (méthode). Cela donne au projet détenu la possibilité de créer un objet de projet agrégé en fonction de l’entrée contrôlant `IUnknown`. Le projet détenu passe interne `IUnknown` et l’objet agrégé dans le projet propriétaire. Cela permet au projet détenu un magasin interne `IUnknown`.

2. En appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> (méthode). Le projet détenu effectue tout son instanciation lorsque cette méthode est appelée au lieu d’appeler `IVsProjectFactory::CreateProject` comme ce serait le cas pour les projets qui n’appartiennent pas. L’entrée `VSOWNEDPROJECTOBJECT` énumération est généralement le projet détenu agrégé. Le projet détenu peut utiliser cette variable pour déterminer si son objet de projet a déjà été créé (cookie différent de NULL) ou doit être créé (cookie égal à NULL).

   Types de projets sont identifiés par un GUID, similaire au CLSID d’un objet COM cocreatable unique du projet. En règle générale, un projet fabrique gère la création d’instances d’un type de projet unique, bien qu’il soit possible d’avoir une fabrique de projet gérer plusieurs GUID de type de projet.

   Types de projets sont associés à une extension de nom de fichier particulier. Lorsqu’un utilisateur tente d’ouvrir un fichier de projet existant ou tente de créer un nouveau projet en clonant un modèle, l’IDE utilise l’extension sur le fichier pour déterminer le GUID du projet correspondant.

   Dès que l’IDE détermine si elle doit créer un nouveau projet ou ouvrez un projet existant d’un type particulier, l’IDE utilise les informations dans le Registre système sous **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  pour rechercher le VSPackage implémente la fabrique de projet requis. L’IDE charge ce VSPackage. Dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (méthode), le VSPackage doit inscrire ses fabrique de projet avec l’IDE en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> (méthode).

   La méthode principale de la `IVsProjectFactory` interface est <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, qui doit gérer deux scénarios : ouvrez un projet existant et la création d’un nouveau projet. La plupart des projets stockent leur état de projet dans un fichier projet. En règle générale, les nouveaux projets sont créés en utilisant une copie du fichier de modèle passée à la `CreateProject` (méthode), puis en ouvrant la copie. Projets existants sont instanciés par directement de l’ouverture du fichier de projet passé à `CreateProject` (méthode). Le `CreateProject` méthode peut afficher les fonctionnalités d’interface utilisateur supplémentaires à l’utilisateur en fonction des besoins.

   Un projet peut également n’utiliser aucun fichier et, au lieu de cela, stocker son état de projet dans un mécanisme de stockage autre que le système de fichiers, comme une base de données ou d’un serveur Web. Dans ce cas, le paramètre de nom de fichier passé à la `CreateProject` méthode n’est pas réellement un chemin d’accès de système de fichiers, mais une chaîne unique, une URL, pour identifier les données de projet. Vous n’avez pas besoin de copier les fichiers de modèle qui sont passées à `CreateProject` pour déclencher la séquence de construction approprié doit être exécuté.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Liste de contrôle : Créer des types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)