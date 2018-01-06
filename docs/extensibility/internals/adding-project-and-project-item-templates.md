---
title: "Ajout de projet et modèles d’élément de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1d0c9e684312468011f63bdfbb72d1cdadba6b08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-project-and-project-item-templates"></a>Ajout de projet et modèles d’élément de projet
Lorsque vous créez vos propres types de projet, vous devez fournir la prise en charge pour l’ajout de nouveaux projets et éléments de projet à l’aide de la norme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intégré des boîtes de dialogue de l’environnement (IDE) de développement. Les rubriques suivantes traitent des différentes techniques pour ajouter des projets et éléments de projet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte de projet](../../extensibility/internals/project-context.md)  
 Explique que le projet fournit la plupart des informations de contexte pour ce qui apparaît dans l’environnement.  
  
 [Priorité de projet](../../extensibility/internals/project-priority.md)  
 Explique qu’un élément de projet est généralement un membre d’un projet pour aider à éviter toute ambiguïté sur lequel le projet est utilisé pour ouvrir l’élément.  
  
 [Projet Fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)  
 Fournit des informations sur les deux types d’éditeurs qui peuvent être utilisés pour ouvrir des fichiers dans un projet et le rôle de la lecture du projet dans la détermination de l’éditeur à utiliser lorsqu’un élément de projet est ouvert.  
  
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explique ce qui se produit lorsqu’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet est créé.  
  
 [Ajout d’éléments aux boîtes de dialogue Ajouter un élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explique le processus d’ajout d’éléments à la **ajouter un nouvel élément** boîte de dialogue.  
  
 [Ajout de répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fournit un exemple d’inscription d’un nouveau répertoire qui contient les modèles personnalisés mis à disposition par un VSPackage.  
  
 [Ajout de répertoires à la boîte de dialogue Ajouter un élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fournit un exemple de l’inscription d’un nouvel ensemble de répertoires pour les **ajouter un nouvel élément** boîte de dialogue.  
  
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Répertorie les différents types d’éléments de commande utilisés pour l’extension des systèmes de projet.  
  
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Répertorie les CATID pour les objets qui sont utilisés pour étendre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systèmes de projet.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions détaillées pour l’ouverture d’un élément intrinsèquement lié à un éditeur spécifique pour un projet.  
  
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions détaillées pour l’ouverture d’un éditeur standard.  
  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 Fournit des liens vers des rubriques conceptuelles de sous-type de projet. Les sous-types de projet étendent existant [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projets.  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui fournissent des informations sur la façon de concevoir de nouveaux types de projet.