---
title: "Cr&#233;ation d’une fen&#234;tre Outil de base | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Kit de développement logiciel (SDK) Visual Studio, fenêtres Outil"
  - "fenêtres Outil, créer dans l’IDE"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Cr&#233;ation d’une fen&#234;tre Outil de base
Les fenêtres Outil sont courantes dans Visual Studio : les fenêtres **Explorateur de solutions**, **Liste des tâches**, **Liste d’erreurs** et **Sortie** sont toutes des fenêtres Outil. Toutes les fenêtres Outil peuvent être ancrées dans l’IDE de la même manière. Un ancrage prévisible permet aux utilisateurs de gérer efficacement les tâches et informations.  
  
 Le modèle Package Visual Studio crée une implémentation de base d’une fenêtre Outil simple.  
  
### Pour créer une fenêtre Outil à l’aide du modèle Package Visual Studio  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez **Autres types de projets**, puis cliquez sur **Extensibilité**.  
  
3.  Dans le volet **Modèles**, cliquez sur **Package Visual Studio**.  
  
4.  Dans la zone **Emplacement**, tapez le chemin du fichier de votre VSPackage.  
  
5.  Dans la zone **Nom**, tapez le nom de la solution et cliquez sur **OK** pour démarrer le modèle.  
  
6.  Dans la page **Sélectionner un langage de programmation**, sélectionnez C\# ou Visual Basic. Faites générer un fichier key.snk au modèle pour signer l’assembly. Sinon, cliquez sur **Parcourir** pour sélectionner votre propre fichier de clé. Le modèle crée une copie de votre fichier de clé et la nomme key.snk.  
  
7.  Dans la page **Informations de base sur le package Visual Studio**, spécifiez des détails concernant le VSPackage ou acceptez les valeurs par défaut. Pour plus d'informations, consultez [Procédure pas à pas : création d’une commande de menu à l’aide du modèle de package Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
8.  Dans la page **Sélectionner les options de package Visual Studio**, cochez Fenêtre Outil.  
  
9. Dans la page Options de la fenêtre d’outils, tapez le nom de la barre de titre dans la zone **Nom de la fenêtre**. Ce nom est également utilisé comme texte affiché pour la commande de menu de la fenêtre Outil. La commande de menu est ajoutée au sous\-menu **Autres fenêtres** du menu **Affichage**. Tapez l’ID de commande de la fenêtre Outil dans la zone **ID de commande**, ou acceptez la valeur par défaut.  
  
10. Cliquez sur **Terminer** pour créer votre VSPackage dans le dossier que vous avez spécifié.  
  
### Pour tester votre fenêtre Outil  
  
1.  Dans le menu **Affichage**, pointez sur **Autres fenêtres**, puis cliquez sur la commande de la fenêtre Outil. Une fenêtre Outil avec un bouton **Cliquez ici \!** s’affiche.  
  
2.  Cliquez sur le bouton. Un message s’affiche avec le texte suivant :  
  
     Nous sommes dans \[Company.\<Nom VSPackage\>.MyControl\].button1\_Click\(\).  
  
## Voir aussi  
 [Ouverture d’une fenêtre Outil par programmation](../misc/opening-a-tool-window-programmatically.md)   
 [Essentiel des VSPackages](../misc/vspackage-essentials.md)