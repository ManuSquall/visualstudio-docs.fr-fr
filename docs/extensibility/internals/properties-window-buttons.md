---
title: Boutons de la fenêtre Propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d21e8d13ef8af83b12d30b6c78c253f371a11c30
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973861"
---
# <a name="properties-window-buttons"></a>Boutons de la fenêtre Propriétés
Selon le langage de développement et le type de produit, certains boutons sont affichés par défaut sur la barre d’outils pour le **propriétés** fenêtre. Dans tous les cas, le **par catégorie**, **Alphabetized**, **propriétés**, et **Pages de propriétés** boutons sont affichés. Dans Visual c# et Visual Basic, le **événements** bouton s’affiche également. Dans des projets Visual C++, le **VC ++ Messages** et **VC remplace** boutons sont affichés. Boutons supplémentaires peuvent s’afficher pour les autres types de projets. Pour plus d’informations sur les boutons dans la **propriétés** fenêtre, consultez [fenêtre Propriétés](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implémentation de boutons de la fenêtre Propriétés  
 Lorsque vous cliquez sur le **par catégorie** bouton, Visual Studio appelle le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interface sur l’objet qui a le focus pour trier ses propriétés par catégorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> est implémenté sur le `IDispatch` objet qui est présentée à la **propriétés** fenêtre.  
  
 Il existe 11 catégories de propriété prédéfinie, qui ont des valeurs négatives. Vous pouvez définir des catégories personnalisées, mais nous vous recommandons d’attribuer les valeurs positives pour les différencier des catégories prédéfinies.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> méthode retourne la valeur de catégorie de propriété appropriée pour la propriété spécifiée. Le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> méthode retourne une chaîne qui contient le nom de catégorie. Vous devez uniquement fournir prise en charge pour les valeurs de catégorie personnalisée, car Visual Studio sait que les valeurs de catégorie de propriété standard.  
  
 Lorsque vous cliquez sur le **Alphabetized** bouton, les propriétés sont affichées dans l’ordre alphabétique par nom. Les noms sont récupérés par `IDispatch` selon un algorithme de tri localisé.  
  
 Lorsque le **propriétés** fenêtre est ouverte, le **propriétés** bouton s’affiche automatiquement comme étant sélectionnée. Dans d’autres parties de l’environnement, le même bouton s’affiche et vous pouvez cliquer dessus pour afficher le **propriétés** fenêtre.  
  
 Le **Pages de propriétés** bouton n’est pas disponible si `ISpecifyPropertyPages` n’est pas implémentée pour l’objet sélectionné. Propriétés dépendantes de la configuration d’affichage qui sont généralement associées aux solutions et projets de pages de propriétés, mais ils peuvent être également être associés à des éléments de projet (par exemple, dans Visual C++).  
  
> [!NOTE]
>  Vous ne pouvez pas ajouter des boutons de barre d’outils pour le **propriétés** fenêtre à l’aide de code non managé. Pour ajouter un bouton de barre d’outils, vous devez créer un objet managé qui dérive de <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)