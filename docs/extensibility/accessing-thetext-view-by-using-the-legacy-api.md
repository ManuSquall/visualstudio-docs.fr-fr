---
title: "L’accès à theText vue à l’aide de l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bea908ee04913c5ec56678f1438229e045bf68c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>L’accès à theText vue à l’aide de l’API héritée
Une vue de texte est une présentation du texte qui est stocké dans une mémoire tampon de texte. Vous pouvez accéder à l’affichage de texte à l’aide de l’API héritée comme indiqué dans la section suivante.  
  
## <a name="text-view-object"></a>Objet de vue de texte  
 Chaque vue est associé à sa propre mémoire tampon de texte, et la vue est une fenêtre sur les données dans la mémoire tampon. Le diagramme suivant montre les interfaces de clé de l’objet de vue de texte, qui est représenté par <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objet de vue de Visual Studio texte](../extensibility/media/vstextview.gif "vstextview")  
Objet de vue de texte  
  
 La vue est une façon de présenter le texte dans la mémoire tampon. Il inclut des fonctionnalités telles que le retour automatique à et le mode plan, afin que ce que vous voyez dans la vue n’est pas une représentation exacte du texte dans la mémoire tampon.  
  
 Une vue permet d’autres services ou un processus pour intercepter les commandes entrantes et agir sur ces derniers avant de la vue agit sur les. Le service courants pour ce faire est un service de langage. Un service de langage, par exemple, devra peut-être intercepter la commande pour la touche entrée fournir des conseils de comportement ou l’outil de mise en retrait personnalisées.  
  
## <a name="adding-functionality-to-the-text-view"></a>Ajout de fonctionnalités à l’affichage de texte  
 Vous pouvez personnaliser le comportement d’affichage de texte en gérant les séquences de touches spécifiques. Pour intercepter les séquences de touches, vous implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sur votre objet et fournissent une cible de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pour surveiller et intercepter des commandes.  
  
 L’affichage de texte utilise une architecture séquentiel pour les filtres de la commande. Nouveaux filtres de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objets) sont ajoutés à la séquence en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode).  
  
 Notification d’événement pour l’affichage de texte est fournie à l’aide de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interface. Implémentez cette interface sur votre objet client pour recevoir une notification des modifications apportées à l’affichage de texte. Exposer cette interface pour l’affichage de texte à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface sur l’affichage de texte pour recevoir une notification de modifications à partir de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des paramètres de la vue à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [À l’aide du Gestionnaire de texte pour surveiller des paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)