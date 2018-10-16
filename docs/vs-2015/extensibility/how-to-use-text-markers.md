---
title: 'Comment : utiliser des marqueurs de texte | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c23bcddceaf3d019add25c5d60ed843912348cc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243410"
---
# <a name="how-to-use-text-markers"></a>Comment : utiliser des marqueurs de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Marqueurs de texte peuvent être appliqués pour modifier un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objet.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-apply-text-markers"></a>Pour appliquer des marqueurs de texte  
  
1.  Pour obtenir une instance de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    >  L’éditeur principal applique automatiquement des marqueurs de texte standard à tout document qu’il est en train de modifier, et il ne doit pas être nécessaire appliquer explicitement les marqueurs de texte standard.  
  
2.  Obtenir un ID de type de marqueur de la marque vous intéressent en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode avec le `GUID` du marqueur de texte que vous souhaitez travailler avec.  
  
    > [!NOTE]
    >  N’utilisez pas le `GUID` du VSPackage ou du service qui fournit le marqueur de texte.  
  
3.  Utilisez l’ID de type de marqueur obtenu en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode en tant que paramètre pour appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour appliquer un marqueur de texte à une région donnée de texte.  
  
#### <a name="to-add-features-to-text-markers"></a>Pour ajouter des fonctionnalités aux marqueurs de texte  
  
1.  Il peut être souhaitable d’ajouter des fonctionnalités supplémentaires à un marqueur de texte, tels que les info-bulles, un menu contextuel spécial ou le Gestionnaire des circonstances particulières. Pour ce faire :  
  
2.  Créer un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
3.  Si vous souhaitez des fonctionnalités supplémentaires, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces sur le même objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
4.  Passer le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface que vous créez, à l’appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode utilisée pour appliquer le marqueur de texte à une région donnée de texte.  
  
5.  Lors de l’ajout de prise en charge du menu contextuel dans une région de marqueur de texte, il est nécessaire créer le menu.  
  
     Pour plus d’informations sur la création d’un menu contextuel, consultez [Menus contextuels](../extensibility/context-menus.md).  
  
6.  Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement appelle les méthodes des interfaces fournies, comme le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> (méthode), ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode en fonction des besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Guide pratique pour implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)

