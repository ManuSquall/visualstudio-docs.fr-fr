---
title: "Comment&#160;: cr&#233;er un contr&#244;le de bo&#238;te &#224; outils qui utilise Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Boîte à outils, contrôle"
  - "WinForms"
  - "boîte à outils"
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Comment&#160;: cr&#233;er un contr&#244;le de bo&#238;te &#224; outils qui utilise Windows Forms
Le modèle de contrôle de boîte à outils Windows Forms inclus dans le [!INCLUDE[vssdk_dev11_long](../misc/includes/vssdk_dev11_long_md.md)] vous permet de créer des contrôles Windows Forms qui sont automatiquement ajoutés à la **boîte à outils** au moment où l’extension est installée. Cette rubrique vous montre comment utiliser le modèle pour créer un contrôle de **boîte à outils** que vous pouvez distribuer à d’autres utilisateurs.  
  
> [!NOTE]
>  Pour savoir comment télécharger le Kit de développement logiciel \(SDK\) Visual Studio, consultez [Centre de développement d’extensibilité Visual Studio](http://go.microsoft.com/fwlink/?linkid=121964) sur le site web MSDN.  
  
## Création d’un contrôle de boîte à outils  
 Pour créer le projet, utilisez le modèle de contrôle de boîte à outils Windows Forms, puis générez une interface utilisateur \(IU\) dans le concepteur.  
  
#### Pour créer un projet de contrôle de boîte à outils Windows Forms  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Modèles installés**, cliquez sur le nœud correspondant à votre langage de programmation préféré, puis cliquez sur **Extensibilité**. Dans la liste des types de projets, sélectionnez **Contrôle de boîte à outils Windows Forms**.  
  
3.  Dans la zone **Nom**, tapez le nom que vous souhaitez utiliser pour le projet. Cliquez sur **OK**.  
  
     Visual Studio crée une solution qui contient un contrôle utilisateur, un attribut pour placer le contrôle dans la **boîte à outils** et un manifeste VSIX pour le déploiement.  
  
#### Pour générer l’interface utilisateur du contrôle  
  
1.  Dans l’**Explorateur de solutions**, double\-cliquez sur ToolboxControl.cs pour l’ouvrir dans le concepteur.  
  
2.  À partir de la **boîte à outils**, faites glisser les contrôles de votre choix vers l’aire de conception, puis disposez\-les en fonction de votre conception.  
  
3.  Dans la fenêtre **Propriétés**, définissez les propriétés publiques du contrôle utilisateur et des contrôles enfants.  
  
## Codage du contrôle  
 Par défaut, votre contrôle apparaît dans la **boîte à outils** sous le nom **ToolboxControl1** dans un groupe d’éléments de **boîte à outils** qui a le même nom que votre solution. Vous pouvez modifier ces noms dans le fichier ToolboxControl.cs.  
  
#### Pour coder le contrôle  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur ToolboxControl.cs, puis cliquez sur **Afficher le code**  pour ouvrir le fichier en mode code.  
  
2.  Au niveau de la définition de la classe partielle qui implémente le contrôle, cliquez avec le bouton droit sur le nom de la classe, cliquez sur **Refactoriser**, puis sur **Renommer**. Remplacez le nom de la classe par le nom que vous voulez faire figurer dans la **boîte à outils** une fois le contrôle installé.  
  
3.  Juste au\-dessus de la définition de la classe, dans la déclaration de l’attribut `ProvideToolboxControl`, remplacez la valeur du premier paramètre par le nom du groupe d’éléments destiné à héberger le contrôle dans la **boîte à outils**.  
  
     L’exemple suivant présente l’attribut `ProvideToolboxControl` et la définition de la classe ajustée pour un contrôle nommé `Counter` dans le groupe d’éléments `General`.  
  
     [!code-cs[ToolboxControlWinForms#07](../misc/codesnippet/CSharp/how-to-create-a-toolbox-control-that-uses-windows-forms_1.cs)]  
  
4.  Implémentez les propriétés, méthodes et événements du contrôle.  
  
## Génération, test et déploiement  
 En appuyant sur F5, vous générez le projet, qui comprend un fichier de déploiement .vsix et une deuxième instance de Visual Studio s’ouvre dans laquelle le contrôle est installé dans la **boîte à outils**.  
  
#### Pour générer et tester le contrôle  
  
1.  Appuyez sur F5.  
  
2.  Dans la nouvelle instance de Visual Studio, créez un projet d’application Windows Forms.  
  
3.  Recherchez votre contrôle dans la **boîte à outils** et faites\-la glisser vers l’aire de conception.  
  
4.  Dans la fenêtre **Propriétés**, vérifiez que les propriétés apparaissent comme prévu.  
  
5.  Ajoutez si nécessaire du code ou des contrôles supplémentaires pour tester vos méthodes et événements.  
  
6.  Appuyez sur F5 pour ouvrir l’application Windows Forms.  
  
7.  Vérifiez que les propriétés, méthodes et événements de votre contrôle se comportent comme prévu.  
  
#### Pour déployer le contenu  
  
1.  Après avoir généré le projet testé, ouvrez le dossier \\bin\\debug\\ du projet dans l’Explorateur de fichiers et recherchez le fichier .vsix.  
  
2.  Chargez le fichier .vsix sur un réseau ou un site web.  
  
     Si vous chargez le fichier sur le site web [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), les autres utilisateurs peuvent utiliser le **Gestionnaire d’extensions** de Visual Studio pour rechercher le contrôle et l’installer.  
  
## Voir aussi  
 [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)