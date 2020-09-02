---
title: Priorité du projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429910"
---
# <a name="project-priority"></a>Priorité de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un élément de projet est généralement membre d’un seul projet dans la solution. Par conséquent, l’IDE peut facilement déterminer quel projet est utilisé pour ouvrir l’élément. Toutefois, si un élément est membre de plusieurs projets, l’IDE utilise un schéma de priorité pour déterminer le projet le mieux adapté à l’ouverture de l’élément.  
  
 La liste suivante présente le schéma de priorité du projet :  
  
- L’IDE appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> méthode pour chaque projet de la solution pour déterminer si le document est membre de ce projet.  
  
- Si le document est membre du projet, le projet répond avec une priorité assignée par le projet en fonction de sa gestion de ce document. Par exemple, un projet de langage répond avec une priorité élevée pour ses fichiers sources de langage, mais répond avec une priorité inférieure pour un type de fichier non reconnu qui n’est pas utilisé dans le cadre de son processus de génération.  
  
- Les projets qui fournissent des éditeurs personnalisés spécifiques au projet ou des concepteurs pour un document reçoivent également une priorité élevée.  
  
- L' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération fournit les valeurs de priorité de document.  
  
- Le projet qui spécifie la priorité la plus élevée reçoit le contexte permettant d’ouvrir le document. Si deux projets retournent des valeurs de priorité égales, le projet actif est préféré. Si aucun projet de la solution ne réagit et qu’il peut ouvrir le document, l’IDE place le document dans le projet fichiers divers. Pour plus d’informations, consultez [projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)   
 [Procédure : ouvrir les éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
