---
title: Projets fichiers divers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707096"
---
# <a name="miscellaneous-files-project"></a>Projet Fichiers divers
Quand un utilisateur ouvre des éléments de projet, l’IDE affecte au projet fichiers divers tous les éléments qui ne sont pas membres de projets dans une solution.

 Les projets jouent un rôle important dans la détermination de l’éditeur qui est utilisé lorsqu’un utilisateur ouvre un élément de projet. Un projet peut être conçu pour ouvrir certains fichiers à l’aide d’un éditeur spécifique à un projet ou d’un éditeur standard.

 Un éditeur spécifique au projet requiert généralement que l’utilisateur ait une connaissance particulière ou utilise des interfaces spéciales du projet. Pour plus d’informations, consultez [Comment : ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md).

 Un éditeur standard peut ouvrir n’importe quel fichier d’une extension spécifique dans n’importe quel projet. L’utilisateur peut personnaliser certains éditeurs standard, tels que l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éditeur de texte, pour les projets tout en conservant leur caractère public. Les éditeurs standard sont créés à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode.

 Si aucun projet de la solution ne réagit et qu’il peut ouvrir un élément de projet, l’IDE fournit un projet spécial appelé projet fichiers divers qui ouvre n’importe quel fichier.

 Ce projet spécial permet d’ouvrir un fichier en dehors du contexte d’un projet. Pendant le traitement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> méthode, le projet fichiers divers répond toujours avec une priorité très basse. Par conséquent, le projet fichiers divers produit toujours un projet de priorité plus élevée qui peut ouvrir des fichiers.

 Le projet fichiers divers ne demande pas à l’utilisateur de le créer explicitement avec la boîte de dialogue **nouveau projet** . En outre, le projet fichiers divers ne gère pas de façon permanente une liste des membres du projet. Il utilise une fonctionnalité facultative pour enregistrer la liste des fichiers utilisés le plus récemment pour chaque utilisateur.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)
- [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
