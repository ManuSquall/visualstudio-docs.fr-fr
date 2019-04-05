---
title: 'Procédure : Fournir la prise en charge de texte masqué dans un Service de langage hérité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a74998e6cb9b236818f20ec3c597f9a3b9bd7dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950920"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procédure : Fournir la prise en charge de texte masqué dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
