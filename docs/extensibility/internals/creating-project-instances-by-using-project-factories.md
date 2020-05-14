---
title: Créer des instances de projet en utilisant des usines de projets . Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709063"
---
# <a name="create-project-instances-by-using-project-factories"></a>Créer des instances de projet en utilisant des usines de projet
Types de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets à l’utilisation d’une usine de *projet* pour créer des instances d’objets de projet. Une usine de projet est similaire à une usine de classe standard pour les objets COM cocréatables. Cependant, les objets du projet ne sont pas cocréatables; ils ne peuvent être créés qu’à l’aide d’une usine de projet.

 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle l’usine de projet mise en œuvre dans votre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage quand un utilisateur charge un projet existant ou crée un nouveau projet en . Le nouvel objet du projet fournit à l’IDE suffisamment d’informations pour peupler **Solution Explorer**. Le nouvel objet du projet fournit également les interfaces requises pour prendre en charge toutes les actions d’interface utilisateur pertinentes initiées par l’IDE.

 Vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> implémenter l’interface dans une classe de votre projet. Typiquement, il réside dans son propre module.

 Les projets qui appuient l’agrégation d’un propriétaire doivent persister dans le dossier de son projet. Lorsque <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> la méthode est appelée sur un projet avec une clé propriétaire, le projet possédé `CreateProject` convertit sa clé propriétaire à une usine de projet GUID appelle alors la méthode sur cette usine de projet pour faire la création réelle.

## <a name="create-an-owned-project"></a>Créer un projet appartenant
 Un propriétaire crée un projet en deux phases :

1. En appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> la méthode. Cela donne au projet détenu une chance de créer un `IUnknown`objet de projet agrégé basé sur le contrôle des entrées . Le projet possédé `IUnknown` transmet l’objet intérieur et l’objet agrégé au projet propriétaire. Cela donne au projet possédé une `IUnknown`chance de stocker l’intérieur .

2. En appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> la méthode. Le projet possédé fait toute son instantanéisation lorsque `IVsProjectFactory::CreateProject` cette méthode est appelée au lieu d’appeler comme ce serait le cas pour les projets qui ne sont pas possédés. Le `VSOWNEDPROJECTOBJECT` recensement des intrants est généralement le projet agrégé. Le projet possédé peut utiliser cette variable pour déterminer si son objet de projet a déjà été créé (cookie n’est pas égal NULL) ou doit être créé (cookie égale NULL).

   Les types de projets sont identifiés par un projet unique GUID, semblable au CLSID d’un objet COM cocréatable. En règle générale, une usine de projet gère la création d’instances d’un seul type de projet, bien qu’il soit possible d’avoir une usine de projet gérer plus d’un type de projet GUID.

   Les types de projets sont associés à une extension particulière du nom de fichier. Lorsqu’un utilisateur tente d’ouvrir un fichier de projet existant ou tente de créer un nouveau projet en clonant un modèle, l’IDE utilise l’extension du fichier pour déterminer le projet GUID correspondant.

   Dès que l’IDE détermine s’il doit créer un nouveau projet ou ouvrir un projet existant d’un type particulier, l’IDE utilise les informations contenues dans le registre du système dans le cadre **de [HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio-8.0- Projects]** pour déterminer quels VSPackage implémente l’usine de projet requise. L’IDE charge ce VSPackage. Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> la méthode, le VSPackage doit enregistrer son usine <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> de projet avec l’IDE en appelant la méthode.

   La principale méthode `IVsProjectFactory` de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>l’interface est , qui devrait gérer deux scénarios: l’ouverture d’un projet existant et la création d’un nouveau projet. La plupart des projets stockent leur état de projet dans un dossier de projet. En règle générale, de nouveaux projets sont créés en faisant une copie du fichier modèle transmis à la `CreateProject` méthode, puis en ouvrant la copie. Les projets existants sont instantanés en `CreateProject` ouvrant directement le dossier du projet transmis à la méthode. La `CreateProject` méthode peut afficher des fonctionnalités d’interface utilisateur supplémentaires à l’utilisateur si nécessaire.

   Un projet ne peut pas non plus utiliser de fichiers et, au lieu de cela, stocker son état de projet dans un mécanisme de stockage autre que le système de fichiers, comme une base de données ou un serveur Web. Dans ce cas, le paramètre `CreateProject` de nom de fichier transmis à la méthode n’est pas réellement une trajectoire de système de fichiers, mais une chaîne unique — une URL — pour identifier les données du projet. Vous n’avez pas besoin de copier `CreateProject` les fichiers de modèle qui sont passés pour déclencher la séquence de construction appropriée à exécuter.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Liste de contrôle : Créer de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
