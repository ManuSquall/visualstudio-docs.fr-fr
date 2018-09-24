---
title: Indiquez le mode plan de prise en charge dans un Service de langage | Microsoft Docs
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
ms.openlocfilehash: 31ae8a6aeba28fbe90e68305f2b48021b4327c26
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511387"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge étendue de mode plan dans un service de langage hérité
Il existe deux options pour étendre la prise en charge en mode plan pour votre langage au-delà de la prise en charge la **réduire aux définitions** commande. Vous pouvez ajouter des régions en mode de plan contrôlés par l’éditeur et ajouter des régions en mode plan de contrôlé par le client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Ajout de régions de contour contrôlés par l’éditeur  
 Utilisez cette approche pour créer une région en mode plan, puis autoriser l’éditeur de gérer une valeur indiquant si la région est développée, réduit et ainsi de suite. Des deux options pour la prise en charge en mode plan, cette option est moins fiable. Pour cette option, vous créez une nouvelle région en mode plan sur une étendue spécifiée de texte à l’aide <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Une fois que cette région est créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour implémenter des régions en mode de plan contrôlés par l’éditeur.  
  
### <a name="to-implement-an-editor-controlled-outline-region"></a>Pour implémenter une région en mode de plan contrôlés par l’éditeur  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée. Cela retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet pour la mémoire tampon.  
  
3.  Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pour un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pour ajouter un ou plusieurs nouvelles hiérarchiques régions à la fois.  
  
     Cette méthode vous permet de spécifier l’étendue de texte pour le plan, si les régions en mode plan existantes sont supprimées ou conservées, et si la région en mode plan est développée ou réduite par défaut.  
  
## <a name="add-client-controlled-outline-regions"></a>Ajouter des régions en mode plan de contrôlé par le client  
 Utilisez cette approche pour implémenter contrôlé par le client (ou recommandé) en mode plan, tels qu’utilisé par le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] services de langage. Un service de langage qui gère sa propre mise en relief analyse le contenu de mémoire tampon de texte afin de détruire l’ancien régions en mode plan lorsqu’elles deviennent non valides et de créer de nouvelles régions en mode plan en fonction des besoins.  
  
### <a name="to-implement-a-client-controlled-outline-region"></a>Pour implémenter une région en mode plan de contrôlé par le client  
  
1.  Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, en passant un pointeur pour une mémoire tampon de texte donnée. Ce paramètre détermine si une texte masqué session existe déjà pour la mémoire tampon.  
  
3.  Si une texte session existe déjà, vous n’avez pas besoin créer un et un pointeur à l’objet de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné. Utilisez ce pointeur pour énumérer et créer des régions en mode plan. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon. Un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> est retourné.  
  
    > [!NOTE]
    >  Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, vous pouvez spécifier un client de texte masqué (autrement dit, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objet). Ce client vous avertit quand un texte masqué ou région en mode plan est développée ou réduite par l’utilisateur.  
  
4.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) paramètre : spécifiez la valeur <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une région en mode plan, plutôt que d’une zone masquée. Spécifiez si la région est contrôlé par le client ou contrôlés par l’éditeur dans le `dwBehavior` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de mode plan intelligente peut contenir un mélange de régions en mode plan contrôlé par l’éditeur et par le client. Spécifiez le texte de bannière s’affiche lorsque votre région en mode plan est réduite, tels que «... », dans le `pszBanner` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Texte de bannière par défaut de l’éditeur pour une zone masquée est «... ».