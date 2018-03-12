---
title: "Comment : utiliser des marqueurs de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>Comment : utiliser des marqueurs de texte
Marqueurs de texte peuvent être appliquées pour modifier un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objet.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-apply-text-markers"></a>Pour appliquer des marqueurs de texte  
  
1.  Pour obtenir une instance de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    >  L’éditeur principal applique automatiquement des marqueurs de texte standard à un document qu’il modifie et ne doit pas être nécessaire d’appliquer explicitement des marqueurs de texte standard.  
  
2.  Obtenir un ID de type de marqueur de la marque qui vous intéressent en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode avec le `GUID` du marqueur de texte que vous souhaitez manipuler.  
  
    > [!NOTE]
    >  N’utilisez pas le `GUID` du VSPackage ou du service qui fournit le marqueur de texte.  
  
3.  Utilisez l’ID de type de marqueur est obtenu en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> méthode en tant que paramètre à appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> (méthode) ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour appliquer un marqueur de texte pour une région donnée de texte.  
  
#### <a name="to-add-features-to-text-markers"></a>Pour ajouter des fonctionnalités aux marqueurs de texte  
  
1.  Il peut être souhaitable d’ajouter des fonctionnalités supplémentaires à un marqueur de texte, tels que les info-bulles, un menu contextuel spécial ou le Gestionnaire des circonstances particulières. Pour cela :  
  
2.  Créer un objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
3.  Si vous souhaitez des fonctionnalités supplémentaires, implémentez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces sur le même objet qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
4.  Passer la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface que vous créez à l’appel à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode utilisée pour appliquer le marqueur de texte pour une région donnée de texte.  
  
5.  Lorsque vous ajoutez la prise en charge du menu contextuel à une zone de marqueur de texte, il est nécessaire créer le menu.  
  
     Pour plus d’informations sur la création d’un menu contextuel, consultez [contextuels](../extensibility/context-menus.md).  
  
6.  Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement appelle les méthodes des interfaces fournies, telles que la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> (méthode), ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode en fonction des besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)