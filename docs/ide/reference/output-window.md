---
title: "Sortie, fenêtre| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 118223d1a5c07188b8f8d8c7b6990792dcd94ff5
ms.lasthandoff: 02/22/2017

---
# <a name="output-window"></a>Fenêtre Sortie
La fenêtre **Sortie** peut afficher des messages d’état pour diverses fonctionnalités dans l’environnement de développement intégré (IDE). Pour ouvrir la fenêtre **Sortie**, dans la barre de menus, choisissez **Affichage/Sortie** (ou cliquez sur Ctrl+Alt+O).  
  
> [!WARNING]
>  La fenêtre Sortie n’apparaît pas dans le menu Affichage des éditions Visual Studio Express. Pour l’afficher, utilisez le raccourci clavier Ctrl+Alt+O.  
  
## <a name="toolbar"></a>ToolBar  
 **Afficher la sortie à partir de**  
 Affiche un ou plusieurs volets de sortie à afficher. Plusieurs volets d’informations peuvent être disponibles, suivant les outils de l’IDE qui ont utilisé la fenêtre **Sortie** pour remettre des messages à l’utilisateur.  
  
 **Rechercher le message dans le code**  
 Déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient l’erreur de build sélectionnée.  
  
 **Atteindre le message précédent**  
 Place le focus dans la fenêtre **Sortie** sur l’erreur de build précédente et déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient cette erreur de build.  
  
 **Atteindre le message suivant**  
 Place le focus dans la fenêtre **Sortie** sur l’erreur de build suivante et déplace le point d’insertion dans l’éditeur de code vers la ligne qui contient cette erreur de build.  
  
 **Effacer tout**  
 Efface tout le texte du volet **Sortie**.  
  
 **Activer/Désactiver le retour automatique à la ligne**  
 Active et désactive la fonctionnalité de retour automatique à la ligne dans le volet **Sortie**. Quand cette option est activée, le texte des longues entrées qui s’étend au-delà de la zone d’affichage apparaît sur la ligne suivante.  
  
## <a name="output-pane"></a>Volet Sortie  
 Le contenu du volet **Sortie** sélectionné dans la liste **Afficher la sortie à partir de** provient de la source indiquée.  
  
## <a name="routing-messages-to-the-output-window"></a>Routage des messages vers la fenêtre Sortie  
 Pour afficher la fenêtre **Sortie** chaque fois que vous générez un projet, dans la boîte de dialogue **Général, Projets et solutions, Options**, sélectionnez **Afficher la fenêtre Sortie au démarrage de la génération**. Ensuite, avec un fichier de code ouvert pour modification, choisissez les boutons **Atteindre le message suivant** et **Atteindre le message précédent** dans la barre d’outils de la fenêtre **Sortie** pour sélectionner des entrées dans le volet **Sortie**. Parallèlement, le point d’insertion dans l’éditeur de code se positionne sur la ligne de code à laquelle se produit le problème sélectionné.  
  
 Certaines fonctionnalités et commandes IDE appelées dans la [fenêtre Commande](../../ide/reference/command-window.md) remettent leur sortie à la fenêtre **Sortie**. La sortie des outils externes tels que les fichiers .bat et .com, qui s’affiche généralement dans la fenêtre Invite de commandes, est routée vers un volet **Sortie** quand vous sélectionnez l’option **Utiliser la fenêtre Sortie** dans la [gestion des outils externes](../../ide/managing-external-tools.md). D’autres types de messages peuvent également être affichés dans les volets **Sortie**. Par exemple, quand la syntaxe Transact-SQL d’une procédure stockée fait l’objet d’une vérification par rapport à une base de données cible, les résultats sont affichés dans la fenêtre **Sortie**.  
  
 Vous pouvez également programmer vos propres applications pour qu’elles écrivent les messages de diagnostic au moment de l’exécution vers un volet **Sortie**. Pour ce faire, utilisez les membres de la classe <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace> dans l’espace de noms <xref:System.Diagnostics> de la bibliothèque de classes .NET Framework. Les membres de la classe <xref:System.Diagnostics.Debug> affichent la sortie quand vous générez des configurations Debug de votre solution ou projet ; les membres de la classe <xref:System.Diagnostics.Trace> affichent la sortie quand vous générez des configurations Debug ou Release. Pour plus d’informations, consultez [Messages de diagnostic dans la fenêtre Sortie](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 Dans [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], vous pouvez créer des étapes de génération personnalisées et des événements de build dont les avertissements et erreurs sont affichés et comptabilisés dans le volet **Sortie**. En appuyant sur F1 dans une ligne de sortie, vous pouvez afficher une rubrique d’aide appropriée. Pour plus d’informations, consultez [Mise en forme de la sortie d’une étape de génération personnalisée ou d’un événement de build](/visual-cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).  
  
## <a name="scrolling-behavior"></a>Comportement de défilement  
 Si vous utilisez le défilement automatique dans la fenêtre Sortie, puis que vous naviguez à l’aide de la souris ou des touches de direction, le défilement automatique s’arrête. Pour reprendre le défilement automatique, appuyez sur Ctrl+Fin.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages de diagnostic dans la fenêtre Sortie](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Comment : contrôler la fenêtre Sortie](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)   
 [Présentation des configurations de build](../../ide/understanding-build-configurations.md)   
 [Présentation des bibliothèques de classes](http://msdn.microsoft.com/Library/7e4c5921-955d-4b06-8709-101873acf157)
