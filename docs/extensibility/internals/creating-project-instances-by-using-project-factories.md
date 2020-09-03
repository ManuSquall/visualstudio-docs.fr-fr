---
title: Création d’instances de projet à l’aide des fabriques de projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709063"
---
# <a name="create-project-instances-by-using-project-factories"></a>Créer des instances de projet à l’aide de fabriques de projets
Les types de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisent une *fabrique de projets* pour créer des instances d’objets de projet. Une fabrique de projet est semblable à une fabrique de classe standard pour les objets COM cocreatables. Toutefois, les objets de projet ne peuvent pas coexister ; ils peuvent uniquement être créés à l’aide d’une fabrique de projets.

 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE appelle la fabrique de projet implémentée dans votre VSPackage lorsqu’un utilisateur charge un projet existant ou crée un nouveau projet dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Le nouvel objet de projet fournit à l’IDE suffisamment d’informations pour remplir **Explorateur de solutions**. Le nouvel objet de projet fournit également les interfaces requises pour la prise en charge de toutes les actions d’IU pertinentes initiées par l’IDE.

 Vous pouvez implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface dans une classe de votre projet. En général, elle réside dans son propre module.

 Les projets qui prennent en charge l’agrégation par un propriétaire doivent rendre persistantes une clé de propriétaire dans leur fichier projet. Quand la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> méthode est appelée sur un projet avec une clé propriétaire, le projet détenu convertit sa clé propriétaire en GUID de fabrique de projet, puis appelle la `CreateProject` méthode sur cette fabrique de projet pour effectuer la création réelle.

## <a name="create-an-owned-project"></a>Créer un projet détenu
 Un propriétaire crée un projet détenu en deux phases :

1. En appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> méthode. Cela donne au projet détenu la possibilité de créer un objet de projet agrégé basé sur le contrôle d’entrée `IUnknown` . Le projet détenu passe le interne `IUnknown` et l’objet agrégé à nouveau au projet propriétaire. Cela donne au projet détenu la possibilité de stocker le interne `IUnknown` .

2. En appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> méthode. Le projet détenu effectue toute son instanciation lorsque cette méthode est appelée au lieu d’appeler comme c’est `IVsProjectFactory::CreateProject` le cas pour les projets qui ne sont pas détenus. L' `VSOWNEDPROJECTOBJECT` énumération d’entrée est généralement le projet détenu agrégé. Le projet détenu peut utiliser cette variable pour déterminer si son objet projet a déjà été créé (le cookie n’est pas égal à NULL) ou doit être créé (le cookie est égal à NULL).

   Les types de projets sont identifiés par un GUID de projet unique, similaire au CLSID d’un objet COM pouvant être cocréé. En règle générale, une fabrique de projets gère la création d’instances d’un seul type de projet, même s’il est possible d’avoir une fabrique de projet qui gère plusieurs GUID de type de projet.

   Les types de projets sont associés à une extension de nom de fichier particulière. Quand un utilisateur tente d’ouvrir un fichier projet existant ou tente de créer un nouveau projet en clonant un modèle, l’IDE utilise l’extension sur le fichier pour déterminer le GUID du projet correspondant.

   Dès que l’IDE détermine s’il doit créer un nouveau projet ou ouvrir un projet existant d’un type particulier, l’IDE utilise les informations du Registre système sous **[HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects]** pour trouver le VSPackage qui implémente la fabrique de projet requise. L’IDE charge ce VSPackage. Dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode, le VSPackage doit inscrire sa fabrique de projet auprès de l’IDE en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> méthode.

   La méthode principale de l' `IVsProjectFactory` interface est <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , qui doit gérer deux scénarios : l’ouverture d’un projet existant et la création d’un nouveau projet. La plupart des projets stockent leur état de projet dans un fichier projet. En général, les nouveaux projets sont créés en faisant une copie du fichier de modèle passé à la `CreateProject` méthode, puis en ouvrant la copie. Les projets existants sont instanciés en ouvrant directement le fichier projet passé à la `CreateProject` méthode. La `CreateProject` méthode peut afficher des fonctionnalités d’interface utilisateur supplémentaires pour l’utilisateur, si nécessaire.

   Un projet peut également utiliser aucun fichier et, à la place, stocker son état de projet dans un mécanisme de stockage autre que le système de fichiers, tel qu’une base de données ou un serveur Web. Dans ce cas, le paramètre de nom de fichier passé à la `CreateProject` méthode n’est pas un chemin de système de fichiers, mais une chaîne unique (une URL) pour identifier les données de projet. Vous n’avez pas besoin de copier les fichiers de modèle passés à `CreateProject` pour déclencher la séquence de construction appropriée à exécuter.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Liste de vérification : créer des types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
