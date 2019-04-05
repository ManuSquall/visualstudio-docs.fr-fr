---
title: Affichent les propriétés de grille | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948561"
---
# <a name="properties-display-grid"></a>Afficher la grille Propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le **propriétés** fenêtre affiche les champs dans une grille. La colonne de gauche contient les noms de propriété ; la colonne de droite contient les valeurs de propriété.  
  
## <a name="working-with-the-grid"></a>Utilisation de la grille  
 La liste de deux colonnes affiche les propriétés indépendantes de la configuration qui peuvent être modifiées au moment du design et leurs paramètres actuels. Notez que toutes les propriétés ne peuvent pas être affichées. Une propriété peut être définie comme étant masquée, par exemple, en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> (méthode). Plus précisément, pour masquer les propriétés qui ont des propriétés enfants voir, [masquage des propriétés qui ont propriétés enfants](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Informations push pour le **propriétés** fenêtre, l’IDE utilise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est appelée par les VSPackages pour chaque fenêtre qui contient les objets sélectionnables avec les propriétés associées à afficher dans le **propriétés** fenêtre. **L’Explorateur de solutions**d’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> appels `GetProperty` à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> dans votre hiérarchie de projet pour acquérir les objets consultable dans la hiérarchie.  
  
 Si votre package Visual Studio ne prend pas en charge <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, l’IDE tente d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> à l’aide de la valeur de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que l’ou les éléments de hiérarchie fournissent.  
  
 Votre projet VSPackage n’a pas besoin pour créer <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car le package de fenêtre fourni par l’IDE qui l’implémente (par exemple, **l’Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se compose de trois méthodes sont appelées par l’IDE :  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contient le nombre d’objets sélectionnés pour être affiché dans le **propriétés** fenêtre.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Retourne le `IDispatch` les objets qui sont sélectionnés pour être affiché dans le **propriétés** fenêtre.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> permet à un des objets retournés par <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> pour être sélectionnées par l’utilisateur. Ainsi, le VSPackage pour visuellement mettre à jour la sélection affichée à l’utilisateur dans l’interface utilisateur.  
  
  Le **propriétés** fenêtre extrait des informations à partir de la `IDispatch` objets pour récupérer les propriétés parcourues. Utilise le navigateur de propriétés `IDispatch` pour demander à l’objet quelles propriétés il prend en charge en interrogeant `ITypeInfo`, qui est obtenu à partir `IDispatch::GetTypeInfo`. Le navigateur utilise ensuite ces valeurs pour remplir le **propriétés** fenêtre et modifier les valeurs des propriétés individuelles affichées dans la grille. Les informations de propriétés sont conservées au sein de l’objet lui-même.  
  
  Étant donné que la prise en charge les objets retournés `IDispatch`, l’appelant peut obtenir des informations telles que nom de l’objet en appelant `IDispatch::Invoke` ou `ITypeInfo::Invoke` avec un identificateur prédéfini de dispatch (DISPID) qui représente les informations souhaitées. DISPID déclarées est négatifs pour vous assurer qu’ils ne sont pas en conflit avec les identificateurs définis par l’utilisateur.  
  
  Le **propriétés** fenêtre affiche différents types de champs en fonction des attributs de propriétés spécifiques d’un objet sélectionné. Ces champs sont des zones d’édition, listes déroulantes et des liens vers des boîtes de dialogue d’éditeur personnalisé.  
  
- Valeurs contenues dans une liste énumérée sont récupérés par un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> des requêtes `IDispatch`. Obtenu à partir d’une liste énumérée de valeurs peuvent être modifiées dans la grille des propriétés en double-cliquant sur le nom du champ, ou en cliquant sur la valeur et en sélectionnant la nouvelle valeur dans la liste déroulante. Pour les propriétés qui ont prédéfinis des paramètres à partir de listes énumérées, double-cliquez sur le nom de propriété dans la liste des propriétés parcourt les choix disponibles. Pour les propriétés prédéfinies contenant uniquement deux options, telles que true/false, double-cliquez sur le nom de propriété pour basculer entre les choix.  
  
- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> est `false`, indiquant que la valeur a été modifiée, la valeur est affichée en gras. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> est utilisé pour déterminer si la valeur peut être réinitialisée à la valeur d’origine. Si, par conséquent, vous pouvez modifier à la valeur par défaut en double-cliquant sur la valeur et en choisissant **réinitialiser** à partir du menu qui s’affiché. Sinon, vous devez modifier la valeur par défaut manuellement. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> vous permet également de localiser et de masquer les noms des propriétés qui s’affichées au moment du design, mais n’affecte pas les noms de propriété affichés pendant l’exécution.  
  
- En cliquant sur le bouton de sélection (...) affiche une liste de valeurs de propriété à partir de laquelle l’utilisateur peut sélectionner (par exemple, un sélecteur de couleurs ou la liste de polices). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fournit ces valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)
