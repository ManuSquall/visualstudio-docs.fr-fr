---
title: Fournir une prise en charge du mode plan dans un service de langage | Microsoft Docs
description: Apprenez à fournir une prise en charge développée du mode plan dans un service de langage hérité en ajoutant des régions de plan contrôlées par l’éditeur et des régions de plan contrôlées par le client.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11d04af2afac04d4ec9ab197c3d3f7b5a15ad28c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078784"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge développée du mode plan dans un service de langage hérité
Il existe deux options pour étendre la prise en charge du mode plan à votre langage au-delà de la prise en charge de la commande **réduire aux définitions** . Vous pouvez ajouter des régions de plan contrôlées par l’éditeur et ajouter des zones de plan contrôlées par le client.

## <a name="adding-editor-controlled-outline-regions"></a>Ajout d’une région de plan contrôlée par l’éditeur
 Utilisez cette approche pour créer une zone de plan, puis autorisez l’éditeur à gérer si la région est développée, réduite et ainsi de suite. Parmi les deux options disponibles pour la prise en charge du mode plan, cette option est la moins fiable. Pour cette option, vous créez une nouvelle région en mode plan sur une étendue de texte spécifiée à l’aide de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Une fois cette région créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour implémenter des régions de plan contrôlées par l’éditeur.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Pour implémenter une région en mode plan contrôlée par l’éditeur

1. Appeler `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Appelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , en passant un pointeur pour une mémoire tampon de texte donnée. Cela retourne un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet pour la mémoire tampon.

3. Appelez <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> on <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pour un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pour ajouter une ou plusieurs nouvelles régions en mode plan à la fois.

     Cette méthode vous permet de spécifier l’étendue de texte à présenter, si les régions de plan existantes sont supprimées ou conservées, et si la zone de plan est développée ou réduite par défaut.

## <a name="add-client-controlled-outline-regions"></a>Ajouter des régions de plan contrôlées par le client
 Utilisez cette approche pour implémenter un mode de mise en plan contrôlé par le client (ou intelligent) comme celui utilisé par les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] services de langage et. Un service de langage qui gère son propre mode plan surveille le contenu de la mémoire tampon de texte afin de détruire les anciennes zones de plan lorsqu’elles deviennent non valides et de créer de nouvelles régions en mode plan en fonction des besoins.

### <a name="to-implement-a-client-controlled-outline-region"></a>Pour implémenter une région en mode plan contrôlé par le client

1. Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Appelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , en passant un pointeur pour une mémoire tampon de texte donnée. Cela détermine si une session de texte masqué existe déjà pour la mémoire tampon.

3. Si une session de texte existe déjà, vous n’avez pas besoin d’en créer une, et un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet existant est retourné. Utilisez ce pointeur pour énumérer et créer des régions de plan. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon. Un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet est retourné.

    > [!NOTE]
    > Lorsque vous appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , vous pouvez spécifier un client de texte masqué (autrement dit, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objet). Ce client vous avertit lorsqu’une zone de texte ou de plan masquée est développée ou réduite par l’utilisateur.

4. Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) : spécifiez une valeur <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une région en mode plan, plutôt qu’une zone masquée. Spécifiez si la région est contrôlée par le client ou contrôlée par l’éditeur dans le `dwBehavior` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de la mise en plan intelligente peut contenir une combinaison de zones de plan de l’éditeur et contrôlées par le client. Spécifiez le texte de la bannière qui s’affiche lorsque votre zone de plan est réduite, par exemple « ... », dans le `pszBanner` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Le texte de bannière par défaut de l’éditeur pour une zone masquée est « ... ».
