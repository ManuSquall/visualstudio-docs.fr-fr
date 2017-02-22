---
title: "Afficher la grille Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grille des propriétés (Visual Studio SDK),"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Afficher la grille Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche des champs de fenêtre de **Propriétés** dans une grille.  La colonne de gauche contient les noms de propriété ; la colonne de droite contient les valeurs de propriété.  
  
## Utiliser la grille  
 La liste à deux colonnes affiche les propriétés pas liées qui peuvent être modifiées au moment de le design et à leurs paramètres actuels.  Notez que toutes les propriétés peuvent ne pas s'afficher.  une propriété peut être définie comme masquée, par exemple, en implémentant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> .  Spécifiquement, pour masquer les propriétés qui font consulter les propriétés enfants, [Masquage des propriétés qui ont des propriétés enfants](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Pour effectuer un push des informations dans la fenêtre de **Propriétés** , l'IDE utilise <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est appelé par les VSPackages pour chaque fenêtre qui contient les objets sélectionnables avec des propriétés connexes à afficher dans la fenêtre de **Propriétés** .  L'implémentation De l'Explorateur de Solutions d' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> appelle `GetProperty` à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> de la hiérarchie de projet pour obtenir les objets browseable dans la hiérarchie.  
  
 Si votre package VS ne prend pas en charge <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, les tentatives de l'IDE d'utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> à l'aide de la valeur de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que le ou les éléments de la hiérarchie fournissent.  
  
 Votre projet VSPackage n'a pas besoin de créer <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> parce que le package IDE\-fourni de fenêtre qui l'implémente \(par exemple, **Explorateur de solutions**\) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> de sa part.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se compose de trois méthodes appelées par l'IDE :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contient le nombre d'objets sélectionnés pour être affiché dans la fenêtre de **Propriétés** .  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> retourne des objets d' `IDispatch` sélectionnés pour être affichés dans la fenêtre de **Propriétés** .  
  
-   l'<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> le rend possible pour l'un des objets retournés par <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> à sélectionner par l'utilisateur.  Cela permet au package VS pour mettre à jour visuellement la sélection affichée à l'utilisateur dans l'interface utilisateur.  
  
 La fenêtre de **Propriétés** extrait les informations des objets d' `IDispatch` pour récupérer les propriétés qui sont parcourues.  Le navigateur de propriétés utilise `IDispatch` demander à l'objet les propriétés il prend en charge en interrogeant `ITypeInfo`, qui est obtenu à partir de `IDispatch::GetTypeInfo`.  Le navigateur utilise ensuite ces valeurs pour remplir la fenêtre de **Propriétés** et de modifier les valeurs de propriétés affichées dans la grille.  Les informations de propriétés sont conservées dans l'objet lui\-même.  
  
 Étant donné que les objets retournés prennent en charge `IDispatch`, l'appelant peut obtenir des informations telles que le nom de l'objet en appelant `IDispatch::Invoke` ou `ITypeInfo::Invoke` avec un identificateur de dispatch prédéfinie \(DISPID\) qui représente les informations souhaitées.  Les dispid déclaré sont négatif pour les vous assurer qu'elles ne sont pas en conflit avec les identificateurs définis par l'utilisateur.  
  
 la fenêtre de **Propriétés** affiche différents types de champs selon les attributs des propriétés spécifiques d'un objet sélectionné.  Ces champs incluent des zones d'édition, les listes déroulantes, et des liens aux boîtes de dialogue personnalisées d'éditeur.  
  
-   Les valeurs contenues dans une liste énumérée sont récupérées par une requête d' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> à `IDispatch`.  Les valeurs obtenues à partir d'une liste énumérée peuvent être modifiées dans la grille des propriétés en double\-cliquant sur le nom du champ, ou en cliquant sur la valeur et en sélectionnant la nouvelle valeur dans la liste déroulante.  Pour les propriétés qui ont intégré des paramètres des listes énumérées, double\-cliquez sur le nom de la propriété dans les cycles de liste des propriétés via les choix disponibles.  Pour les propriétés intégrées que deux choix, tels que vrai\/faux, double\-cliquez sur le nom de la propriété pour basculer entre des tableaux.  
  
-   Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> est `false`, indiquant que la valeur a été modifiée, la valeur est affichée en gras.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> est utilisé pour déterminer si la valeur peut être réinitialisée à la valeur d'origine.  Dans ce cas, vous pouvez revenir à un la valeur par défaut en cliquant avec le bouton droit sur la valeur et en choisissant **Reset** du menu affiche.  Sinon, vous devez modifier la valeur dans la valeur par défaut manuellement.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> vous permet également de localiser et masquer les noms des propriétés affichées au moment de le design, mais n'affecte pas les noms de propriété affichés au moment de l'exécution.  
  
-   Cliquez sur le bouton de sélection \(...\) affiche une liste de valeurs de propriété parmi lesquelles l'utilisateur peut sélectionner \(comme une liste de sélecteur de couleurs et de police\).  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fournit ces valeurs.  
  
## Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)