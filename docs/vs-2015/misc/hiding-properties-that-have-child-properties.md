---
title: Masquage des propriétés qui ont des propriétés enfants | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822384"
---
# <a name="hiding-properties-that-have-child-properties"></a>Masquage des propriétés qui ont des propriétés enfants
Vous souhaitez masquer les propriétés qui ont des propriétés enfants :  
  
- Si vous avez des projets imbriqués où le projet parent contrôle par programmation certains aspects du projet enfant.  
  
- Si vous utilisez un contrôle avec un concepteur spécialisé et que vous ne souhaitez pas accorder aux développeurs un accès complet à toutes les propriétés du contrôle.  
  
- Si vous avez la propriété d’étendue d’un objet et que vous souhaitez limiter l’affichage des propriétés.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Pour masquer les propriétés qui ont des propriétés enfants  
  
1. Définissez le `pfDisplay` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> sur `FALSE` .  
  
2. Définissez le `pfHide` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> sur `TRUE` .  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la grille Propriétés](../extensibility/internals/properties-display-grid.md)