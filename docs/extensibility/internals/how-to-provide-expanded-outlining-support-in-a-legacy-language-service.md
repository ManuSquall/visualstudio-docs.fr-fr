---
title: Fournir la prise en charge dans un Service de langage du mode plan | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge en mode plan étendue dans un Service de langage hérité
Il existe deux options pour étendre la prise en charge en mode plan pour votre langage de prendre en charge la **réduire aux définitions** commande. Vous pouvez ajouter des régions en mode plan de contrôlés par l’éditeur et ajouter des régions en mode plan de contrôlé par le client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Ajout de régions en mode plan de contrôlés par l’éditeur  
 Utilisez cette approche pour créer une région en mode plan, puis laissez l’éditeur à gérer si la région est développée, réduit et ainsi de suite. Les deux options pour la prise en charge en mode plan, cette option est la moins fiable. Pour cette option, vous créez une nouvelle zone de plan sur une plage spécifiée de texte à l’aide <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Une fois cette zone est créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour implémenter les régions en mode plan de contrôlés par l’éditeur.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Pour implémenter une région en mode plan de contrôlés par l’éditeur  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur de mémoire tampon de texte donné. Cela retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet pour la mémoire tampon.  
  
3.  Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pour un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pour ajouter une ou plusieurs nouvelles montrer les régions à la fois.  
  
     Cette méthode vous permet de spécifier l’étendue de texte à un plan, si les régions en mode plan existantes sont supprimées ou conservées, et si la région en mode plan est développée ou réduite par défaut.  
  
## <a name="adding-client-controlled-outline-regions"></a>Ajout de régions en mode plan de contrôlé par le Client  
 Utilisez cette approche pour implémenter contrôlé par le client (ou active) en mode plan similaire qui utilisé par le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] les services de langage. Un service de langage qui gère son propre mode plan analyse le contenu de mémoire tampon de texte pour pouvoir détruire une ancienne régions en mode plan lorsqu’ils devient non valide et pour créer de nouvelles régions en mode plan en fonction des besoins.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Pour implémenter une région en mode plan de contrôlé par le client  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur de mémoire tampon de texte donné. Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  Si une texte session existe déjà, vous n’avez pas besoin créer un et un pointeur à l’objet existant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné. Utilisez ce pointeur pour énumérer et créer des régions en mode plan. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon. Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, vous pouvez spécifier un client de texte masqué (autrement dit, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objet). Ce client vous avertit lorsqu’un texte masqué ou la région en mode plan est développée ou réduite par l’utilisateur.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) paramètre : spécifiez la valeur <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une région en mode plan, plutôt qu’une zone masquée. Spécifiez si la région est contrôlé par le client ou dépendant de l’éditeur dans le `dwBehavior` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de mode plan intelligente peut contenir une combinaison de régions en mode plan contrôlé par l’éditeur et par le client. Spécifiez le texte de bannière s’affiche lorsque votre région en mode plan est réduite, tels que «... », dans le `pszBanner` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Texte de bannière par défaut de l’éditeur pour une zone masquée est «... ».