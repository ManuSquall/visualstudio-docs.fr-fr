---
title: 'Procédure : Ouvrir des éditeurs pour les Documents ouverts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8342947681bcd8f698c2a646e917b353ec6c9dd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319328"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procédure : Ouvrir des éditeurs pour les documents ouverts
Avant d’un projet s’ouvre une fenêtre de document, le projet devez d’abord déterminer si le fichier est déjà ouvert dans la fenêtre de document pour un autre éditeur. Le fichier peut être soit ouvert dans un éditeur spécifique au projet ou un des éditeurs standards inscrit avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="open-a-project-specific-editor"></a>Ouvrez un éditeur spécifique au projet
 Utilisez la procédure suivante pour ouvrir un éditeur spécifique au projet pour un fichier qui est déjà ouvert.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Pour ouvrir un éditeur spécifique au projet pour un fichier ouvert

1. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.

    Cet appel retourne des pointeurs vers la hiérarchie du document, élément de hiérarchie et le frame de fenêtre, le cas échéant.

2. Si le document est ouvert, le projet doit vérifier a posteriori si seul un objet de données de document existe, ou si un objet de vue de document est également présent.

   - Si un objet de vue de document existe, et cette vue est pour une autre hiérarchie ou un élément de la hiérarchie, le projet utilise le pointeur de frame de fenêtre de la vue pour resurface la fenêtre existante.

   - Si un objet de vue de document existe, et cette vue est pour la même hiérarchie et un élément de la hiérarchie, le projet peut ouvrir une seconde vue si s’attacher à l’objet de données sous-jacent. Sinon, le projet doit utiliser le pointeur de frame de fenêtre de la vue à resurface la fenêtre existante.

   - Si seul l’objet de données existe, le projet doit déterminer s’il peut utiliser l’objet de données pour sa vue. Si l’objet de données est compatible, terminé les étapes décrites dans [ouvrir un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).

     Si l’objet de données n’est pas compatible, une erreur doit être affichée à l’utilisateur qui indique que le fichier est actuellement en cours d’utilisation. Cette erreur doit être affichée uniquement dans les cas temporaires, tels que lors de la compilation d’un fichier en même temps l’utilisateur tente d’ouvrir le fichier à l’aide d’un éditeur autre que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal éditeur de texte. L’éditeur de texte principal peut partager des objets de données de document avec le compilateur.

3. Si le document n’est pas ouvert, car il n’existe aucun objet de données de document ou d’un objet de vue de document, suivez les étapes de [ouvrir un éditeur spécifique au projet](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Ouvrez un éditeur standard
 Utilisez la procédure suivante pour ouvrir un éditeur standard d’un fichier qui est déjà ouvrir.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Pour ouvrir un éditeur standard d’un fichier ouvert

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Cette méthode vérifie d’abord que le document n’est pas déjà ouvert en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Si le document est déjà ouvert, sa fenêtre d’éditeur est remontée.

2. Si le document n’est pas ouvert, puis suivez les étapes de [Comment : Ouvrir des éditeurs standard](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Voir aussi
- [Ouvrir et enregistrer des éléments de projet](../extensibility/internals/opening-and-saving-project-items.md)
- [Guide pratique pour Ouvrez éditeurs spécifiques du projet](../extensibility/how-to-open-project-specific-editors.md)
- [Guide pratique pour Éditeurs standards Open](../extensibility/how-to-open-standard-editors.md)
