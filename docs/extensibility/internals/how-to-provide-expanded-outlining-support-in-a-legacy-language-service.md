---
title: Fournir la prise en charge dans un Service de langage du mode plan | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge étendue de plan dans un Service de langage hérité
Il existe deux options pour étendre la prise en charge en mode plan pour votre langage de prendre en charge les **réduire aux définitions** commande. Vous pouvez ajouter des régions de contour contrôlés par l’éditeur et ajouter des zones de contour contrôlé par le client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Ajout de régions de contour contrôlés par l’éditeur  
 Utilisez cette approche pour créer une région en mode plan et permettre ensuite à l’éditeur à gérer si la région est développée, réduit et ainsi de suite. Les deux options pour la prise en charge en mode plan, cette option est moins fiable. Pour cette option, vous créez une nouvelle région de plan sur une plage spécifiée de texte à l’aide de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Une fois que cette région est créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour implémenter des régions de contour contrôlés par l’éditeur.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Pour implémenter une zone de contour contrôlés par l’éditeur  
  
1.  Appelez `QueryService` pour<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Cette opération retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objet de la mémoire tampon.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Appel <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>pour ajouter une ou plusieurs nouvelles montrer les régions à la fois.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Cette méthode vous permet de spécifier l’étendue de texte à un plan, si les régions en mode plan existant sont supprimées ou conservées, et si la région en mode plan est développée ou réduite par défaut.  
  
## <a name="adding-client-controlled-outline-regions"></a>Ajout de régions de plan contrôlé par le Client  
 Utilisez cette approche pour implémenter contrôlé par le client (ou recommandé) mise en relief du même type utilisé par le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] les services de langage. Un service de langage qui gère son propre plan analyse le contenu du tampon de texte afin de détruire les régions en mode plan ancien lorsqu’ils devient non valide et pour créer de nouvelles régions en mode plan en fonction des besoins.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Pour implémenter une région plan contrôlé par le client  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  Si une texte session existe déjà, alors que vous n’avez pas besoin créer un et un pointeur à l’objet de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>est retourné.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Utilisez ce pointeur pour énumérer et créer des régions en mode plan. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>pour créer une session de texte masqué pour le tampon.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>est retourné.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Lorsque vous appelez la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, vous pouvez spécifier un client texte masqué (autrement dit, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>objet).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Ce client vous informe lorsqu’un texte masqué ou la région en mode plan est développée ou réduite par l’utilisateur.  
  
4.  Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>structure) paramètre : spécifiez la valeur <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>dans les `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>structure pour indiquer que vous créez une région en mode plan, plutôt que d’une zone masquée.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Spécifiez si la région est contrôlé par le client ou dépendant de l’éditeur dans le `dwBehavior` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>structure.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Votre implémentation de plan active peut contenir une combinaison des régions en mode plan contrôlé par l’éditeur et par le client. Spécifiez le texte de bannière s’affiche lorsque votre région en mode plan est réduite, tels que «... », dans le `pszBanner` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>structure.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Texte de bannière par défaut de l’éditeur pour une zone masquée est «... ».
