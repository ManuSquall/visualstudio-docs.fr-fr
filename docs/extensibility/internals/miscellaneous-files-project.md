---
title: Projet fichiers divers | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>Projet fichiers divers
Lorsqu’un utilisateur ouvre les éléments de projet, l’IDE assigne au projet fichiers divers tous les éléments qui ne sont pas membres de tous les projets dans une solution.  
  
 Projets jouent un rôle important dans la détermination de l’éditeur est utilisé lorsqu’un utilisateur ouvre un élément de projet. Un projet peut être conçu pour ouvrir certains fichiers à l’aide d’un éditeur spécifique au projet ou un éditeur standard.  
  
 Un éditeur spécifique au projet nécessite généralement que l’utilisateur ont des connaissances spéciales ou utiliser des interfaces spéciales à partir du projet. Pour plus d’informations, consultez [Comment : ouvrir les éditeurs spécifique au projet](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un éditeur standard permettre ouvrir n’importe quel fichier d’une extension spécifique dans un projet. L’utilisateur peut personnaliser certains éditeurs standards, tels que le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur de texte, pour les projets conserver, tout en conservant leur caractère public. Éditeurs standards sont créés à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (méthode).  
  
 Si aucun projet de la solution ne répond qu’il puisse ouvrir un élément de projet, l’IDE fournit un projet spécial appelé projet fichiers divers qui ouvre un fichier.  
  
 Ce projet spécial fournit pour l’ouverture d’un fichier en dehors du contexte d’un projet. Lors du traitement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> (méthode), le projet fichiers divers toujours répond avec une priorité très basse. Par conséquent, les fichiers divers de projet toujours donne à tout projet présentant une priorité plus élevée qui peuvent ouvrir les fichiers.  
  
 Le projet fichiers divers ne nécessite pas l’utilisateur à créer explicitement le **nouveau projet** boîte de dialogue. En outre, le projet fichiers divers ne gère pas définitivement une liste des membres du projet. Il utilise une fonctionnalité facultative pour enregistrer une liste des derniers fichiers utilisés pour chaque utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Comment : ouvrir les éditeurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md)   
 [Comment : ouvrir les éditeurs Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Ajout de projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)