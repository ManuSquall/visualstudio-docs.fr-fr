---
title: 'Comment : fournir une prise en charge étendue de mode plan dans un Service de langage hérité | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6371339da12d88832e84d5086ed2d8a83226a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239530"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge étendue de mode plan dans un Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe deux options pour étendre la prise en charge en mode plan pour votre langage au-delà de la prise en charge la **réduire aux définitions** commande. Vous pouvez ajouter des régions en mode de plan contrôlés par l’éditeur et ajouter des régions en mode plan de contrôlé par le client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Ajout de régions de contour contrôlés par l’éditeur  
 Utilisez cette approche pour créer une région en mode plan, puis autoriser l’éditeur de gérer une valeur indiquant si la région est développée, réduit et ainsi de suite. Des deux options pour la prise en charge en mode plan, cette option est moins fiable. Pour cette option, vous créez une nouvelle région en mode plan sur une étendue spécifiée de texte à l’aide <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Une fois que cette région est créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour implémenter des régions en mode de plan contrôlés par l’éditeur.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Pour implémenter une région en mode de plan contrôlés par l’éditeur  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée. Cela retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet pour la mémoire tampon.  
  
3.  Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pour un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pour ajouter un ou plusieurs nouvelles hiérarchiques régions à la fois.  
  
     Cette méthode vous permet de spécifier l’étendue de texte pour le plan, si les régions en mode plan existantes sont supprimées ou conservées, et si la région en mode plan est développée ou réduite par défaut.  
  
## <a name="adding-client-controlled-outline-regions"></a>Ajout de régions de contour contrôlé par le Client  
 Utilisez cette approche pour implémenter contrôlé par le client (ou recommandé) en mode plan, tels qu’utilisé par le [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] services de langage. Un service de langage qui gère sa propre mise en relief analyse le contenu de mémoire tampon de texte afin de détruire l’ancien régions en mode plan lorsqu’ils devient non valide et pour créer de nouvelles régions en mode plan en fonction des besoins.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Pour implémenter une région en mode plan de contrôlé par le client  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée. Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  Si une texte session existe déjà, vous n’avez pas besoin créer un et un pointeur à l’objet de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné. Utilisez ce pointeur pour énumérer et créer des régions en mode plan. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon. Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, vous pouvez spécifier un client de texte masqué (autrement dit, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objet). Ce client vous avertit quand un texte masqué ou région en mode plan est développée ou réduite par l’utilisateur.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) paramètre : spécifiez la valeur <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une région en mode plan, plutôt que d’une zone masquée. Spécifiez si la région est contrôlé par le client ou contrôlés par l’éditeur dans le `dwBehavior` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de mode plan intelligente peut contenir un mélange de régions en mode plan contrôlé par l’éditeur et par le client. Spécifiez le texte de bannière s’affiche lorsque votre région en mode plan est réduite, tels que «... », dans le `pszBanner` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Texte de bannière par défaut de l’éditeur pour une zone masquée est «... ».

