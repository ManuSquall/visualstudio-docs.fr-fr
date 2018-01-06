---
title: "Comment : ouvrir les éditeurs pour les Documents ouverts | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4c6321644cb59f55ad1335249aec5b071aef4ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-editors-for-open-documents"></a>Comment : ouvrir les éditeurs pour les Documents ouverts
Avant qu’un projet s’ouvre une fenêtre de document, le projet devez d’abord déterminer si le fichier est déjà ouvert dans la fenêtre de document pour un autre éditeur. Le fichier peut être soit ouvert dans un éditeur spécifique au projet, ou un éditeur standard inscrit auprès de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Ouverture d’un éditeur spécifique au projet  
 Utilisez la procédure suivante pour ouvrir un éditeur spécifique au projet pour un fichier qui est déjà ouvert.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Pour ouvrir un éditeur spécifique au projet pour un fichier ouvert  
  
1.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Cet appel retourne des pointeurs vers la hiérarchie du document, élément de hiérarchie et le frame de fenêtre, le cas échéant.  
  
2.  Si le document est ouvert, le projet doit vérifier si seul un objet de données de document existe, ou si un objet de vue de document est également présent.  
  
    -   Si un objet de vue de document existe et que cette vue est pour une autre hiérarchie ou un élément de la hiérarchie, le projet utilise le pointeur vers le frame de fenêtre de la vue à resurface la fenêtre existante.  
  
    -   Si un objet de vue de document existe et que cette vue est pour la même hiérarchie et d’un élément de la hiérarchie, le projet peut ouvrir une seconde vue si elle peut ajouter à l’objet de données de document sous-jacent. Dans le cas contraire, le projet doit utiliser le pointeur vers le frame de fenêtre de la vue à resurface la fenêtre existante.  
  
    -   Si seul l’objet de données de document existe, le projet doit déterminer s’il peut utiliser l’objet de données de document pour son affichage. Si l’objet de données de document est compatible, terminé les étapes décrites dans [ouverture d’un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si l’objet de données de document n’est pas compatible, une erreur doit être affichée à l’utilisateur qui indique que le fichier est actuellement en cours d’utilisation. Cette erreur doit s’afficher que dans les cas temporaires, tels que lors de la compilation d’un fichier à la fois l’utilisateur tente d’ouvrir le fichier à l’aide d’un éditeur autre que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur de texte principal. L’éditeur de texte principal peut partager objet de données de document avec le compilateur.  
  
3.  Si le document n’est pas ouvert, car il n’existe aucun objet de données de document ou d’un objet de vue de document, effectuez les étapes de [ouverture d’un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Ouvrir un éditeur Standard  
 Utilisez la procédure suivante pour ouvrir un éditeur standard d’un fichier qui est déjà ouvrir.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Pour ouvrir un éditeur standard d’un fichier ouvert  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Cette méthode vérifie d’abord que le document n’est pas déjà ouvert en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Si le document est déjà ouvert, sa fenêtre de l’éditeur est remontée.  
  
2.  Si le document n’est pas ouvert, puis effectuez les étapes de [Comment : ouvrir les éditeurs Standard](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir les éditeurs spécifiques au projet](../extensibility/how-to-open-project-specific-editors.md)   
 [Guide pratique pour ouvrir des éditeurs standard](../extensibility/how-to-open-standard-editors.md)