---
title: "&#201;tape&#160;7&#160;: ajouter des composants Dialog &#224; votre formulaire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &#201;tape&#160;7&#160;: ajouter des composants Dialog &#224; votre formulaire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour que votre programme ouvre les fichiers image et choisisse une couleur d'arrière\-plan, lors de cette étape, ajoutez un composant **OpenFileDialog** et un composant **ColorDialog** à votre formulaire.  
  
 À certains égards, un composant est semblable à un contrôle.  Vous utilisez la Boîte à outils pour ajouter un composant à votre formulaire, et vous définissez ses propriétés à l'aide de la fenêtre **Propriétés**.  Mais contrairement à un contrôle, lorsque vous ajoutez un composant, il n'est pas visible dans votre formulaire.  À la place, il permet d'utiliser des comportements que vous pouvez déclencher à l'aide de code.  Un composant sert par exemple à ouvrir une boîte de dialogue **Ouvrir un fichier**.  
  
 ![lien vers la vidéo](../data-tools/media/playvideo.png "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [Didacticiel 1 : Créer une visionneuse d'images en Visual Basic – Vidéo 3](http://go.microsoft.com/fwlink/?LinkId=205213) ou [Didacticiel 1 : Créer une visionneuse d'images en C\# – Vidéo 3](http://go.microsoft.com/fwlink/?LinkId=205202).  Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d'interface utilisateur.  Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.  
  
### Pour ajouter des composants de boîte de dialogue à votre formulaire  
  
1.  Choisissez le Concepteur Windows Forms \(Form1.cs \[Design\] ou Form1.vb \[Design\]\), puis ouvrez le groupe **Boîtes de dialogue** dans la boîte à outils.  
  
    > [!NOTE]
    >  Le groupe **Boîtes de dialogue** de la Boîte à outils contient des composants capables d'ouvrir de nombreuses boîtes de dialogue utiles \(pour ouvrir et enregistrer des fichiers, parcourir des dossiers ou choisir des polices et des couleurs\).  Dans ce projet, vous utilisez deux composants de boîte de dialogue : **OpenFileDialog** et **ColorDialog**.  
  
2.  Pour ajouter un composant appelé **openFileDialog1** à votre formulaire, double\-cliquez sur **OpenFileDialog**.  Pour ajouter un composant appelé **colorDialog1** à votre formulaire, double\-cliquez sur **ColorDialog** dans la Boîte à outils. \(Vous l'utiliserez dans la prochaine étape de ce didacticiel.\) Une zone, contenant une icône pour chacun des deux composants de boîte de dialogue que vous avez ajoutés, doit s'afficher en bas du Concepteur Windows Forms \(sous le formulaire de la visionneuse d'images\), comme indiqué dans l'image suivante.  
  
     ![Composants de la boîte de dialogue](../ide/media/express_dialogsadded.png "Express\_DialogsAdded")  
Composants de boîte de dialogue  
  
3.  Sélectionnez l'icône **openFileDialog1** dans la zone située en bas du Concepteur Windows Forms.  Définissez deux propriétés :  
  
    -   Attribuez à la propriété **Filter** la valeur suivante \(vous pouvez la copier et la coller\) :  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Affectez la valeur suivante à la propriété **Title** : Sélectionner un fichier image  
  
         Les paramètres de la propriété **Filter** spécifient les types de fichiers qui s'afficheront dans la boîte de dialogue **Sélectionner un fichier image**.  
  
    > [!NOTE]
    >  Pour voir un exemple de la boîte de dialogue **Ouvrir un fichier** dans une application différente, ouvrez le Bloc\-notes ou Paint, et dans la barre de menus, choisissez **Fichier**, **Ouvrir**.  Notez la liste déroulante **Types de fichiers** qui se trouve en bas.  Pour cette configuration, vous venez d'utiliser la propriété **Filter** dans le composant **OpenFileDialog**.  Notez également que les propriétés **Title** et **Filter** sont écrites en gras dans la fenêtre **Propriétés**.  L'IDE utilise ce style pour vous montrer toutes les propriétés dont les valeurs par défaut ont été modifiées.  
  
### Pour continuer ou examiner  
  
-   Pour passer à l'étape suivante du didacticiel, consultez [Étape 8 : écrire du code pour le gestionnaire d'événements du bouton Afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Pour revenir à l'étape précédente du didacticiel, consultez [Étape 6 : affecter un nom à vos contrôles bouton](../ide/step-6-name-your-button-controls.md).