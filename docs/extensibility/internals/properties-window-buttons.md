---
title: "Boutons de la fenêtre Propriétés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 950b9f0a7b0f38689042877a42499e23253e6486
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-buttons"></a>Boutons de la fenêtre Propriétés
Selon le langage de développement et le type de produit, certains boutons sont affichés par défaut dans la barre d’outils pour le **propriétés** fenêtre. Dans tous les cas, le **par catégorie**, **Alphabetized**, **propriétés**, et **Pages de propriétés** boutons sont affichés. Dans Visual c# et Visual Basic, le **événements** bouton s’affiche également. Dans des projets Visual C++, le **Messages VC ++** et **VC substitue** boutons sont affichés. Des boutons supplémentaires peuvent s’afficher pour les autres types de projet. Pour plus d’informations sur les boutons dans les **propriétés** fenêtre, consultez [fenêtre Propriétés](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implémentation de boutons de la fenêtre Propriétés  
 Lorsque vous cliquez sur le **par catégorie** bouton, Visual Studio appelle le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interface sur l’objet qui a le focus pour trier ses propriétés par catégorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>est implémentée sur le `IDispatch` objet qui est présenté à la **propriétés** fenêtre.  
  
 Il existe des catégories de propriété prédéfinie 11, qui ont des valeurs négatives. Vous pouvez définir des catégories personnalisées, mais nous recommandons d’attribuer les valeurs positives pour les différencier des catégories prédéfinies.  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> méthode retourne la valeur de catégorie de propriété appropriée pour la propriété spécifiée. Le <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> méthode retourne une chaîne qui contient le nom de catégorie. Vous avez uniquement prendre en charge les valeurs de catégorie personnalisée, car Visual Studio sait que les valeurs de catégorie de propriété standard.  
  
 Lorsque vous cliquez sur le **Alphabetized** bouton, les propriétés sont affichées dans l’ordre alphabétique par nom. Les noms sont récupérés par `IDispatch` selon un algorithme de tri localisé.  
  
 Lorsque le **propriétés** fenêtre est ouverte, la **propriétés** automatiquement du bouton est affiché comme étant sélectionnée. Dans d’autres parties de l’environnement, le même bouton s’affiche et vous pouvez cliquer dessus pour afficher la **propriétés** fenêtre.  
  
 Le **Pages de propriétés** bouton n’est pas disponible si `ISpecifyPropertyPages` n’est pas implémentée pour l’objet sélectionné. Propriétés dépendantes de la configuration d’affichage qui sont généralement associées à des projets et solutions des pages de propriétés, mais ils peuvent être également être associés à des éléments de projet (par exemple, dans Visual C++).  
  
> [!NOTE]
>  Vous ne pouvez pas ajouter des boutons de barre d’outils pour le **propriétés** fenêtre à l’aide de code non managé. Pour ajouter un bouton de barre d’outils, vous devez créer un objet managé qui dérive de <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)