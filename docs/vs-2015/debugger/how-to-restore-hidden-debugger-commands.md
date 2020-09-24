---
title: 'Comment : restaurer les commandes masquées du débogueur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 297be3a3a4ad3c70ad28c627d5dc8d64c6ba1c7a
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147236"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Comment : restaurer les commandes masquées du débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous installez Visual Studio, vous êtes invité à choisir un jeu de paramètres IDE par défaut pour votre langage de programmation principal. Les paramètres IDE par défaut de quelques langages peuvent masquer certaines commandes de débogueur.  
  
 Si vous souhaitez utiliser une fonctionnalité de débogueur masquée par vos paramètres IDE par défaut, vous pouvez replacer la commande dans le menu à l’aide de la procédure suivante.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Pour restaurer des commandes de débogueur masquées  
  
1. Un projet étant ouvert, dans le menu **Outils**, cliquez sur **Personnaliser**.  
  
2. Dans la boîte de dialogue **Personnaliser** , cliquez sur l’onglet **Commandes** .  
  
3. Dans le menu déroulant **Barre de menus :**, sélectionnez le menu **Déboguer** qui doit contenir la commande restaurée.  
  
4. Cliquez sur la **commande Ajouter...** .  
  
5. Dans la zone **Ajouter une commande**, sélectionnez la commande que vous souhaitez ajouter, puis cliquez sur **OK**.  
  
6. Répétez l'étape précédente pour ajouter une autre commande.  
  
7. Cliquez sur **Fermer** lorsque vous avez terminé d'ajouter des commandes au menu.  
  
    > [!WARNING]
    > Certains éléments du menu n'apparaissent que lorsque le débogueur se trouve dans un mode spécifique, tel que le mode exécution ou le mode arrêt. Par conséquent, un élément que vous avez ajouté n'est pas forcément immédiatement visible lorsque vous avez terminé ces étapes.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Restauration de commandes non disponibles dans la boîte de dialogue Personnaliser  
 Quelques commandes, surtout dans les menus hiérarchiques, ne peuvent pas être restaurées dans la boîte de dialogue **Personnaliser**. Pour les restaurer, vous devez importer une nouvelle collection de paramètres IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Pour importer de nouveaux paramètres IDE  
  
1. Dans le menu **Outils**, cliquez sur **Importation et exportation des paramètres**.  
  
2. Sur la page **Bienvenue dans l'Assistant Importation et exportation des paramètres**, cliquez sur **Importer les paramètres d'environnement sélectionnés**, puis cliquez sur **Suivant**.  
  
3. Sur la page **Enregistrer les paramètres actuels**, enregistrez ou non vos paramètres existants, puis cliquez sur **Suivant**.  
  
4. Sur la page **Choisir une collection de paramètres à importer**, dans le dossier **Paramètres par défaut**, choisissez une collection de paramètres de développement dotés des commandes à utiliser. Si vous ne savez pas quelle collection choisir, essayez **Paramètres de développement généraux** ou **Paramètres de développement Visual C++**, option qui fournit le plus grand nombre de commandes de débogueur.  
  
5. Cliquez sur **Suivant**.  
  
6. Sur la page **Choisir les paramètres à importer**, sous **Options**, assurez-vous que **Débogage** est sélectionné. Désactivez les autres cases à cocher, sauf si vous souhaitez également importer ces paramètres.  
  
7. Cliquez sur **Terminer**.  
  
8. Sur la page **Importation terminée**, examinez les erreurs associées à la réinitialisation de vos paramètres sous **Détails**.  
  
9. Cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)
