---
title: "L&#39;acc&#232;s &#224; theText vue &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - affichage de texte"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# L&#39;acc&#232;s &#224; theText vue &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un affichage de texte est une présentation de texte stocké dans une mémoire tampon de texte.  Vous pouvez accéder à l'affichage de texte à l'aide de l'API héritée comme indiqué dans la section suivante.  
  
## objet d'affichage de texte  
 Chaque vue est associée à sa propre mémoire tampon de texte, et la vue est une fenêtre sur les données dans la mémoire tampon.  Le diagramme suivant illustre les interfaces principales de l'objet d'affichage de texte, représenté par <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Objet de vue de texte Visual Studio](~/docs/extensibility/media/vstextview.gif "vstextview")  
objet d'affichage de texte  
  
 La vue est un moyen de disposition du texte dans la mémoire tampon.  Il inclut des fonctionnalités telles que le retour automatique à la ligne, et le mode plan, afin que ce que vous voyez dans la vue ne soit pas une représentation exacte du texte dans la mémoire tampon.  
  
 Une vue permet à d'autres services ou processus pour désactiver les commandes entrantes et pour agir sur ces valeurs avant que la vue agisse sur elles.  La plupart de service commun pour ce faire est un service de langage.  Un service de langage peut avoir besoin, par exemple, désactiver la commande pour la touche ENTRÉE fournisse un comportement personnalisé ou les info\-bulles de mise en retrait.  
  
## Ajout de fonctionnalités à l'affichage de texte  
 vous pouvez personnaliser le comportement d'affichage de texte en gérant des séquences de touches spécifiques.  Pour désactiver les séquences de touches, vous implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sur votre objet, et fournir une cible de la commande \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) pour surveiller et désactiver des commandes.  
  
 L'affichage de texte utilise l'architecture séquentielle des filtres de commande.  de nouveaux filtres de commande \(objets d'<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \) sont ajoutés à la séquence en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 la notification d'événements pour l'affichage de texte est fournie à l'aide de l'interface d' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` .  Implémentez cette interface sur votre objet client pour recevoir la notification des modifications apportées à l'affichage de texte.  Exposez cette interface à l'affichage de texte à l'aide de l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> de l'affichage de texte pour recevoir la notification des modifications de la vue.  
  
## Voir aussi  
 [Modification des paramètres d'affichage à l'aide de l'API héritée](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Utilisation du Gestionnaire de texte pour surveiller les paramètres globaux](../extensibility/using-the-text-manager-to-monitor-global-settings.md)