---
title: 'Comment : implémenter la rechercher et remplacer le mécanisme | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128938"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Comment : implémenter la rechercher et remplacer le mécanisme
Visual Studio fournit deux méthodes d’implémentation de la recherche et le remplacement. Une façon consiste à passer d’une image de texte à l’interpréteur de commandes et qu’il traite la recherche, la mise en surbrillance et le texte de remplacement. Cela permet aux utilisateurs de spécifier plusieurs plages de texte. Votre VSPackage peut également contrôler cette fonctionnalité lui-même. Dans les deux cas, vous devez informer l’interpréteur de commandes sur la cible actuelle et les cibles pour tous les documents ouverts.  
  
### <a name="to-implement-findreplace"></a>Pour implémenter la recherche et le remplacement  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interface sur l’un des objets retournés par les propriétés de frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Si vous créez un éditeur personnalisé, vous devez implémenter cette interface dans le cadre de la classe d’éditeur personnalisé.  
  
2.  Utilisez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> méthode pour spécifier les options qui prend en charge par votre éditeur et pour indiquer si elle implémente la recherche de texte image.  
  
     Si votre éditeur prend en charge la recherche de texte image, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Sinon, mettre en œuvre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Si vous implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> méthodes, vous pouvez simplifier vos tâches de recherche en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>