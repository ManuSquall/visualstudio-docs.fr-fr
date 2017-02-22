---
title: "Strat&#233;gie de mod&#232;le et de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenêtre Propriétés, la stratégie des modèles"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Strat&#233;gie de mod&#232;le et de la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsqu'un projet est contenu à l'intérieur d'un projet de modèle pour l'entreprise, ce projet de modèle pour l'entreprise peut appliquer la stratégie.  La stratégie de modèle est un système de contrainte qui peut être utilisé pour définir des valeurs par défaut pour les propriétés, masquez des propriétés, ajoutez des propriétés, et ainsi de suite.  
  
 À l'aide de la stratégie de modèle contrôler l'affichage des informations dans la fenêtre de **Propriétés** est différent d'implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gère les propriétés de l'objet au niveau de composant, alors que la stratégie de modèle peut être utilisée pour limiter les propriétés de l'objet à la solution ou au niveau de le projet.  en d'autres termes  
  
-   Implémentez les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> pour déterminer ce qui est affiché dans la fenêtre de **Propriétés** pour les objets spécifiques  
  
-   Utilisez la stratégie de modèle à la solution et du projet pour comprendre ce qui est affiché dans la fenêtre de **Propriétés** pour les objets précédemment spécifiés  
  
 À l'aide de la stratégie de modèle il peut être utile de contraindre sélectivement leurs propriétés spécifiques dans la fenêtre de **Propriétés** lorsqu'un élément de projet d'un type spécifié est sélectionné dans **Explorateur de solutions** à tous les membres de l'équipe de développement qui travaillent sur un projet.  Par exemple, l'utilisation de la stratégie de modèle, vous pouvez installer toutes les informations de chaîne de connexion dans une base de données pour vos développeurs et rendre la chaîne de connexion en lecture seule.  De cette façon, vous pouvez fournir un moyen simple de s'assurer que chaque développeur utilise le chemin d'accès approprié pour l'accès aux données.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Étendre les propriétés](../../extensibility/internals/extending-properties.md)