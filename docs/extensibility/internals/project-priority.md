---
title: Priorité du projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee4c0f41902e74f58684d6806877d352447351bf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725394"
---
# <a name="project-priority"></a>Priorité de projet
Un élément de projet est généralement membre d’un seul projet dans la solution. Par conséquent, l’IDE peut facilement déterminer quel projet est utilisé pour ouvrir l’élément. Toutefois, si un élément est membre de plusieurs projets, l’IDE utilise un schéma de priorité pour déterminer le projet le mieux adapté à l’ouverture de l’élément.

 La liste suivante présente le schéma de priorité du projet :

- L’IDE appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> pour chaque projet de la solution pour déterminer si le document est membre de ce projet.

- Si le document est membre du projet, le projet répond avec une priorité assignée par le projet en fonction de sa gestion de ce document. Par exemple, un projet de langage répond avec une priorité élevée pour ses fichiers sources de langage, mais répond avec une priorité inférieure pour un type de fichier non reconnu qui n’est pas utilisé dans le cadre de son processus de génération.

- Les projets qui fournissent des éditeurs personnalisés spécifiques au projet ou des concepteurs pour un document reçoivent également une priorité élevée.

- L’énumération <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> fournit les valeurs de priorité de document.

- Le projet qui spécifie la priorité la plus élevée reçoit le contexte permettant d’ouvrir le document. Si deux projets retournent des valeurs de priorité égales, le projet actif est préféré. Si aucun projet de la solution ne réagit et qu’il peut ouvrir le document, l’IDE place le document dans le projet fichiers divers. Pour plus d’informations, consultez [projet fichiers divers](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Voir aussi
- [Projet Fichiers divers](../../extensibility/internals/miscellaneous-files-project.md)
- [Guide pratique pour ouvrir des éditeurs pour les documents ouverts](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)