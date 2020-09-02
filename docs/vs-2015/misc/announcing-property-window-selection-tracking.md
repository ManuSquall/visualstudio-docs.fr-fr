---
title: Annonce du suivi de sélection de la fenêtre de propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002453"
---
# <a name="announcing-property-window-selection-tracking"></a>Annonce du suivi de sélection de la fenêtre Propriétés
Si vous souhaitez utiliser la fenêtre **Propriétés** ou les pages de **Propriétés** , par exemple un formulaire, du texte ou une sélection dont vous souhaitez afficher les propriétés, vous devez avoir une connaissance complète de la façon dont vous coordonnez la sélection. Par exemple, vous devez savoir si vous avez des sélections uniques ou des sélections multiples. Vous devez ensuite annoncer votre type de sélection (unique ou multiple) à l’IDE à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Cette interface fournit les informations requises par la fenêtre **Propriétés** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Pour annoncer la sélection à l’environnement  
  
1. Appelez `QueryInterface` pour <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Pour ce faire, utilisez le pointeur de site passé à la vue au moment de sa création.  
  
    2. Appelez `QueryService` à partir de la vue pour le `SID_STrackSelection` service.  
  
         Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> méthode chaque fois que votre sélection est modifiée et transmettez un pointeur vers un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     L’objet conteneur de sélection peut utiliser des sélections uniques ou multiples et contient les informations de sélection dans un `IDispatch` objet. L’appel de la <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> méthode notifie la fenêtre **Propriétés** que la sélection a changé. La fenêtre **Propriétés** utilise ensuite les objets sur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour déterminer si une ou plusieurs sélections ont eu lieu et les sélections d’objets réelles.  
  
     Si vous spécifiez une sélection multiple, la fenêtre **Propriétés** recherche l’intersection entre les propriétés communes des objets. Si vous spécifiez une sélection d’objet unique, la fenêtre **Propriétés** affiche toutes les propriétés de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../extensibility/internals/extending-properties.md)   
 [Pages de propriétés](../extensibility/internals/property-pages.md)