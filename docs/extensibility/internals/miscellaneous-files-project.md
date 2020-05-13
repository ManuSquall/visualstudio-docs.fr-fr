---
title: Projet de fichiers divers (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707096"
---
# <a name="miscellaneous-files-project"></a>Projet Fichiers divers
Lorsqu’un utilisateur ouvre des éléments de projet, l’IDE assigne aux Fichiers Divers tout élément qui ne fait partie d’aucun projet dans une solution.

 Les projets jouent un rôle important dans la détermination de l’éditeur utilisé lorsqu’un utilisateur ouvre un élément de projet. Un projet peut être conçu pour ouvrir certains fichiers en utilisant un éditeur spécifique à un projet ou un éditeur standard.

 Un éditeur spécifique au projet exige généralement que l’utilisateur ait des connaissances particulières ou utilise des interfaces spéciales du projet. Pour plus d’informations, voir [Comment : Ouvrir les rédacteurs spécifiques au projet](../../extensibility/how-to-open-project-specific-editors.md).

 Un éditeur standard peut ouvrir n’importe quel fichier d’une extension spécifique dans n’importe quel projet. L’utilisateur peut personnaliser certains éditeurs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] standard, tels que l’éditeur de texte, pour les projets, tout en conservant leur caractère public. Les éditeurs standard sont <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> créés en utilisant la méthode.

 Si aucun projet dans la solution ne répond qu’il peut ouvrir un élément de projet, l’IDE fournit un projet spécial appelé le projet Divers Files qui ouvre n’importe quel fichier.

 Ce projet spécial prévoit l’ouverture d’un fichier en dehors du cadre d’un projet. Pendant le traitement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> de la méthode, le projet Divers Files répond toujours avec une très faible priorité. Par conséquent, le projet Divers Files donne toujours à tout projet de priorité supérieure qui peut ouvrir des fichiers.

 Le projet Miscellaneous Files n’oblige pas l’utilisateur à le créer explicitement avec la boîte de dialogue **du nouveau projet.** De plus, le projet Divers Files ne gère pas de façon permanente une liste des membres du projet. Il utilise une fonctionnalité facultative pour enregistrer une liste des fichiers les plus récemment utilisés pour chaque utilisateur.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Guide pratique pour ouvrir des éditeurs spécifiques à un projet](../../extensibility/how-to-open-project-specific-editors.md)
- [Guide pratique pour ouvrir des éditeurs standard](../../extensibility/how-to-open-standard-editors.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
