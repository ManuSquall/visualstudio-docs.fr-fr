---
title: Masquage des propriétés qui ont des propriétés enfants | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505616"
---
# <a name="hiding-properties-that-have-child-properties"></a>Masquage des propriétés qui ont des propriétés enfants
Vous pouvez masquer les propriétés qui ont des propriétés enfants :  
  
-   Si vous avez des projets imbriqués, où le projet parent contrôle par programmation certains aspects du projet enfant.  
  
-   Si vous utilisez un contrôle avec un concepteur spécialement conçu et vous ne souhaitez pas que permettre aux développeurs un accès complet à toutes les propriétés du contrôle.  
  
-   Si vous possédez la propriété étendue d’un objet et que vous souhaitez restreindre l’affichage des propriétés.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Pour masquer les propriétés qui ont des propriétés enfants  
  
1.  Définir le `pfDisplay` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> à `FALSE`.  
  
2.  Définir le `pfHide` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> à `TRUE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la grille Propriétés](../extensibility/internals/properties-display-grid.md)