---
title: "Affichent les propriétés de grille | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>Afficher la grille Propriétés
Le **propriétés** fenêtre affiche les champs dans une grille. La colonne de gauche contient les noms de propriété ; la colonne de droite contient les valeurs de propriété.  
  
## <a name="working-with-the-grid"></a>Utilisation de la grille  
 La liste de deux colonnes affiche les propriétés de configuration indépendant qui peuvent être modifiées au moment du design et leurs paramètres actuels. Notez que toutes les propriétés ne peuvent pas être affichées. Une propriété peut être définie comme masqué, par exemple, en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> (méthode). Plus précisément, pour masquer les propriétés qui ont des propriétés enfants :  
  
1.  Définir le `pfDisplay` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> à `FALSE`.  
  
2.  Définir le `pfHide` paramètre dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> à `TRUE`.  
  
 Pour pousser les informations vers le **propriétés** fenêtre, l’IDE utilise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>est appelée par les VSPackages pour chaque fenêtre qui contient des objets sélectionnables avec des propriétés connexes à afficher dans le **propriétés** fenêtre. **L’Explorateur de solutions**d’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> appelle `GetProperty` à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> dans votre hiérarchie de projet pour acquérir les objets parcourus dans la hiérarchie.  
  
 Si votre VSPackage ne prend pas en charge <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, l’IDE tente d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> à l’aide de la valeur de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que l’ou les éléments hiérarchie fournissent.  
  
 Votre projet VSPackage n’a pas besoin de créer <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car le package de la fenêtre IDE qui implémente (par exemple, **l’Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> sur son nom.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>se compose de trois méthodes sont appelées par l’IDE :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contient le nombre d’objets sélectionnés pour être affiché dans le **propriétés** fenêtre.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Retourne le `IDispatch` les objets sélectionnés pour être affiché dans le **propriétés** fenêtre.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>rend possible pour les objets retournés par <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> être sélectionnée par l’utilisateur. Ainsi, le VSPackage pour visuellement mettre à jour la sélection affichée à l’utilisateur dans l’interface utilisateur.  
  
 Le **propriétés** fenêtre extrait des informations à partir de la `IDispatch` objets pour récupérer les propriétés parcourues. Le navigateur de propriétés utilise `IDispatch` pour demander des propriétés de l’objet qu’il prend en charge en interrogeant `ITypeInfo`, qui est obtenu à partir de `IDispatch::GetTypeInfo`. Le navigateur utilise ensuite ces valeurs pour remplir le **propriétés** fenêtre et modifier les valeurs des propriétés individuelles affichées dans la grille. Les informations de propriétés sont conservées au sein de l’objet lui-même.  
  
 Étant donné que les objets retournés prend en charge `IDispatch`, l’appelant peut obtenir des informations telles que nom de l’objet en appelant `IDispatch::Invoke` ou `ITypeInfo::Invoke` avec un identificateur prédéfini de dispatch (DISPID) qui représente les informations souhaitées. Les DISPID déclarées sont négatifs pour vous assurer qu’ils ne sont pas en conflit avec les identificateurs définis par l’utilisateur.  
  
 Le **propriétés** affiche différents types de champs en fonction des attributs de propriétés spécifiques d’un objet sélectionné. Ces champs sont des zones d’édition, des listes déroulantes et des liens vers les boîtes de dialogue d’éditeur personnalisé.  
  
-   Les valeurs contenues dans une liste énumérée sont récupérés par un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> de requête pour `IDispatch`. Les valeurs obtenues à partir d’une liste énumérée peuvent être modifiées dans la grille des propriétés en double-cliquant sur le nom du champ, ou en cliquant sur la valeur et en sélectionnant la nouvelle valeur dans la liste déroulante. Pour les propriétés qui ont prédéfinis des paramètres à partir de listes énumérées, double-cliquez sur le nom de propriété dans la liste des propriétés parcourt les choix disponibles. Pour les propriétés prédéfinies contenant uniquement deux options, telles que true/false, double-cliquez sur le nom de propriété pour basculer entre les choix.  
  
-   Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> est `false`, indiquant que la valeur a été modifiée, la valeur est affichée en gras. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>est utilisé pour déterminer si la valeur peut être réinitialisée à la valeur d’origine. Si, par conséquent, vous pouvez modifier à la valeur par défaut en cliquant sur la valeur et en choisissant **réinitialiser** à partir du menu qui s’affiché. Dans le cas contraire, vous devez modifier la valeur par défaut manuellement. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>vous permet également de localiser et de masquer les noms des propriétés affichées au moment du design, mais n’affecte pas les noms de propriété affichés pendant l’exécution.  
  
-   Affiche la liste des valeurs de propriété à partir de laquelle l’utilisateur peut sélectionner (par exemple, un sélecteur de couleur ou une liste de polices) en cliquant sur le bouton de sélection (...). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fournit ces valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)