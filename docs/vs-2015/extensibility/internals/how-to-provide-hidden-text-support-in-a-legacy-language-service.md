---
title: 'Comment : fournir la prise en charge de texte masqué dans un Service de langage hérité | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b689bdfff45f12bc85f79b3cba8581e728c89728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501476"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Comment : fournir la prise en charge de texte masqué dans un Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : fournir masqué texte prise en charge dans un Service de langage hérité](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service).  
  
Vous pouvez créer des zones de texte masqué en plus de régions en mode plan. Zones de texte masqué peuvent être contrôlé par le client ou contrôlée par l’éditeur et sont utilisés pour masquer une zone de texte complètement. L’éditeur affiche une zone masquée en tant que lignes horizontales. Un exemple de ceci est le mode Script uniquement dans l’éditeur HTML.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-implement-a-hidden-text-region"></a>Pour implémenter une zone de texte masqué  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée. Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  Si il en existe déjà, vous n’avez pas besoin créer un et un pointeur à l’objet de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné. Utilisez ce pointeur pour énumérer et créer des zones de texte masqué. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon.  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez `CreateHiddenTextSession`, vous pouvez spécifier un client de texte masqué (autrement dit, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Le client de texte masqué vous avertit lorsque le texte masqué ou le mode plan est développé ou réduit par l’utilisateur.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> d’ajouter un ou plusieurs nouvelles décrivent régions à la fois, en spécifiant les informations suivantes dans le `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) paramètre :  
  
    1.  Spécifiez la valeur `hrtConcealed` dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une zone masquée, plutôt que d’une région en mode plan.  
  
        > [!NOTE]
        >  Lorsque les régions masquées sont masquées, l’éditeur affiche automatiquement les lignes dans les zones masquées pour indiquer leur présence.  
  
    2.  Spécifiez si la région est contrôlé par le client ou contrôlés par l’éditeur dans le `dwBehavior` membres de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de mode plan intelligente peut contenir un mélange de contour contrôlé par l’éditeur et par le client et les zones de texte masqué.

