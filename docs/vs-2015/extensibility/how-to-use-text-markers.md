---
title: 'Comment : utiliser des marqueurs de texte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839617"
---
# <a name="how-to-use-text-markers"></a>Guide pratique pour utiliser des marqueurs de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les marqueurs de texte peuvent être appliqués pour modifier un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objet.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-apply-text-markers"></a>Pour appliquer des marqueurs de texte  
  
1. Obtenez une instance de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    > L’éditeur principal applique automatiquement des marqueurs de texte standard à tout document qu’il modifie, et il n’est pas nécessaire d’appliquer explicitement des marqueurs de texte standard.  
  
2. Obtenez un ID de type de marqueur pour le marqueur qui vous intéresse en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode avec le `GUID` du marqueur de texte que vous souhaitez utiliser.  
  
    > [!NOTE]
    > N’utilisez pas le `GUID` du VSPackage ou le service qui fournit le marqueur de texte.  
  
3. Utilisez l’ID de type de marqueur obtenu en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode en tant que paramètre pour appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour appliquer un marqueur de texte à une zone de texte donnée.  
  
#### <a name="to-add-features-to-text-markers"></a>Pour ajouter des fonctionnalités à des marqueurs de texte  
  
1. Il peut être souhaitable d’ajouter des fonctionnalités supplémentaires à un marqueur de texte, telles que des info-bulles, un menu contextuel spécial ou un gestionnaire pour des circonstances particulières. Pour ce faire :  
  
2. Créez un objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
3. Si vous souhaitez des fonctionnalités supplémentaires, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> et les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces sur le même objet qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
4. Transmettez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface que vous créez à l’appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode utilisée pour appliquer le marqueur de texte à une zone de texte donnée.  
  
5. Lorsque vous ajoutez une prise en charge du menu contextuel à une région de marqueur de texte, il est nécessaire de créer le menu.  
  
     Pour plus d’informations sur la création d’un menu contextuel, consultez [menus contextuels](../extensibility/context-menus.md).  
  
6. L' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement appelle les méthodes des interfaces fournies, telles que la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> méthode, ou la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)   
 [Guide pratique pour implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)
