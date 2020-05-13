---
title: Fournir un support texte caché dans le service linguistique hérité
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707927"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Comment : Fournir un support texte caché dans un service linguistique hérité
Vous pouvez créer des régions de texte cachées en plus des régions définies. Les régions de texte cachée peuvent être contrôlées par le client ou contrôlées par l’éditeur et sont utilisées pour cacher complètement une région de texte. L’éditeur affiche une région cachée comme des lignes horizontales. Un exemple de ceci est la vue **script seulement** dans l’éditeur HTML.

## <a name="to-implement-a-hidden-text-region"></a>Mettre en œuvre une région de texte caché

1. Appel `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>pour .

     Cela renvoie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>un pointeur à .

2. Appelez, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>en passant dans un pointeur pour un tampon de texte donné. Cela détermine si une session de texte cachée existe déjà pour le tampon.

3. Si l’on existe déjà, alors vous n’avez pas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> besoin de créer un et un pointeur de l’objet existant est retourné. Utilisez ce pointeur pour énumérer et créer des régions de texte cachées. Sinon, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> appelez pour créer une session de texte cachée pour le tampon.

     Un pointeur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> de l’objet est retourné.

    > [!NOTE]
    > Lorsque vous `CreateHiddenTextSession`appelez, vous pouvez spécifier <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>un client de texte caché (c’est-à-dire, ). Le client de texte caché vous informe lorsque le texte caché ou la description est élargi ou effondré par l’utilisateur.

4. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> pour ajouter une ou plusieurs nouvelles régions à la `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>fois, en précisant les informations suivantes dans le ( ) paramètre:

    1. Spécifier `hrtConcealed` une `iType` valeur <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> de dans le membre de la structure pour indiquer que vous créez une région cachée, plutôt que d’une région de contour.

        > [!NOTE]
        > Lorsque des régions cachées sont cachées, l’éditeur affiche automatiquement des lignes autour des régions cachées pour indiquer leur présence.

    2. Précisez si la région est contrôlée par le `dwBehavior` client <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ou contrôlée par le rédacteur en chef dans les membres de la structure. Votre implémentation intelligente peut contenir un mélange de grandes lignes contrôlées par l’éditeur et le client et de régions de texte cachées.
