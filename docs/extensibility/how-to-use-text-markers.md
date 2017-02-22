---
title: "Comment : utiliser des marqueurs de texte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - à l'aide de marqueurs de texte"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment : utiliser des marqueurs de texte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les marqueurs de texte peuvent être appliqués pour modifier un objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## Procédures  
  
#### pour appliquer des marqueurs de texte  
  
1.  obtenez une instance de la classe d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> .  
  
    > [!NOTE]
    >  L'éditeur principal appliquent automatiquement les marqueurs de texte standard à tout document qu'il modifie, et ne doit pas être nécessaire d'appliquer les marqueurs de texte standard explicitement.  
  
2.  Obtenez un ID de type de marqueur de marqueur qui vous intéressent en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> avec `GUID` du marqueur de texte que vous souhaitez à utiliser.  
  
    > [!NOTE]
    >  n'utilisez pas `GUID` du VSPackage ou du service qui fournit le marqueur de texte.  
  
3.  Utilisez l'ID de type de marqueur obtenu en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> comme paramètre pour appeler la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> ou la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> pour appliquer un marqueur de texte à une zone donnée de texte.  
  
#### Pour ajouter des fonctionnalités à des marqueurs de texte  
  
1.  Il peut être souhaitable d'ajouter des fonctionnalités supplémentaires à un marqueur de texte, tel que des info\-bulles, un menu contextuel spécial, ou le gestionnaire pour les circonstances particulières.  Pour cela :  
  
2.  Créez un objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
3.  Si les fonctionnalités supplémentaires est souhaitée, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>, et les interfaces d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> sur le même objet qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
4.  passez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> que vous créez, à l'appel à la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> ou à la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> utilisée pour appliquer le marqueur de texte à une zone donnée de texte.  
  
5.  en ajoutant la prise en charge de menu contextuel à une zone de marqueur de texte il est nécessaire de créer le menu.  
  
     Pour plus d'informations sur la création d'un menu contextuel consultez, [Menus contextuels](../extensibility/context-menus.md).  
  
6.  L'environnement de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle les méthodes d'interfaces fournies, telles que la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> , ou la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> si nécessaire.  
  
## Voir aussi  
 [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : ajouter des marqueurs de texte Standard](../extensibility/how-to-add-standard-text-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : implémenter des marqueurs d'erreur](../extensibility/how-to-implement-error-markers.md)