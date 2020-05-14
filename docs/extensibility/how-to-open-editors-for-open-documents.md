---
title: 'Comment : Ouvrir les rédacteurs pour les documents ouverts (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710916"
---
# <a name="how-to-open-editors-for-open-documents"></a>Comment : Ouvrir les éditeurs pour les documents ouverts
Avant l’ouverture d’un projet d’une fenêtre de document, le projet doit d’abord déterminer si le fichier est déjà ouvert dans la fenêtre de document d’un autre éditeur. Le fichier peut être ouvert soit dans un éditeur spécifique au [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]projet, soit dans l’un des éditeurs standard enregistrés auprès .

## <a name="open-a-project-specific-editor"></a>Ouvrir un éditeur spécifique au projet
 Utilisez la procédure suivante pour ouvrir un éditeur spécifique au projet pour un fichier déjà ouvert.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Ouvrir un éditeur spécifique à un projet pour un fichier ouvert

1. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Cet appel renvoie des indications à la hiérarchie du document, l’élément de hiérarchie et le cadre de fenêtre, le cas échéant.

2. Si le document est ouvert, le projet doit vérifier si seul un objet de données documentaire existe ou si un objet de vue de document est également présent.

   - Si un objet de vue de document existe, et que cette vue est pour une hiérarchie ou un élément de hiérarchie différent, le projet utilise le pointeur du cadre de fenêtre de la vue pour refaire surface la fenêtre existante.

   - Si un objet de vue de document existe, et que cette vue est pour la même hiérarchie et l’élément de hiérarchie, le projet peut ouvrir une deuxième vue s’il peut s’attacher à l’objet de données de document sous-jacent. Dans le cas contraire, le projet devrait utiliser le pointeur du cadre de la fenêtre de la vue pour refaire surface la fenêtre existante.

   - Si seul l’objet de données de document existe, le projet doit déterminer s’il peut utiliser l’objet de données de document pour sa vue. Si l’objet de données de document est compatible, remplissez les étapes discutées dans [Open, un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).

     Si l’objet de données de document n’est pas compatible, une erreur doit être affichée à l’utilisateur qui indique que le fichier est actuellement utilisé. Cette erreur ne doit être affichée que dans des cas transitoires, comme lorsqu’un fichier est compilé en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] même temps que l’utilisateur essaie d’ouvrir le fichier en utilisant un éditeur autre que l’éditeur de texte de base. L’éditeur de texte de base peut partager l’objet de données de documents avec le compilateur.

3. Si le document n’est pas ouvert parce qu’il n’y a pas d’objet de données documentaires ou d’objet de vue documentaire, remplissez les étapes [d’Open un éditeur spécifique au projet.](../extensibility/how-to-open-project-specific-editors.md)

## <a name="open-a-standard-editor"></a>Ouvrez un éditeur standard
 Utilisez la procédure suivante pour ouvrir un éditeur standard pour un fichier qui est déjà ouvert.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Ouvrir un éditeur standard pour un fichier ouvert

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Cette méthode vérifie d’abord que le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>document n’est pas déjà ouvert en appelant . Si le document est déjà ouvert, alors sa fenêtre d’éditeur est refaite.

2. Si le document n’est pas ouvert, alors remplissez les étapes de [Comment : Ouvrir les éditeurs standard](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Voir aussi
- [Ouvrir et enregistrer les éléments du projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Comment : Ouvrir les éditeurs spécifiques au projet](../extensibility/how-to-open-project-specific-editors.md)
- [Comment : Ouvrir les éditeurs standard](../extensibility/how-to-open-standard-editors.md)
