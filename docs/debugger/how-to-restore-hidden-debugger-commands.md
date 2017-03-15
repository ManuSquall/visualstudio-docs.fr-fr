---
title: "Comment&#160;: restaurer les commandes masqu&#233;es du d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "commandes, débogueur"
  - "débogueur, restaurer des commandes"
  - "déboguer (Visual Studio), restaurer des commandes"
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment&#160;: restaurer les commandes masqu&#233;es du d&#233;bogueur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous installez Visual Studio, vous êtes invité à choisir un jeu de paramètres IDE par défaut pour votre langage de programmation principal.  Les paramètres IDE par défaut de quelques langages peuvent masquer certaines commandes de débogueur.  
  
 Si vous souhaitez utiliser une fonctionnalité de débogueur masquée par vos paramètres IDE par défaut, vous pouvez replacer la commande dans le menu à l'aide de la procédure suivante.  
  
### Pour restaurer des commandes de débogueur masquées  
  
1.  Un projet étant ouvert, dans le menu **Outils**, cliquez sur **Personnaliser**.  
  
2.  Dans la boîte de dialogue **Personnaliser**, cliquez sur l'onglet **Commandes**.  
  
3.  Dans le menu déroulant **Barre de menus :**, sélectionnez le menu **Déboguer** qui doit contenir la commande restaurée.  
  
4.  Cliquez sur le bouton **Ajouter une commande**.  
  
5.  Dans la zone **Ajouter une commande**, sélectionnez la commande que vous souhaitez ajouter, puis cliquez sur **OK**.  
  
6.  Répétez l'étape précédente pour ajouter une autre commande.  
  
7.  Cliquez sur **Fermer** lorsque vous avez terminé d'ajouter des commandes au menu.  
  
    > [!WARNING]
    >  Certains éléments du menu n'apparaissent que lorsque le débogueur se trouve dans un mode spécifique, tel que le mode exécution ou le mode arrêt.  Par conséquent, un élément que vous avez ajouté n'est pas forcément immédiatement visible lorsque vous avez terminé ces étapes.  
  
## Restauration de commandes non disponibles dans la boîte de dialogue Personnaliser  
 Quelques commandes, surtout dans les menus hiérarchiques, ne peuvent pas être restaurées dans la boîte de dialogue **Personnaliser**.  Pour les restaurer, vous devez importer une nouvelle collection de paramètres IDE.  
  
#### Pour importer de nouveaux paramètres IDE  
  
1.  Dans le menu **Outils**, cliquez sur **Importation et exportation des paramètres**.  
  
2.  Sur la page **Bienvenue dans l'Assistant Importation et exportation des paramètres**, cliquez sur **Importer les paramètres d'environnement sélectionnés**, puis cliquez sur **Suivant**.  
  
3.  Sur la page **Enregistrer les paramètres actuels**, enregistrez ou non vos paramètres existants, puis cliquez sur **Suivant**.  
  
4.  Sur la page **Choisir une collection de paramètres à importer**, dans le dossier **Paramètres par défaut**, choisissez une collection de paramètres de développement dotés des commandes à utiliser.  Si vous ne savez pas quelle collection choisir, essayez **Paramètres de développement généraux** ou **Paramètres de développement Visual C\+\+**, option qui fournit le plus grand nombre de commandes de débogueur.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur la page **Choisir les paramètres à importer**, sous **Options**, assurez\-vous que **Débogage** est sélectionné.  Désactivez les autres cases à cocher, sauf si vous souhaitez également importer ces paramètres.  
  
7.  Cliquez sur **Terminer**.  
  
8.  Sur la page **Importation terminée**, examinez les erreurs associées à la réinitialisation de vos paramètres sous **Détails**.  
  
9. Cliquez sur **Fermer**.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)