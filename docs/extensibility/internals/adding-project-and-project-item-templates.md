---
title: "Ajout de projet et mod&#232;les d&#39;&#233;l&#233;ment de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), ajouter"
  - "éléments de projet (Visual Studio), ajout"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Ajout de projet et mod&#232;les d&#39;&#233;l&#233;ment de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous créez vos propres types de projet, vous devez fournir une prise en charge d'ajouter de nouveaux projets et éléments de projet à l'aide de les boîtes de dialogue standard d'environnement de développement intégré \(IDE\) \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Les rubriques suivantes expliquent différentes techniques pour ajouter des projets et des éléments de projet.  
  
## Dans cette section  
 [Contexte du projet](../../extensibility/internals/project-context.md)  
 Explique que le projet fournit la plupart des informations de contexte pour ce qui transpire dans l'environnement.  
  
 [Priorité du projet](../../extensibility/internals/project-priority.md)  
 Explique qu'un élément de projet est généralement un membre d'un projet d'aider à éviter toute ambiguïté sur le projet est utilisé pour ouvrir l'élément.  
  
 [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)  
 Fournit des informations sur les deux types d'éditeur qui peuvent être utilisés pour ouvrir des fichiers dans un projet et le rôle le projet utilise pour déterminer quel éditeur à utiliser lorsqu'un élément de projet est ouvert.  
  
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explique ce qui se produit lorsqu'un projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est créé.  
  
 [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explique le processus pour ajouter des éléments à la boîte de dialogue d' **Ajouter un nouvel élément** .  
  
 [Ajout de répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fournit un exemple d'enregistrer un nouveau répertoire qui contient des modèles personnalisés rendues disponibles par un VSPackage.  
  
 [Ajout de répertoires à la boîte de dialogue Nouvel élément Ajouter](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fournit un exemple d'inscrire un nouvel ensemble de répertoires pour la boîte de dialogue d' **Ajouter un nouvel élément** .  
  
 [Commandes définies par l'IDE pour l'extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Répertorie les différents types d'éléments de commande utilisés pour étendre les systèmes de projet.  
  
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 répertorie CATIDs pour les objets qui sont utilisés pour étendre [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], et des systèmes de projet de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## Rubriques connexes  
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)  
 Fournit des instructions pour ouvrir un élément intrinsèquement lié à un éditeur spécifique à un projet.  
  
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)  
 Fournit des instructions pour ouvrir un éditeur standard.  
  
 [Sous\-types de projets](../../extensibility/internals/project-subtypes.md)  
 Fournit des liens vers des rubriques conceptuelles de sous\-type de projet.  Sous\-types de projet étendent existant [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et les projets de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
 [Types de projet](../../extensibility/internals/project-types.md)  
 Fournit des liens vers les rubriques supplémentaires qui offrent des informations sur la conception de nouveaux types de projet.