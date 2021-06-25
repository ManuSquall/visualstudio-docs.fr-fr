---
title: Objets de contexte de sélection | Microsoft Docs
description: Découvrez les éléments internes de la façon dont l’IDE de Visual Studio utilise un objet de contexte de sélection globale pour déterminer ce qui doit être affiché dans l’IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c97108eaba426a4def4c1052d3adc7348eb88b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898485"
---
# <a name="selection-context-objects"></a>Objets de contexte de sélection
L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) utilise un objet de contexte de sélection global pour déterminer ce qui doit être affiché dans l’IDE. Chaque fenêtre de l’IDE peut avoir son propre objet de contexte de sélection envoyé au contexte de sélection globale. L’IDE met à jour le contexte de sélection global avec les valeurs d’une fenêtre lorsque cette fenêtre a le focus. Pour plus d’informations, consultez [les commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).

 Chaque frame de fenêtre ou site dans l’IDE a un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . L’objet créé par le VSPackage qui est sur site dans le frame de fenêtre doit appeler la `QueryService` méthode pour obtenir un pointeur vers l' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface.

 Les fenêtres Frame peuvent empêcher des parties de leurs informations de contexte de sélection d’être propagées vers le contexte de sélection global lorsqu’elles sont démarrées. Cette fonctionnalité est utile pour les fenêtres outil qui peuvent être amenées à démarrer avec une sélection vide.

 La modification du contexte de sélection global déclenche les événements que les VSPackages peuvent surveiller. Les VSPackages peuvent effectuer les tâches suivantes en implémentant les `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfaces et :

- Met à jour le fichier actuellement actif dans une hiérarchie.

- Surveiller les modifications apportées à certains types d’éléments. Par exemple, si votre VSPackage utilise une fenêtre de **Propriétés** spéciale, vous pouvez surveiller les modifications dans la fenêtre **Propriétés** actives et redémarrer la vôtre lorsque cela est nécessaire.

  La séquence suivante montre le parcours classique du suivi de sélection.

1. L’IDE récupère le contexte de sélection de la nouvelle fenêtre ouverte et le place dans le contexte de sélection global. Si le contexte de sélection utilise HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, ces informations ne sont pas propagées vers le contexte global. Pour plus d’informations, consultez [les commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).

2. Les événements de notification sont diffusés à tout VSPackage qui les a demandés.

3. Le VSPackage agit sur les événements qu’il reçoit en effectuant des activités telles que la mise à jour d’une hiérarchie, la réactivation d’un outil ou d’autres tâches similaires.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Types de projets](../../extensibility/internals/project-types.md)
