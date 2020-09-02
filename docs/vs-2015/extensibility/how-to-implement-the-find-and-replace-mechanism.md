---
title: 'Comment : implémenter le mécanisme de recherche et de remplacement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548693"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Guide pratique pour implémenter le mécanisme Rechercher et remplacer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio offre deux façons d’implémenter rechercher/remplacer. L’une consiste à passer une image de texte à l’interpréteur de commandes et à l’autoriser à gérer la recherche, la mise en surbrillance et le remplacement de texte. Cela permet aux utilisateurs de spécifier plusieurs étendues de texte. Votre VSPackage peut également contrôler cette fonctionnalité elle-même. Dans les deux cas, vous devez notifier l’interpréteur de commandes sur la cible actuelle et les cibles pour tous les documents ouverts.  
  
### <a name="to-implement-findreplace"></a>Pour implémenter rechercher/remplacer  
  
1. Implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interface sur l’un des objets retournés par les propriétés de frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Si vous créez un éditeur personnalisé, vous devez implémenter cette interface dans le cadre de la classe de l’éditeur personnalisé.  
  
2. Utilisez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> méthode pour spécifier les options que votre éditeur prend en charge et pour indiquer s’il implémente la recherche d’image de texte.  
  
     Si votre éditeur prend en charge la recherche d’images de texte, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     Sinon, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. Si vous implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> méthodes et, vous pouvez simplifier vos tâches de recherche en appelant l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
