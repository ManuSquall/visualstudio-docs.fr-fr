---
title: Ajout de modèles d’éléments de projet et de projet . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710209"
---
# <a name="add-project-and-project-item-templates"></a>Ajouter des modèles de projet et d’élément de projet
Lorsque vous créez vos propres types de projets, vous devez vous [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] soutenir pour l’ajout de nouveaux projets et de nouveaux éléments de projet en utilisant les boîtes de dialogue standard intégrées de l’environnement de développement intégré (IDE). Les sujets suivants traitent des différentes techniques d’ajout de projets et d’éléments de projet.

## <a name="in-this-section"></a>Contenu de cette section
- [Contexte du projet](../../extensibility/internals/project-context.md)

 Explique que le projet fournit la plupart des informations contextuelles sur ce qui se passe dans l’environnement.

- [Priorité du projet](../../extensibility/internals/project-priority.md)

 Explique qu’un élément de projet est généralement membre d’un projet pour aider à éviter l’ambiguïté sur le projet utilisé pour ouvrir l’article.

- [Projet Divers Files](../../extensibility/internals/miscellaneous-files-project.md)

 Fournit des informations sur les deux types d’éditeurs qui peuvent être utilisés pour ouvrir des fichiers dans un projet et le rôle que joue le projet dans la détermination de l’éditeur à utiliser lorsqu’un élément de projet est ouvert.

- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)

 Explique ce qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se passe lorsqu’un projet est créé.

- [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Explique le processus d’ajout d’éléments à la boîte de dialogue **Add New Item.**

- [Ajouter des répertoires à la boîte de dialogue du nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Fournit un exemple d’enregistrement d’un nouvel annuaire qui contient des modèles personnalisés mis à disposition par un VSPackage.

- [Ajouter des répertoires à la boîte de dialogue Add New Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Fournit un exemple d’enregistrement d’un nouvel ensemble d’annuaires pour la boîte de dialogue **Add New Item.**

- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Répertorie différents types d’éléments de commande utilisés pour étendre les systèmes de projet.

- [CATIDs pour les objets qui sont généralement utilisés pour étendre les projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Listes CATIDs pour les objets [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]qui [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sont utilisés pour étendre , , et les systèmes de projet.

## <a name="related-sections"></a>Sections connexes
- [Comment : Ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)

 Fournit des instructions étape par étape pour l’ouverture d’un élément intrinsèquement lié à un éditeur spécifique pour un projet.

- [Comment : Ouvrir les éditeurs standard](../../extensibility/how-to-open-standard-editors.md)

 Fournit des instructions étape par étape pour l’ouverture d’un éditeur standard.

- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)

 Fournit des liens vers des sujets conceptuels de sous-type de projet. Les sous-types de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projets étendent les projets existants et existants.

- [Types de projet](../../extensibility/internals/project-types.md)

 Fournit des liens vers d’autres sujets qui offrent des informations sur la façon de concevoir de nouveaux types de projets.
