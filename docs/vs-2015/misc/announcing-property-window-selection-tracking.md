---
title: Annonce de suivi de sélection de fenêtre de propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 9639e0347689fc99e0b43c4b69394b522af984da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246738"
---
# <a name="announcing-property-window-selection-tracking"></a>Annonce du suivi de sélection de la fenêtre Propriétés
Si vous souhaitez travailler avec le **propriétés** fenêtre ou le **propriété** des pages, par exemple, un formulaire, texte ou une sélection pour lequel vous souhaitez voir les propriétés, puis vous devez avoir une connaissance complète de la façon vous coordonner la sélection. Par exemple, vous devez connaître si vous disposez d’une sélection unique ou plusieurs sélections. Vous devez ensuite annoncer votre type de sélection (un ou plusieurs) à l’IDE à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Cette interface fournit des informations requises par le **propriétés** fenêtre.  
  
### <a name="to-announce-selection-to-the-environment"></a>Annoncer la sélection à l’environnement  
  
1.  Appelez `QueryInterface` pour <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Pour ce faire, utilisez le pointeur de site passé à la vue lors de sa création.  
  
    2.  Appelez `QueryService` à partir de la vue pour la `SID_STrackSelection` service.  
  
         Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> méthode chaque fois que votre sélection change et passe un pointeur vers un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     L’objet de conteneur de sélection peut utiliser une ou plusieurs sélections et contient les informations de sélection dans un `IDispatch` objet. Appel de la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> méthode avertit le **propriétés** fenêtre la sélection a changé. Le **propriétés** fenêtre utilise ensuite les objets sur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour déterminer si une ou plusieurs sélections se sont produites, et quelles sont les sélections de l’objet réel.  
  
     Si vous spécifiez une sélection multiple, puis le **propriétés** fenêtre trouve l’intersection entre les propriétés communes pour les objets. Si vous spécifiez une sélection d’un objet unique, puis le **propriétés** fenêtre affiche toutes les propriétés de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les propriétés](../extensibility/internals/extending-properties.md)   
 [Pages de propriétés](../extensibility/internals/property-pages.md)