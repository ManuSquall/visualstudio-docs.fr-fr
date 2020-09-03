---
title: Ajout de modèles de projet et d’élément de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203857"
---
# <a name="adding-project-and-project-item-templates"></a>Ajout d’un projet et de modèles d’élément de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous créez vos propres types de projets, vous devez fournir la prise en charge de l’ajout de nouveaux projets et éléments de projet à l’aide des boîtes de dialogue de l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement de développement intégré (IDE) standard. Les rubriques suivantes décrivent les différentes techniques permettant d’ajouter des projets et des éléments de projet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte de projet](../../extensibility/internals/project-context.md)  
 Explique que le projet fournit la plupart des informations de contexte pour ce qui se passe dans l’environnement.  
  
 [Priorité de projet](../../extensibility/internals/project-priority.md)  
 Explique qu’un élément de projet est généralement membre d’un projet afin d’éviter toute ambiguïté quant au projet utilisé pour ouvrir l’élément.  
  
 [Projet Fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)  
 Fournit des informations sur les deux types d’éditeurs qui peuvent être utilisés pour ouvrir des fichiers dans un projet et le rôle joué par le projet dans la détermination de l’éditeur à utiliser lorsqu’un élément de projet est ouvert.  
  
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explique ce qui se produit lors de la création d’un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projet.  
  
 [Ajout d’éléments aux boîtes de dialogue Ajouter un élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explique le processus d’ajout d’éléments à la boîte de dialogue **Ajouter un nouvel élément** .  
  
 [Ajout de répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fournit un exemple d’inscription d’un nouveau répertoire qui contient des modèles personnalisés mis à disposition par un VSPackage.  
  
 [Ajout de répertoires à la boîte de dialogue Ajouter un élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fournit un exemple d’inscription d’un nouvel ensemble de répertoires pour la boîte de dialogue **Ajouter un nouvel élément** .  
  
 [Commandes définies par l’IDE pour l’extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Répertorie les différents types d’éléments de commande utilisés pour l’extension des systèmes de projet.  
  
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Répertorie les CATID des objets utilisés pour étendre [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] des [!INCLUDE[csprcs](../../includes/csprcs-md.md)] systèmes de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projet, et.  
  
## <a name="related-sections"></a>Sections connexes  
 [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions pas à pas pour ouvrir un élément lié intrinsèquement à un éditeur spécifique pour un projet.  
  
 [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions pas à pas pour ouvrir un éditeur standard.  
  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 Fournit des liens vers des rubriques conceptuelles sur le sous-type de projet. Les sous-types de projet étendent [!INCLUDE[csprcs](../../includes/csprcs-md.md)] les projets et existants [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit des liens vers des rubriques supplémentaires qui fournissent des informations sur la façon de concevoir de nouveaux types de projets.
