---
title: L’accès à theText vue à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bce39d8ae736d9f7dcda8b18198053f90933b811
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892152"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>Accéder à l’affichage de texte à l’aide de l’API héritée
Une vue de texte est une présentation du texte qui est stocké dans une mémoire tampon de texte. Vous pouvez accéder à l’affichage de texte à l’aide de l’API héritée comme indiqué dans la section suivante.

## <a name="text-view-object"></a>Objet de vue de texte
 Chaque vue est associé à sa propre mémoire tampon de texte, et la vue est une fenêtre sur les données dans la mémoire tampon. Le diagramme suivant illustre les interfaces de clé de l’objet de vue de texte, qui est représentée par <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Objet de vue de texte Visual Studio](../extensibility/media/vstextview.gif)

 La vue est une façon de présenter le texte dans la mémoire tampon. Il inclut des fonctionnalités telles que le retour automatique à et le mode plan, afin que ce que vous voyez dans la vue n’est pas une représentation exacte du texte dans la mémoire tampon.

 Un affichage permet à d’autres services ou processus d’intercepter les commandes entrantes et d’agir sur ces derniers avant de la vue agit en conséquence. Le service plus courants pour ce faire est un service de langage. Un service de langage peut devoir, par exemple, intercepter la commande pour la touche entrée pour fournir des conseils personnalisés de comportement ou l’outil de mise en retrait.

## <a name="add-functionality-to-the-text-view"></a>Ajouter des fonctionnalités à l’affichage de texte
 Vous pouvez personnaliser le comportement d’affichage de texte en gérant les séquences de touches spécifiques. Pour intercepter les séquences de touches, vous implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sur votre objet et fournir une cible de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) pour surveiller et intercepter des commandes.

 L’affichage de texte utilise une architecture séquentiel pour les filtres de commande. Nouveaux filtres de commande (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objets) sont ajoutés à la séquence en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (méthode).

 Notification d’événement pour l’affichage de texte est fournie à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> interface. Implémentez cette interface sur votre objet client pour recevoir une notification des modifications apportées à l’affichage de texte. Exposer cette interface pour l’affichage de texte à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface sur l’affichage de texte pour recevoir une notification de modifications à partir de la vue.

## <a name="see-also"></a>Voir aussi

- [Modifier les paramètres de vue à l’aide de l’API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Utilisez le Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)