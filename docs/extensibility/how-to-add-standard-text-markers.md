---
title: 'Procédure : Ajouter des marqueurs de texte Standard | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e49b8f2b0cdccbf4c6acfab0c8b68b0f3ad1a5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340967"
---
# <a name="how-to-add-standard-text-markers"></a>Procédure : Ajouter des marqueurs de texte standard
Utilisez la procédure suivante pour créer l’un des types de marqueur de texte par défaut fournis avec le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal.

## <a name="to-create-a-text-marker"></a>Pour créer un marqueur de texte

1. Selon que vous utilisez une ou deux dimensions repère, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> méthode ou le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> méthode pour créer un nouveau marqueur de texte.

     Dans cet appel de méthode, spécifiez un type de marqueur, une plage de texte afin de créer le marqueur sur et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface. Ensuite, cette méthode retourne un pointeur au marqueur de texte qui vient d’être créée. Types de marqueur sont extraites de la <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> énumération. Spécifiez un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface si vous souhaitez être informé des événements de marqueur.

    > [!NOTE]
    > Créer des marqueurs de texte sur le thread principal dans l’interface utilisateur. L’éditeur principal s’appuie sur le contenu de la mémoire tampon de texte pour créer des marqueurs de texte et la mémoire tampon de texte n’est pas thread-safe.

## <a name="add-a-custom-command"></a>Ajouter une commande personnalisée
 Implémentation de la `IVsTextMarkerClient` interface et en fournissant un pointeur à celui-ci à partir d’un marqueur améliore le comportement de marqueur de plusieurs façons. Tout d’abord, cela vous permet à fournissent des conseils pour votre marque et d’exécuter des commandes. Cela vous permet également de recevoir des notifications d’événements pour les marqueurs individuels et pour créer un menu contextuel personnalisé sur le marqueur. Utilisez la procédure suivante pour ajouter une commande personnalisée au menu contextuel marqueur.

### <a name="to-add-a-custom-command-to-the-context-menu"></a>Pour ajouter une commande personnalisée au menu contextuel

1. Avant que le menu contextuel s’affiche, l’environnement appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> méthode et passe vous un pointeur vers le marqueur de texte concerné et le numéro de l’élément de commande dans le menu contextuel.

     Par exemple, les commandes de point d’arrêt spécifique dans le menu contextuel incluent **supprimer un point d’arrêt** via **nouveau point d’arrêt**, comme indiqué dans la capture d’écran suivante.

     ![Menu contextuel marqueur](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")

2. Transmettre un texte identifiant le nom de la commande personnalisée. Par exemple, **supprimer un point d’arrêt** peut être une commande personnalisée si l’environnement ne le n'a pas déjà fourni. Vous transmettez également si la commande n’est pris en charge, disponible et activée, et/ou un bouton bascule activé / désactivé. L’environnement utilise ces informations pour afficher la commande personnalisée dans le menu contextuel de la façon correcte.

3. Pour exécuter la commande, l’environnement appelle le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> méthode, en passant un pointeur vers le marqueur de texte et le numéro de la commande sélectionnée dans le menu contextuel.

     Utilisez ces informations à partir de cet appel pour exécuter toute action du marqueur de texte de votre commande personnalisée dicte.

## <a name="see-also"></a>Voir aussi
- [Utiliser des marqueurs de texte avec l’API héritée](../extensibility/using-text-markers-with-the-legacy-api.md)
- [Guide pratique pour Implémenter des marqueurs d’erreur](../extensibility/how-to-implement-error-markers.md)
- [Guide pratique pour Créer des marqueurs de texte personnalisé](../extensibility/how-to-create-custom-text-markers.md)
- [Guide pratique pour Utiliser des marqueurs de texte](../extensibility/how-to-use-text-markers.md)