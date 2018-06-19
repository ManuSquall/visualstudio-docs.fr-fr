---
title: 'Comment : prendre en charge le texte masqué dans un Service de langage hérité | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54e508c6bcbb9cb79459e0b61a97f51350c00708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132640"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Comment : prendre en charge le texte masqué dans un Service de langage hérité
Vous pouvez créer des zones de texte masqué en plus des régions en mode plan. Zones de texte masqué peuvent être contrôlé par le client ou contrôlés par l’éditeur et sont utilisés pour masquer une zone de texte complètement. L’éditeur affiche une zone masquée comme des lignes horizontales. Ceci est le mode Script uniquement dans l’éditeur HTML.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-implement-a-hidden-text-region"></a>Pour implémenter une zone de texte masqué  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur de mémoire tampon de texte donné. Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  S’il en existe déjà, puis que vous n’avez pas besoin de créer un et un pointeur à l’objet de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné. Utilisez ce pointeur pour énumérer et créer des zones de texte masqué. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon.  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez `CreateHiddenTextSession`, vous pouvez spécifier un client de texte masqué (autrement dit, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Le client de texte masqué vous avertit lorsque le texte masqué ou le mode plan est développé ou réduit par l’utilisateur.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> d’ajouter un ou plusieurs nouvelles montrer les régions à la fois, en spécifiant les informations suivantes dans le `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) paramètre :  
  
    1.  Spécifiez la valeur `hrtConcealed` dans les `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une zone masquée, plutôt que d’une région en mode plan.  
  
        > [!NOTE]
        >  Lorsque les régions masquées sont masquées, l’éditeur affiche automatiquement les lignes dans les zones masquées pour indiquer leur présence.  
  
    2.  Spécifiez si la région est contrôlé par le client ou dépendant de l’éditeur dans le `dwBehavior` membres de le <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de mode plan intelligente peut contenir une combinaison de plan de l’éditeur - et contrôlé par le client et les zones de texte masqué.