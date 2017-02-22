---
title: "Comment : ajouter des marqueurs de texte Standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - marqueurs de texte standard"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment : ajouter des marqueurs de texte Standard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez la procédure suivante pour créer un des types de marqueur de texte par défaut fournis d'éditeur principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
### pour créer un marqueur de texte  
  
1.  Selon que vous utilisez une ou le système de coordonnées à deux dimensions, appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> ou la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> pour créer un marqueur de texte.  
  
     dans cet appel de méthode, spécifiez un type de marqueur, une plage de texte pour créer la marque plus de, et une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  Cette méthode retourne ensuite un pointeur vers le marqueur de texte récemment créée.  Les types de marqueur sont pris de l'énumération d' <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> .  Spécifiez une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> si vous souhaitez être informés des événements de marque.  
  
    > [!NOTE]
    >  Créez des marqueurs de texte sur le thread d'interface utilisateur principal uniquement.  L'éditeur principal dépend du contenu de la mémoire tampon de texte pour créer des marqueurs de texte et la mémoire tampon de texte n'est pas thread\-safe.  
  
## ajouter une commande personnalisée  
 Implémenter l'interface de `IVsTextMarkerClient` et la fourniture d'un pointeur partir d'une marque améliore le comportement de marque de plusieurs façons.  D'abord, cela vous permet de fournir des conseils pour votre marque et d'exécuter des commandes.  Cela vous permet également de recevoir des notifications d'événements pour des marques et créer un menu contextuel personnalisé sur la marque.  Utilisez la procédure suivante pour ajouter une commande personnalisée au menu contextuel de la marque.  
  
#### pour ajouter une commande personnalisée au menu contextuel  
  
1.  Avant que le menu contextuel affiché, l'environnement appelle la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> et vous passe un pointeur vers le marqueur de texte affectées et le numéro de l'élément de commande dans le menu contextuel.  
  
     Par exemple, les commandes de point d'arrêt\-détail dans le menu contextuel incluent **supprimez le point d'arrêt** via **Nouveau point d'arrêt**, comme le montre la capture d'écran suivante.  
  
     ![Menu contextuel Marqueur](../extensibility/media/vsmarkercontextmenu.png "vsMarkercontextmenu")  
  
2.  Passez en arrière du texte identifiant le nom de la commande personnalisée.  Par exemple, **supprimez le point d'arrêt** peut être une commande personnalisée si l'environnement ne la fournissait pas déjà.  Vous passez également en arrière si la commande est prise en charge, disponible et actif, et\/ou une bascule aligner sur.  L'environnement utilise ces informations pour afficher la commande personnalisée dans le menu contextuel de la façon correcte.  
  
3.  Pour exécuter la commande, les appels d'environnement la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> , vous pouvez passer un pointeur vers le marqueur de texte et numéro de la commande sélectionnée dans le menu contextuel.  
  
     Utilisez ces informations de cet appel pour exécuter toute action du marqueur de texte votre commande personnalisée implique.  
  
## Voir aussi  
 [À l'aide de marqueurs de texte avec l'API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : implémenter des marqueurs d'erreur](../extensibility/how-to-implement-error-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)