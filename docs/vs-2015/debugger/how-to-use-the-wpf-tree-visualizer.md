---
title: 'Comment : utiliser le visualiseur de l’arborescence WPF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8eb0bae29db30c5ba3a305707d886b01b5c34d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188330"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Comment : utiliser le visualiseur de l’arborescence WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser le visualiseur de l’arborescence WPF pour explorer l’arborescence d’éléments visuels d’un objet WPF et visualiser les propriétés de dépendance WPF pour les objets contenus dans cette arborescence. Pour plus d’informations sur les arborescences d’éléments visuels, consultez [arborescences dans WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Lorsque vous ouvrez le visualiseur de l’arborescence WPF, vous verrez deux volets : le **arborescence d’éléments visuels** sur la gauche et le **propriétés de** _nom_**:**  _Type_ volet de droite. Sélectionnez n’importe quel objet dans le **arborescence d’éléments visuels** volet et le **propriétés de** _nom_**:**_Type_ volet est mise à jour automatiquement pour afficher les propriétés pour cet objet.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Pour ouvrir le visualiseur de l’arborescence WPF  
  
1.  Dans un DataTip, **espion** fenêtre, **automatique** fenêtre, ou **variables locales** située en regard d’un nom d’objet WPF, cliquez sur la flèche en regard de l’icône de loupe.  
  
     Une liste de visualiseurs s'affiche.  
  
2.  Cliquez sur **visualiseur de l’arborescence WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Pour effectuer une recherche sur l’arborescence d’éléments visuels  
  
-   Dans le **arborescence d’éléments visuels** volet, tapez la chaîne que vous souhaitez rechercher dans le **recherche** boîte.  
  
     Le visualiseur de l’arborescence WPF recherche immédiatement le premier objet de l’arborescence d’éléments visuels qui correspond à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Pour passer à la correspondance suivante de l’arborescence visuelle, cliquez sur **suivant**.  
  
    -   Pour revenir à la correspondance précédente, cliquez sur **Prev**.  
  
    -   Pour effacer les critères de recherche, cliquez sur **effacer**.  
  
### <a name="to-search-the-properties-list"></a>Pour effectuer une recherche sur la liste des propriétés  
  
-   Dans le **propriétés de** _nom_**:**_Type_ volet, tapez la chaîne à rechercher dans le **filtrer**boîte.  
  
     Le visualiseur de l’arborescence WPF recherche immédiatement les propriétés qui correspondent à la chaîne que vous avez tapée. À présent, la liste n’affiche que les propriétés correspondant à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Pour effacer les critères de recherche, cliquez sur **effacer**.  
  
### <a name="to-close-the-visualizer"></a>Pour fermer le visualiseur  
  
-   Cliquez sur le **fermer** icône dans le coin supérieur droit de la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser un visualiseur](../misc/how-to-use-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Arborescences dans WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Vue d’ensemble des propriétés de dépendance](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)



