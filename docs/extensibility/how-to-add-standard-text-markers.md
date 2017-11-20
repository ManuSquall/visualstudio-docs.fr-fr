---
title: "Comment : ajouter des marqueurs de texte Standard | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fb92185dd2efee7f42ce1ba4d97435e0b2e8a68
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-standard-text-markers"></a>Comment : ajouter des marqueurs de texte Standard
Utilisez la procédure suivante pour créer un des types de marqueur de texte par défaut fournis avec le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal.  
  
### <a name="to-create-a-text-marker"></a>Pour créer un marqueur de texte  
  
1.  Selon que vous utilisez un ou deux dimensions, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour créer un nouveau marqueur de texte.  
  
     Dans cet appel de méthode, spécifiez un type de marqueur, une plage de texte pour créer le marqueur et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface. Ensuite, cette méthode retourne un pointeur au marqueur de texte qui vient d’être créé. Types de marqueur sont tirées de la <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> énumération. Spécifiez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface si vous souhaitez être informé des événements de marqueur.  
  
    > [!NOTE]
    >  Créer des marqueurs de texte sur le thread principal dans l’interface utilisateur. L’éditeur principal s’appuie sur le contenu de la mémoire tampon de texte pour créer des marqueurs de texte et la mémoire tampon de texte n’est pas thread-safe.  
  
## <a name="adding-a-custom-command"></a>Ajout d’une commande personnalisée  
 Mise en œuvre le `IVsTextMarkerClient` interface et en fournissant un pointeur à celui-ci à partir d’un marqueur améliore le comportement de marqueur de plusieurs façons. Tout d’abord, cela permet de vous fournissent des conseils pour le curseur et d’exécuter des commandes. Cela vous permet également de recevoir des notifications d’événements pour les marqueurs individuels et pour créer un menu contextuel personnalisé sur le marqueur. Utilisez la procédure suivante pour ajouter une commande personnalisée au menu contextuel marqueur.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Pour ajouter une commande personnalisée au menu contextuel  
  
1.  Avant que le menu contextuel s’affiche, l’environnement appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> méthode et passe vous un pointeur vers le marqueur de texte concerné et le numéro de l’élément de commande dans le menu contextuel.  
  
     Par exemple, les commandes de point d’arrêt spécifique dans le menu contextuel incluent **supprimer un point d’arrêt** via **nouveau point d’arrêt**, comme indiqué dans la capture d’écran suivante.  
  
     ![Menu contextuel marqueur](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Passer du texte identifiant le nom de la commande personnalisée. Par exemple, **supprimer un point d’arrêt** peut être une commande personnalisée si l’environnement n’a pas déjà fourni il. Vous passez également si la commande est pris en charge, disponible et activée et/ou un bouton bascule marche / arrêt. L’environnement utilise ces informations pour afficher la commande personnalisée dans le menu contextuel de la façon correcte.  
  
3.  Pour exécuter la commande, l’environnement appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode, en passant un pointeur vers le marqueur de texte et le numéro de la commande sélectionnée dans le menu contextuel.  
  
     Utilisez ces informations à partir de cet appel pour exécuter toute action de marqueur de texte dicte de votre commande personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de marqueurs de texte avec l’API hérité](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Comment : créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)   
 [Comment : utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)