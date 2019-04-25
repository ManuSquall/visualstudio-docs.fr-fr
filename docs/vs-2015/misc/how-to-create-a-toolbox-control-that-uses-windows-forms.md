---
title: 'Procédure : Créer un contrôle de boîte à outils qui utilise Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a2b51b8f07a1cc049e4761001bfea754b6ca1819
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105641"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Procédure : Créer un contrôle de boîte à outils qui utilise Windows Forms
Le modèle de contrôle de boîte à outils Windows Forms inclus dans le [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] vous permet de créer des contrôles Windows Forms qui sont automatiquement ajoutés à la **boîte à outils** au moment où l’extension est installée. Cette rubrique vous montre comment utiliser le modèle pour créer un contrôle de **boîte à outils** que vous pouvez distribuer à d’autres utilisateurs.  
  
> [!NOTE]
>  Pour savoir comment télécharger le Kit de développement logiciel (SDK) Visual Studio, consultez [Centre de développement d’extensibilité Visual Studio](http://go.microsoft.com/fwlink/?linkid=121964) sur le site web MSDN.  
  
## <a name="creating-a-toolbox-control"></a>Création d’un contrôle de boîte à outils  
 Pour créer le projet, utilisez le modèle de contrôle de boîte à outils Windows Forms, puis générez une interface utilisateur (IU) dans le concepteur.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Pour créer un projet de contrôle de boîte à outils Windows Forms  
  
1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2. Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, cliquez sur le nœud correspondant à votre langage de programmation préféré, puis cliquez sur **Extensibilité**. Dans la liste des types de projets, sélectionnez **Contrôle de boîte à outils Windows Forms**.  
  
3. Dans la zone **Nom** , tapez le nom que vous souhaitez utiliser pour le projet. Cliquez sur **OK**.  
  
     Visual Studio crée une solution qui contient un contrôle utilisateur, un attribut pour placer le contrôle dans la **boîte à outils**et un manifeste VSIX pour le déploiement.  
  
#### <a name="to-build-the-control-ui"></a>Pour générer l’interface utilisateur du contrôle  
  
1. Dans l’ **Explorateur de solutions**, double-cliquez sur ToolboxControl.cs pour l’ouvrir dans le concepteur.  
  
2. À partir de la **boîte à outils**, faites glisser les contrôles de votre choix vers l’aire de conception, puis disposez-les en fonction de votre conception.  
  
3. Dans la fenêtre **Propriétés** , définissez les propriétés publiques du contrôle utilisateur et des contrôles enfants.  
  
## <a name="coding-the-control"></a>Codage du contrôle  
 Par défaut, votre contrôle apparaît dans la **boîte à outils** sous le nom **ToolboxControl1** dans un groupe d’éléments de **boîte à outils** qui a le même nom que votre solution. Vous pouvez modifier ces noms dans le fichier ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Pour coder le contrôle  
  
1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur ToolboxControl.cs, puis cliquez sur **Afficher le code** pour ouvrir le fichier en mode code.  
  
2. Au niveau de la définition de la classe partielle qui implémente le contrôle, cliquez avec le bouton droit sur le nom de la classe, cliquez sur **Refactoriser**, puis sur **Renommer**. Remplacez le nom de la classe par le nom que vous voulez faire figurer dans la **boîte à outils** une fois le contrôle installé.  
  
3. Juste au-dessus de la définition de la classe, dans la déclaration de l’attribut `ProvideToolboxControl` , remplacez la valeur du premier paramètre par le nom du groupe d’éléments destiné à héberger le contrôle dans la **boîte à outils**.  
  
     L’exemple suivant présente l’attribut `ProvideToolboxControl` et la définition de la classe ajustée pour un contrôle nommé `Counter` dans le groupe d’éléments `General` .  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Implémentez les propriétés, méthodes et événements du contrôle.  
  
## <a name="building-testing-and-deployment"></a>Génération, test et déploiement  
 En appuyant sur F5, vous générez le projet, qui comprend un fichier de déploiement .vsix et une deuxième instance de Visual Studio s’ouvre dans laquelle le contrôle est installé dans la **boîte à outils**.  
  
#### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle  
  
1. Appuyez sur F5.  
  
2. Dans la nouvelle instance de Visual Studio, créez un projet d’application Windows Forms.  
  
3. Recherchez votre contrôle dans la **boîte à outils** et faites-la glisser vers l’aire de conception.  
  
4. Dans la fenêtre **Propriétés** , vérifiez que les propriétés apparaissent comme prévu.  
  
5. Ajoutez si nécessaire du code ou des contrôles supplémentaires pour tester vos méthodes et événements.  
  
6. Appuyez sur F5 pour ouvrir l’application Windows Forms.  
  
7. Vérifiez que les propriétés, méthodes et événements de votre contrôle se comportent comme prévu.  
  
#### <a name="to-deploy-the-control"></a>Pour déployer le contenu  
  
1. Après avoir généré le projet testé, ouvrez le dossier \bin\debug\ du projet dans l’Explorateur de fichiers et recherchez le fichier .vsix.  
  
2. Chargez le fichier .vsix sur un réseau ou un site web.  
  
     Si vous chargez le fichier à la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) site Web, les autres utilisateurs peuvent utiliser **Gestionnaire d’extensions** dans Visual Studio pour rechercher le contrôle et l’installer.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)