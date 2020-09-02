---
title: 'Procédure : ouvrir des éditeurs pour des documents ouverts | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204149"
---
# <a name="how-to-open-editors-for-open-documents"></a>Guide pratique pour ouvrir des éditeurs pour les documents ouverts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avant qu’un projet n’ouvre une fenêtre de document, le projet doit d’abord déterminer si le fichier est déjà ouvert dans la fenêtre de document pour un autre éditeur. Le fichier peut être ouvert dans un éditeur spécifique au projet ou dans l’un des éditeurs standard inscrits auprès de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="opening-a-project-specific-editor"></a>Ouverture d’un éditeur spécifique au projet  
 Utilisez la procédure suivante pour ouvrir un éditeur spécifique au projet pour un fichier déjà ouvert.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Pour ouvrir un éditeur spécifique au projet pour un fichier ouvert  
  
1. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .  
  
    Cet appel retourne des pointeurs vers la hiérarchie, l’élément de hiérarchie et le frame de fenêtre du document, le cas échéant.  
  
2. Si le document est ouvert, le projet doit vérifier s’il existe uniquement un objet de données de document ou si un objet de vue de document est également présent.  
  
   - S’il existe un objet de vue de document et que cet affichage est destiné à un autre élément de hiérarchie ou de hiérarchie, le projet utilise le pointeur vers le frame de fenêtre de la vue pour répartir la fenêtre existante.  
  
   - S’il existe un objet de vue de document et que cet affichage concerne le même hiérarchie et l’élément de hiérarchie, le projet peut ouvrir une deuxième vue s’il peut être attaché à l’objet de données de document sous-jacent. Dans le cas contraire, le projet doit utiliser le pointeur vers le frame de fenêtre de la vue pour resurfacer la fenêtre existante.  
  
   - Si seul l’objet de données de document existe, le projet doit déterminer s’il peut utiliser l’objet de données de document pour sa vue. Si l’objet de données de document est compatible, suivez les étapes décrites dans [ouverture d’un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si l’objet de données de document n’est pas compatible, une erreur doit s’afficher pour l’utilisateur, indiquant que le fichier est en cours d’utilisation. Cette erreur ne doit être affichée que dans des cas temporaires, par exemple lorsqu’un fichier est en cours de compilation en même temps que l’utilisateur tente d’ouvrir le fichier à l’aide d’un éditeur autre que l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur de texte principal. L’éditeur de texte principal peut partager un objet de données de document avec le compilateur.  
  
3. Si le document n’est pas ouvert, car il n’existe aucun objet de données de document ou objet de vue de document, effectuez les étapes de l' [ouverture d’un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Ouverture d’un éditeur standard  
 Utilisez la procédure suivante pour ouvrir un éditeur standard pour un fichier déjà ouvert.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Pour ouvrir un éditeur standard pour un fichier ouvert  
  
1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Cette méthode vérifie d’abord que le document n’est pas déjà ouvert en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Si le document est déjà ouvert, sa fenêtre d’éditeur est réexposée.  
  
2. Si le document n’est pas ouvert, effectuez les étapes de la [procédure : ouvrir les éditeurs standard](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ouverture et enregistrement d’éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Comment : ouvrir des éditeurs spécifiques à un projet](../extensibility/how-to-open-project-specific-editors.md)   
 [Guide pratique pour ouvrir des éditeurs standard](../extensibility/how-to-open-standard-editors.md)
