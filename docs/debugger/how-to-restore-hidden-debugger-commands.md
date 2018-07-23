---
title: 'Comment : restaurer les commandes masquées du débogueur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9ee37e72a52f866f5b67afaeacfd248628a3484
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176841"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Comment : restaurer les commandes masquées du débogueur
Lorsque vous installez Visual Studio, vous êtes invité à choisir un jeu de paramètres IDE par défaut pour votre langage de programmation principal. Les paramètres IDE par défaut de quelques langages peuvent masquer certaines commandes de débogueur.  
  
 Si vous souhaitez utiliser une fonctionnalité de débogueur masquée par vos paramètres IDE par défaut, vous pouvez replacer la commande dans le menu à l’aide de la procédure suivante.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Pour restaurer des commandes de débogueur masquées  
  
1.  Avec un projet ouvert, dans le **outils** menu, cliquez sur **personnaliser**.  
  
2.  Dans le **personnaliser** boîte de dialogue, cliquez sur le **commandes** onglet.  
  
3.  Dans le **barre de menus :** liste déroulante, sélectionnez le **déboguer** menu que vous voulez contenir la commande restaurée.  
  
4.  Cliquez sur le **ajouter commande...**  bouton.  
  
5.  Dans le **ajouter une commande** , sélectionnez la commande que vous souhaitez ajouter, puis cliquez sur **OK**.  
  
6.  Répétez l'étape précédente pour ajouter une autre commande.  
  
7.  Cliquez sur **fermer** lorsque vous avez terminé l’ajout de commandes au menu.  
  
    > [!WARNING]
    >  Certains éléments du menu n'apparaissent que lorsque le débogueur se trouve dans un mode spécifique, tel que le mode exécution ou le mode arrêt. Par conséquent, un élément que vous avez ajouté n'est pas forcément immédiatement visible lorsque vous avez terminé ces étapes.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Restauration de commandes non disponibles dans la boîte de dialogue Personnaliser  
 Certaines commandes, surtout dans les menus hiérarchiques, ne peuvent pas être restaurées à partir de la **personnaliser** boîte de dialogue. Pour les restaurer, vous devez importer une nouvelle collection de paramètres IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Pour importer de nouveaux paramètres IDE  
  
1.  Sur le **outils** menu, cliquez sur **importation et exportation de paramètres**.  
  
2.  Sur le **Bienvenue dans l’Assistant Importation et exportation paramètres** , cliquez sur **importer les paramètres d’environnement sélectionnés**, puis cliquez sur **suivant**.  
  
3.  Sur le **enregistrer les paramètres actuels** page, décidez s’il faut enregistrer vos paramètres existants, puis cliquez sur **suivant**.  
  
4.  Sur le **choisir une collection de paramètres à importer** page, sous la **paramètres par défaut** dossier, choisissez une collection de paramètres de développement qui comporte les commandes que vous souhaitez utiliser. Si vous ne connaissez pas quelle collection choisir, essayez **paramètres de développement généraux** ou **paramètres de développement Visual C++**, qui fournit le meilleur parti des commandes de débogueur.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **choisir les paramètres à importer** page sous **Options**, assurez-vous que **débogage** est sélectionné. Désactivez les autres cases à cocher, sauf si vous souhaitez également importer ces paramètres.  
  
7.  Cliquez sur **Terminer**.  
  
8.  Sur le **importation complète** page, passez en revue les erreurs associées à la réinitialisation de vos paramètres sous **détails**.  
  
9. Cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/getting-started-with-the-debugger.md)