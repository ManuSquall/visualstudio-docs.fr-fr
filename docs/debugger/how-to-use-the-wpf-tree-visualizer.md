---
title: "Comment&#160;: utiliser le visualiseur de l&#39;arborescence WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogage, WPF"
  - "WPF, débogage"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser le visualiseur de l&#39;arborescence WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le visualiseur de l'arborescence WPF pour explorer l'arborescence d'éléments visuels d'un objet WPF et visualiser les propriétés de dépendance WPF pour les objets contenus dans cette arborescence.  Pour plus d'informations sur les arborescences d'éléments visuels, consultez [Arborescences dans WPF](../Topic/Trees%20in%20WPF.md).  Pour plus d'informations sur les propriétés de dépendance, consultez [Vue d'ensemble des propriétés de dépendance](../Topic/Dependency%20Properties%20Overview.md).  
  
 Lorsque vous ouvrez le visualiseur de l'arborescence WPF, deux volets s'affichent : le volet **Arborescence d'éléments visuels** à gauche et le volet **Propriétés de***Name***:***Type* à droite.  Sélectionnez un objet dans le volet **Arborescence d'éléments visuels** ; le volet **Propriétés de** *Name***:***Type* est alors automatiquement mis à jour afin d'afficher les propriétés pour cet objet.  
  
### Pour ouvrir le visualiseur de l'arborescence WPF  
  
1.  Dans la fenêtre **Espion**, **Automatique** ou **Variables locales** d'un DataTip, cliquez sur la flèche à côté de l'icône de loupe située en regard d'un nom d'objet WPF.  
  
     Une liste de visualiseurs s'affiche.  
  
2.  Cliquez sur **Visualiseur de l'arborescence WPF**.  
  
### Pour effectuer une recherche sur l'arborescence d'éléments visuels  
  
-   Dans le volet **Arborescence d'éléments visuels**, tapez la chaîne que vous souhaitez rechercher dans la zone **Recherche**.  
  
     Le visualiseur de l'arborescence WPF recherche immédiatement le premier objet de l'arborescence d'éléments visuels qui correspond à la chaîne que vous avez tapée.  Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Cliquez sur **Suivant** pour accéder à la correspondance suivante de l'arborescence d'éléments visuels.  
  
    -   Cliquez sur **Préc.** pour revenir à la correspondance précédente.  
  
    -   Cliquez sur **Effacer** pour effacer les critères de recherche.  
  
### Pour effectuer une recherche sur la liste des propriétés  
  
-   Dans le volet **Propriétés de** *Name***:***Type*, tapez la chaîne à rechercher dans la zone **Filtre**.  
  
     Le visualiseur de l'arborescence WPF recherche immédiatement les propriétés qui correspondent à la chaîne que vous avez tapée. À présent, la liste n'affiche que les propriétés correspondant à la chaîne que vous avez tapée.  Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Cliquez sur **Effacer** pour effacer les critères de recherche.  
  
### Pour fermer le visualiseur  
  
-   Cliquez sur l'icône **Fermer** située dans l'angle supérieur droit de la boîte de dialogue.  
  
## Voir aussi  
 [Comment : utiliser un visualiseur](../Topic/How%20to:%20Use%20a%20Visualizer.md)   
 [Visualiseurs](../debugger/create-custom-visualizers-of-data.md)   
 [Arborescences dans WPF](../Topic/Trees%20in%20WPF.md)   
 [Vue d'ensemble des propriétés de dépendance](../Topic/Dependency%20Properties%20Overview.md)