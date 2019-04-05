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
ms.openlocfilehash: 8bc6510936e25e61ef47bb813b77e6efbf063573
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954079"
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