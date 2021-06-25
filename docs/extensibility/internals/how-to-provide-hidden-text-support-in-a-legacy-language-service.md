---
title: Fournir la prise en charge du texte masqué dans le service de langage hérité
description: Apprenez à fournir une prise en charge du texte masqué dans un service de langage hérité en ajoutant des zones de texte masquées, contrôlées par l’éditeur ou contrôlées par le client.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31c62f50cfff8662c543d24dceabdb429a9b9b05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901784"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Comment : fournir une prise en charge du texte masqué dans un service de langage hérité
Vous pouvez créer des zones de texte masqué en plus des régions de plan. Les zones de texte masquées peuvent être contrôlées par le client ou par l’éditeur et utilisées pour masquer complètement une région de texte. L’éditeur affiche une zone masquée sous forme de lignes horizontales. Par exemple, l’affichage **script uniquement** dans l’éditeur HTML.

## <a name="to-implement-a-hidden-text-region"></a>Pour implémenter une zone de texte masquée

1. Appelez `QueryService` pour <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Appelle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , en passant un pointeur pour une mémoire tampon de texte donnée. Cela détermine si une session de texte masqué existe déjà pour la mémoire tampon.

3. S’il en existe déjà un, vous n’avez pas besoin d’en créer un et un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet existant est retourné. Utilisez ce pointeur pour énumérer et créer des zones de texte masquées. Sinon, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> pour créer une session de texte masqué pour la mémoire tampon.

     Un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objet est retourné.

    > [!NOTE]
    > Lorsque vous appelez `CreateHiddenTextSession` , vous pouvez spécifier un client de texte masqué (autrement dit, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). Le client texte masqué vous avertit lorsque le texte masqué ou le mode plan est développé ou réduit par l’utilisateur.

4. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> pour ajouter une ou plusieurs nouvelles régions en mode plan à la fois, en spécifiant les informations suivantes dans le `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> paramètre () :

    1. Spécifiez une valeur `hrtConcealed` dans le `iType` membre de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure pour indiquer que vous créez une zone masquée, plutôt qu’une région en mode plan.

        > [!NOTE]
        > Lorsque les régions masquées sont masquées, l’éditeur affiche automatiquement des lignes autour des zones masquées pour indiquer leur présence.

    2. Spécifiez si la région est contrôlée par le client ou contrôlée par l’éditeur dans les `dwBehavior` membres de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> structure. Votre implémentation de la mise en plan intelligente peut contenir une combinaison de zones de texte masquées et de plan de l’éditeur et contrôlés par le client.
