---
title: Objets contextuelles de sélection Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705512"
---
# <a name="selection-context-objects"></a>Objets de contexte de sélection
L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) utilise un objet global de contexte de sélection pour déterminer ce qui doit être affiché dans l’IDE. Chaque fenêtre de l’IDE peut avoir son propre objet de contexte de sélection poussé au contexte de sélection globale. L’IDE met à jour le contexte de sélection global avec des valeurs à partir d’une fenêtre lorsque cette fenêtre a l’accent. Pour plus d’informations, voir [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).

 Chaque cadre de fenêtre ou site dans <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>l’IDE a un service appelé . L’objet créé par votre VSPackage qui est situé `QueryService` dans le cadre <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> de la fenêtre doit appeler la méthode pour obtenir un pointeur à l’interface.

 Les fenêtres de cadre peuvent empêcher une partie de leurs informations contextuelles de sélection d’être propagées au contexte global de sélection lorsqu’elles sont lancées. Cette capacité est utile pour les fenêtres d’outils qui peuvent avoir à commencer par une sélection vide.

 La modification du contexte de sélection global déclenche des événements que VSPackages peut surveiller. VSPackages peut effectuer les tâches `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> suivantes en implémentant et interfaces :

- Mettre à jour le fichier actuellement actif dans une hiérarchie.

- Surveiller les modifications apportées à certains types d’éléments. Par exemple, si votre VSPackage utilise une fenêtre **Propriétés** spéciales, vous pouvez surveiller les changements dans la fenêtre **Active Properties** et redémarrer la vôtre au besoin.

  La séquence suivante montre le cours typique du suivi de sélection.

1. L’IDE récupère le contexte de sélection de la fenêtre nouvellement ouverte et le met dans le contexte de sélection globale. Si le contexte de sélection utilise HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, cette information n’est pas propagée au contexte mondial. Pour plus d’informations, voir [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md).

2. Les événements de notification sont diffusés à tout VSPackage qui les a demandés.

3. Le VSPackage agit sur les événements qu’il reçoit en effectuant des activités telles que la mise à jour d’une hiérarchie, la réactivation d’un outil ou d’autres tâches similaires.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Types de projets](../../extensibility/internals/project-types.md)
