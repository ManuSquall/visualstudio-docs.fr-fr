---
title: "Boutons de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenêtre Propriétés, boutons"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Boutons de la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En fonction de le langage de développement et le type de produit, boutons sont affichés par défaut dans la barre d'outils de la fenêtre de **Propriétés** .  Dans tous les cas, **Par catégorie**, **classé par ordre alphabétique**, les boutons de **Propriétés**, et de **Pages de propriétés** sont affichés.  En Visual c\# et Visual Basic, le bouton d' **Événements** est également affiché.  Dans certains projets Visual C\+\+, **Messages VC\+\+** et des boutons de **Substitutions de VC** sont affichés.  Les boutons supplémentaires peuvent être affichés pour d'autres types de projets.  Pour plus d'informations sur les boutons de la fenêtre de **Propriétés** , consultez [Fenêtre Propriétés](../../ide/reference/properties-window.md).  
  
## Implémentation des boutons de la fenêtre Propriétés  
 Lorsque vous cliquez sur le bouton de **Par catégorie** , Visual Studio appelle l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> sur l'objet qui a le focus pour trier ses propriétés par catégorie.  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> est implémenté sur l'objet d' `IDispatch` qui est présenté dans la fenêtre de **Propriétés** .  
  
 il y a 11 catégories prédéfinies de propriété, qui ont des valeurs négatives.  Vous pouvez définir des catégories personnalisées, mais nous vous recommandons de leur assigner des valeurs positives pour les distinguer les catégories prédéfinies.  
  
 La méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> retourne la valeur appropriée de catégorie de propriété pour la propriété spécifiée.  La méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> retourne une chaîne contenant le nom de catégorie.  Il vous suffit de fournir la prise en charge de valeurs de catégorie personnalisée car Visual Studio reconnaît les valeurs standard de catégorie de propriété.  
  
 Lorsque vous cliquez sur le bouton de **classé par ordre alphabétique** , les propriétés s'affichent dans l'ordre alphabétique de nom.  Les noms sont récupérés par `IDispatch` en fonction d'un algorithme de tri localisé.  
  
 Lorsque la fenêtre de **Propriétés** est ouverte, le bouton de **Propriétés** est automatiquement comme indiqué sélectionné.  Dans d'autres parties de l'environnement, le bouton s'affiche, et vous pouvez cliquer sur pour afficher la fenêtre de **Propriétés** .  
  
 Le bouton de **Pages de propriétés** est pas disponible si `ISpecifyPropertyPages` n'est pas implémenté pour l'objet sélectionné.  Les pages de propriétés affichent les propriétés de configuration qui sont généralement associées à des solutions et des projets, mais elles peuvent également être associées à des éléments de projet \(par exemple, dans Visual C\+\+\).  
  
> [!NOTE]
>  vous ne pouvez pas ajouter des boutons de barre d'outils à la fenêtre de **Propriétés** à l'aide de code non managé.  pour ajouter un bouton de barre d'outils, vous devez créer un objet managé qui dérive d' <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## Voir aussi  
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)