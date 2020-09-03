---
title: Accès à la vue theText à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184953"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Accès à la vue texte à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un affichage de texte est une présentation du texte stocké dans une mémoire tampon de texte. Vous pouvez accéder à l’affichage de texte à l’aide de l’API héritée, comme indiqué dans la section suivante.  
  
## <a name="text-view-object"></a>Objet de vue de texte  
 Chaque vue est associée à sa propre mémoire tampon de texte, et la vue est une fenêtre sur les données dans la mémoire tampon. Le diagramme suivant montre les interfaces clés de l’objet d’affichage de texte, représenté par <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Objet de vue de texte Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Objet de vue de texte  
  
 La vue est un moyen de présenter le texte dans la mémoire tampon. Il inclut des fonctionnalités telles que le retour automatique à la ligne et le mode plan, de sorte que ce que vous voyez dans la vue n’est pas une représentation exacte du texte dans la mémoire tampon.  
  
 Une vue permet à d’autres services ou processus d’intercepter des commandes entrantes et d’agir dessus avant que la vue n’y agisse. Le service le plus courant pour effectuer cette opération est un service de langage. Un service de langage peut avoir besoin, par exemple, d’intercepter la commande pour la touche entrée pour fournir un comportement de mise en retrait personnalisé ou des info-bulles.  
  
## <a name="adding-functionality-to-the-text-view"></a>Ajout de fonctionnalités à l’affichage de texte  
 Vous pouvez personnaliser le comportement d’affichage de texte en gérant des séquences de touches spécifiques. Pour intercepter les séquences de touches, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sur votre objet et fournissez une cible de commande ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) pour analyser et intercepter les commandes.  
  
 L’affichage de texte utilise une architecture séquentielle pour les filtres de commande. De nouveaux filtres de commande ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objets) sont ajoutés à la séquence en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> méthode.  
  
 La notification d’événement pour l’affichage de texte est fournie à l’aide de l' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interface. Implémentez cette interface sur votre objet client pour recevoir la notification des modifications apportées à la vue de texte. Exposez cette interface à l’affichage de texte à l’aide de l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface de la vue de texte pour recevoir la notification des modifications de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des paramètres d’affichage à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Utilisation du gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
