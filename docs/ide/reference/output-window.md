---
title: "Fen&#234;tre Sortie | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.build.output"
  - "vs.debug.output"
  - "vs.output"
helpviewer_keywords: 
  - "Sortie (fenêtre), à propos de la fenêtre Sortie"
  - "Sortie (fenêtre)"
  - "Boîte à outils, suppression de contrôles"
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 30
caps.handback.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Fen&#234;tre Sortie
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La fenêtre **Sortie** affiche des messages d'état relatifs à diverses fonctionnalités de l'environnement de développement intégré \(IDE\).  Pour ouvrir la fenêtre **Sortie**, dans la barre de menus, sélectionnez **Vue\/sortie** \(ou cliquez sur Ctrl \+ Alt \+ O\).  
  
> [!WARNING]
>  La fenêtre Sortie n'apparaît pas dans le menu Affichage dans les éditions Visual Studio Express.  Pour ce faire, utilisez la touche directe Ctrl \+ Alt \+ Y.  
  
## Barre d'outils  
 **Afficher la sortie à partir de**  
 Affiche un ou plusieurs volets de sortie à afficher.  Plusieurs volets d'informations peuvent être disponibles en fonction des outils de l'environnement IDE qui ont utilisé la fenêtre **Sortie** pour afficher des messages aux utilisateurs.  
  
 **Rechercher le message dans le code**  
 Place le point d'insertion dans l'éditeur de code sur la ligne qui contient l'erreur de build sélectionnée.  
  
 **Atteindre le message précédent**  
 Change le focus dans la fenêtre **Sortie** à l'erreur de build précédente et place le point d'insertion dans l'éditeur de code, à la ligne qui contient cette erreur de build.  
  
 **Atteindre le message suivant**  
 Change le focus dans la fenêtre **Sortie** à l'erreur de build suivante et place le point d'insertion dans l'éditeur de code, à la ligne qui contient cette erreur de build.  
  
 **Effacer tout**  
 Efface tout le texte du volet **Sortie**.  
  
 **Activer\/Désactiver le retour automatique à la ligne**  
 Active et désactive la fonctionnalité de retour à la ligne dans le volet **Sortie**.  Lorsque la fonctionnalité Retour automatique à la ligne est activée, le texte des entrées les plus longues est ramené à la ligne suivante lorsqu'il sort de la zone d'affichage.  
  
## Volet Sortie  
 Le volet **Sortie** sélectionné dans la liste **Afficher la sortie à partir de** affiche la sortie de la source indiquée.  
  
## Routage des messages vers la fenêtre Sortie  
 Pour afficher la fenêtre **Sortie** chaque fois que vous générez un projet, dans la boîte de dialogue **Général, Projets et solutions, options**, sélectionnez **Afficher la fenêtre Sortie au démarrage de la génération**.  Ensuite, avec un fichier de code ouvert pour modifier, choisissez les boutons **Atteindre le message suivant** et **Atteindre le message précédent** dans la barre d'outils de la fenêtre **Sortie** pour sélectionner des entrées dans le volet **Sortie**.  Pendant ce temps, le point d'insertion dans l'éditeur de code saute à la ligne de code où le problème sélectionné se produit.  
  
 Certaines fonctionnalités et commandes IDE appelées dans la fenêtre Commande \([Commande, fenêtre](../../ide/reference/command-window.md)\) livrent leur sortie dans la fenêtre **Sortie**.  La sortie des outils externes tels que les fichiers .bat et .com, qui est généralement affiché dans la fenêtre d'invite de commandes, est routée vers un volet **Sortie** lorsque vous sélectionnez l'option **Utiliser la fenêtre Sortie** dans [Gestion des outils externes](../../ide/managing-external-tools.md).  Nombre d'autres types de messages peuvent également être affichés dans les volets **Sortie**.  Par exemple, lorsque la syntaxe Transact\-SQL d'une procédure stockée est vérifiée par rapport à une base de données cible, les résultats s'affichent dans la fenêtre **Sortie**.  
  
 Vous pouvez également programmer vos propres applications pour écrire des messages de diagnostic au moment de l'exécution dans un volet **Sortie**.  Pour cela, les membres de la classe <xref:System.Diagnostics.Debug> ou la classe <xref:System.Diagnostics.Trace> dans l'espace de noms <xref:System.Diagnostics> de la bibliothèque de classes .NET Framework.  Les membres de la classe <xref:System.Diagnostics.Debug> affichent leur sortie lorsque vous générez des configurations Debug de votre solution ou projet ; les membres de la classe <xref:System.Diagnostics.Trace> affichent leur sortie lorsque vous générez des configurations Debug ou Release.  Pour plus d'informations, consultez [Messages de diagnostic dans la fenêtre Sortie](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 En [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)], vous pouvez créer des étapes de génération personnalisées et des événements de build dont les avertissements et les erreurs sont affichés et comptabilisés dans le volet **Sortie**.  En appuyant sur F1 dans une ligne de sortie, vous pouvez afficher une rubrique d'aide appropriée.  Pour plus d'informations, consultez [Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build](/visual-cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).  
  
## Comportement de défilement  
 Si vous utilisez le défilement automatique dans la fenêtre Sortie puis accédez en utilisant la souris ou les touches de direction, faites défiler automatiquement des points.  Pour poursuivre le défilement automatique, appuyez sur CTRL\+FIN.  
  
## Voir aussi  
 [Messages de diagnostic dans la fenêtre Sortie](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Comment : contrôler la fenêtre Sortie](../Topic/How%20to:%20Control%20the%20Output%20Window.md)   
 [Génération d'applications dans Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)   
 [Présentation des configurations de build](../../ide/understanding-build-configurations.md)   
 [Vue d'ensemble de la bibliothèque de classes](../Topic/.NET%20Framework%20Class%20Library%20Overview.md)