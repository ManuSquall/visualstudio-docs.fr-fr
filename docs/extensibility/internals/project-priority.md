---
title: Priorité de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c58c248650c0ba1e5fdc1fc5c9310b3e4530fbe4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994525"
---
# <a name="project-priority"></a>Priorité de projet
Un élément de projet est généralement un membre d’un seul projet dans la solution. Par conséquent, l’IDE peut facilement déterminer le projet qui est utilisé pour ouvrir l’élément. Toutefois, si un élément est un membre de plusieurs projets, l’IDE utilise un schéma de priorité pour déterminer le projet meilleures pour l’ouverture de l’élément.  
  
 La liste suivante présente les schémas de priorité de projet :  
  
-   Les appels de l’IDE le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> méthode pour chaque projet dans la solution pour déterminer si le document est un membre de ce projet.  
  
-   Si le document est un membre du projet, le projet répond avec une priorité que le projet affecte en fonction de sa gestion de ce document. Par exemple, un projet de langage répond avec une priorité élevée pour ses fichiers sources du langage, mais répond avec une priorité plus faible pour un type de fichier non reconnu qui n’est pas utilisé dans le cadre de son processus de génération.  
  
-   Les projets qui fournissent des éditeurs personnalisés, spécifique au projet ou les concepteurs pour un document reçoivent également une priorité élevée.  
  
-   Le <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> énumération fournit des valeurs de priorité le document.  
  
-   Le projet qui spécifie la priorité la plus élevée est fonction du contexte pour ouvrir le document. Si deux projets retournent des valeurs de priorité égale, le projet actif est préféré. Si aucun projet dans la solution ne répond qu’il peut ouvrir le document, l’IDE place le document dans le projet fichiers divers. Pour plus d’informations, consultez [le projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)   
 [Guide pratique pour Ouvrir des éditeurs pour les Documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)