---
title: Ajout de projet et modèles d’élément de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c89f38c98047a8fab57317c491c051474995f472
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963655"
---
# <a name="add-project-and-project-item-templates"></a>Ajouter le projet et les modèles d’élément de projet
Lorsque vous créez vos propres types de projet, vous devez fournir la prise en charge pour l’ajout de nouveaux projets et éléments de projet à l’aide de la norme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intégrées des boîtes de dialogue de l’environnement (IDE) de développement. Les rubriques suivantes traitent des différentes techniques pour l’ajout de projets et éléments de projet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte du projet](../../extensibility/internals/project-context.md)  
 Explique que le projet fournit la plupart des informations de contexte pour ce qui se passe réellement dans l’environnement.  
  
 [Priorité de projet](../../extensibility/internals/project-priority.md)  
 Explique qu’un élément de projet est généralement un membre d’un projet pour aider à éviter toute ambiguïté sur lequel le projet est utilisé pour ouvrir l’élément.  
  
 [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)  
 Fournit des informations sur les deux types d’éditeurs qui peuvent être utilisées pour ouvrir des fichiers dans un projet et le rôle de la lecture du projet pour déterminer quel éditeur à utiliser lors de l’ouverture d’un élément de projet.  
  
 [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explique ce qui se produit lorsqu’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet est créé.  
  
 [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explique le processus d’ajout d’éléments à la **ajouter un nouvel élément** boîte de dialogue.  
  
 [Ajouter des répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fournit un exemple de l’inscription d’un répertoire qui contient les modèles personnalisés mis à disposition par un VSPackage.  
  
 [Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fournit un exemple de l’inscription d’un nouvel ensemble de répertoires pour les **ajouter un nouvel élément** boîte de dialogue.  
  
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Répertorie les différents types d’éléments de commande utilisés pour l’extension des systèmes de projet.  
  
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Répertorie le CATID pour les objets qui sont utilisés pour étendre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systèmes de projet.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour Ouvrez éditeurs spécifiques du projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions détaillées pour l’ouverture d’un élément intrinsèquement lié à un éditeur spécifique pour un projet.  
  
 [Guide pratique pour Éditeurs standards Open](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions détaillées pour l’ouverture d’un éditeur standard.  
  
 [Sous-types de projet](../../extensibility/internals/project-subtypes.md)  
 Fournit des liens vers des rubriques conceptuelles de sous-type de projet. Étendent les sous-types de projet existant [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projets.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui offrent des informations sur la façon de concevoir de nouveaux types de projet.