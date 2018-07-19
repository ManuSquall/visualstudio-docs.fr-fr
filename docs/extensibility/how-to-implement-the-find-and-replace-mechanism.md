---
title: 'Comment : implémenter la rechercher et remplacer le mécanisme | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45d0b1307d86b32f1def3c4474e1ca25959915c0
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056444"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Comment : implémenter la rechercher et remplacer le mécanisme

Visual Studio fournit deux méthodes d’implémentation de rechercher/remplacer. Une façon consiste à passer d’une image de texte à l’interpréteur de commandes et qu’il traite de la recherche, la mise en surbrillance et le texte en remplaçant. Cela permet aux utilisateurs de spécifier plusieurs étendues de texte. Vous pouvez également votre VSPackage peut contrôler cette fonctionnalité lui-même. Dans les deux cas, vous devez informer l’interpréteur de commandes sur la cible actuelle et les cibles pour tous les documents ouverts.

## <a name="to-implement-findreplace"></a>Pour implémenter les rechercher/remplacer.

1. Implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interface sur l’un des objets retournés par les propriétés de frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Si vous créez un éditeur personnalisé, vous devez implémenter cette interface dans le cadre de la classe d’éditeur personnalisé.

2. Utilisez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> méthode pour spécifier les options qui prend en charge de votre éditeur et pour indiquer si elle implémente la recherche de texte image.

   Si votre éditeur prend en charge la recherche de texte image, implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   Sinon, implémenter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. Si vous implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> méthodes, vous pouvez simplifier vos tâches de recherche en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interface.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>