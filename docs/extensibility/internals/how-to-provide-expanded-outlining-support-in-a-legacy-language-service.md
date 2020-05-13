---
title: Fournir un soutien décrivant dans un service linguistique Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707971"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Comment : Fournir un soutien élargi dans un service linguistique hérité
Il existe deux options pour étendre le soutien à votre langue au-delà de l’appui de la commande **Collapse to Definitions.** Vous pouvez ajouter des régions de contour contrôlées par l’éditeur et ajouter des régions de contour contrôlées par le client.

## <a name="adding-editor-controlled-outline-regions"></a>Ajout de régions de contour contrôlées par l’éditeur
 Utilisez cette approche pour créer une région de contour et ensuite permettre à l’éditeur de gérer si la région est élargie, effondrée, et ainsi de suite. Parmi les deux options pour fournir un soutien, cette option est la moins robuste. Pour cette option, vous créez une nouvelle région <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>de contour sur une durée spécifiée de texte à l’aide de . Une fois cette région créée, son comportement est contrôlé par l’éditeur. Utilisez la procédure suivante pour mettre en œuvre les régions à contours contrôlées par l’éditeur.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Mettre en œuvre une région de contour contrôlée par les éditeurs

1. Appel `QueryService` pour<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Cela renvoie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>un pointeur à .

2. Appelez, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>en passant dans un pointeur pour un tampon de texte donné. Cela renvoie un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pointeur à l’objet pour le tampon.

3. Faites appel <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>un pointeur pour . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>

4. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pour ajouter une ou plusieurs nouvelles régions à la fois.

     Cette méthode vous permet de spécifier la durée du texte à décrire, si les régions de contour existantes sont supprimées ou préservées, et si la région de contour est élargie ou effondrée par défaut.

## <a name="add-client-controlled-outline-regions"></a>Ajouter des régions de contour contrôlées par le client
 Utilisez cette approche pour mettre en œuvre des données contrôlées par le client (ou intelligentes) comme celles utilisées par les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] services linguistiques et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] les services linguistiques. Un service linguistique qui gère ses propres moniteurs de description du contenu tampon de texte afin de détruire les anciennes régions à contours lorsqu’elles deviennent invalides et de créer de nouvelles régions à contours au besoin.

### <a name="to-implement-a-client-controlled-outline-region"></a>Mettre en œuvre une région de contour contrôlée par le client

1. Appel `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>pour . Cela renvoie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>un pointeur à .

2. Appelez, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>en passant dans un pointeur pour un tampon de texte donné. Cela détermine si une session de texte cachée existe déjà pour le tampon.

3. Si une session de texte existe déjà, alors vous n’avez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pas besoin d’en créer une, et un pointeur de l’objet existant est retourné. Utilisez ce pointeur pour énumérer et créer des régions de contour. Sinon, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> appelez pour créer une session de texte cachée pour le tampon. Un pointeur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> de l’objet est retourné.

    > [!NOTE]
    > Lorsque vous <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>appelez, vous pouvez spécifier <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> un client de texte caché (c’est-à-dire un objet). Ce client vous informe lorsqu’un texte caché ou une région de contour est élargi ou effondré par l’utilisateur.

4. Paramètres <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> de structure d’appel) `iType` : Spécifier une valeur de la part du <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> membre de la structure pour indiquer que vous créez une région de contour, plutôt qu’une région cachée. Précisez si la région est contrôlée par le `dwBehavior` client <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ou contrôlée par le rédacteur en chef dans le membre de la structure. Votre mise en œuvre intelligente peut contenir un mélange de régions de contour contrôlées par l’éditeur et le client. Spécifier le texte de la bannière qui s’affiche `pszBanner` lorsque votre <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> région de contour est effondrée, comme «..., dans le membre de la structure. Le texte par défaut de la bannière de l’éditeur pour une région cachée est "...".
