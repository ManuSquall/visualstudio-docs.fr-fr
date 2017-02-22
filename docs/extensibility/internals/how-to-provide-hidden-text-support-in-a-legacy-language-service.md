---
title: "Comment&#160;: fournir la prise en charge du texte masqu&#233; dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "texte, masqué prenant en charge"
  - "éditeurs (Visual Studio SDK), masqués texte"
  - "services de langage, l’implémentation des zones de texte masqué"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: fournir la prise en charge du texte masqu&#233; dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez créer des zones de texte masqué en plus de les régions en mode Plan.  Les zones de texte masqué peuvent être client\-contrôlées ou contrôlées par l'éditeur et sont utilisées pour masquer une zone de texte complètement.  l'éditeur affiche une zone masquée comme lignes horizontales.  Un exemple de cette opération est en mode script uniquement dans l'éditeur HTML.  
  
## Procédure  
  
#### pour implémenter une zone de texte masqué  
  
1.  appel `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur d'une mémoire tampon de texte donnée.  Cela détermine si une session de texte masqué existe déjà pour la mémoire tampon.  
  
3.  Le cas échéant, vous n'avez pas besoin de créer un et un pointeur vers l'objet existant d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  Utilisez ce pointeur pour énumérer et créer des zones de texte masqué.  Sinon, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> d'appel pour créer une session de texte masqué pour la mémoire tampon.  
  
     Un pointeur vers l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez `CreateHiddenTextSession`, vous pouvez spécifier un client de texte masqué \(autrement dit, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\).  Le client de texte masqué vous avertit lorsque le texte masqué ou le mode Plan est développé ou réduit par l'utilisateur.  
  
4.  appelez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> pour ajouter une ou plusieurs nouvelles régions en mode Plan à la fois, en spécifiant les informations suivantes dans le paramètre d' `reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\) :  
  
    1.  spécifiez une valeur d' `hrtConcealed` dans le membre d' `iType` de la structure d' <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> pour indiquer que vous créez une zone masquée, plutôt qu'une région en mode Plan.  
  
        > [!NOTE]
        >  Une fois cachées les régions sont masquées, les affiche les lignes d'éditeur automatiquement autour de les zones masquées pour indiquer leur présence.  
  
    2.  Spécifiez si la région est client\-contrôlée ou contrôlée par l'éditeur dans les membres d' `dwBehavior` de la structure d' <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> .  Votre implémentation intelligente de mode Plan peut contenir une combinaison des régions client\-contrôlées d'éditeur et d'ensemble et de texte masqué.