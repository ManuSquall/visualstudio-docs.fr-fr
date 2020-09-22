---
title: 'Comment : ajouter des marqueurs de texte standard | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839298"
---
# <a name="how-to-add-standard-text-markers"></a>Guide pratique pour ajouter des marqueurs de texte standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez la procédure suivante pour créer l’un des types de marqueurs de texte par défaut fournis avec l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] éditeur principal.  
  
### <a name="to-create-a-text-marker"></a>Pour créer un marqueur de texte  
  
1. Selon que vous utilisez un système de coordonnées à une ou deux dimensions, appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour créer un nouveau marqueur de texte.  
  
     Dans cet appel de méthode, spécifiez un type de marqueur, une plage de texte pour créer le marqueur et une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface. Cette méthode retourne ensuite un pointeur désignant le marqueur de texte nouvellement créé. Les types de marqueur sont extraits de l' <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> énumération. Spécifiez une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface si vous souhaitez être informé des événements de marqueur.  
  
    > [!NOTE]
    > Créez des marqueurs de texte sur le thread d’interface utilisateur principal uniquement. L’éditeur principal s’appuie sur le contenu de la mémoire tampon de texte pour créer des marqueurs de texte et la mémoire tampon de texte n’est pas thread-safe.  
  
## <a name="adding-a-custom-command"></a>Ajout d’une commande personnalisée  
 L’implémentation de l' `IVsTextMarkerClient` interface et la fourniture d’un pointeur vers celle-ci à partir d’un marqueur améliorent le comportement des marqueurs de plusieurs façons. Tout d’abord, cela vous permet de fournir des conseils pour votre marqueur et d’exécuter des commandes. Cela vous permet également de recevoir des notifications d’événements pour des marqueurs individuels et de créer un menu contextuel personnalisé sur le marqueur. Utilisez la procédure suivante pour ajouter une commande personnalisée au menu contextuel du marqueur.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Pour ajouter une commande personnalisée au menu contextuel  
  
1. Avant que le menu contextuel ne s’affiche, l’environnement appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> méthode et passe un pointeur vers le marqueur de texte affecté et le numéro de l’élément de commande dans le menu contextuel.  
  
     Par exemple, les commandes spécifiques aux points d’arrêt dans le menu contextuel incluent **supprimer le point d’arrêt** via le **nouveau point d’arrêt**, comme indiqué dans la capture d’écran suivante.  
  
     ![Menu contextuel Marqueur](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Repassez du texte identifiant le nom de la commande personnalisée. Par exemple, **supprimer un point d’arrêt** peut être une commande personnalisée si l’environnement ne l’a pas déjà fourni. Vous revenez également si la commande est prise en charge, disponible et activée, et/ou un basculement actif. L’environnement utilise ces informations pour afficher la commande personnalisée dans le menu contextuel de la manière correcte.  
  
3. Pour exécuter la commande, l’environnement appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode, en passant un pointeur vers le marqueur de texte et le numéro de la commande sélectionnée dans le menu contextuel.  
  
     Utilisez ces informations à partir de cet appel pour exécuter toutes les actions du marqueur de texte que votre commande personnalisée dicte.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Comment : implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)   
 [Comment : créer des marqueurs de texte personnalisés](../extensibility/how-to-create-custom-text-markers.md)   
 [Guide pratique pour utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)
