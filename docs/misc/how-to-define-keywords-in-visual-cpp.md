---
title: "Comment&#160;: d&#233;finir des mots cl&#233;s dans Visual&#160;C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mots clés utilisateur"
  - "mots réservés, mots clés définis par l’utilisateur"
  - "mots clés définis par l'utilisateur"
  - "mots clés réservés, définis par l’utilisateur"
  - "usertype.dat"
  - "mots clés (C++), définis par l’utilisateur"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Comment&#160;: d&#233;finir des mots cl&#233;s dans Visual&#160;C++
Les mots clés sont des identificateurs réservés et prédéfinis qui ont des significations particulières. Ils ne peuvent pas être utilisés comme identificateurs dans un programme. Toutefois, vous pouvez définir vos propres mots clés en vue de les utiliser en Visual C\+\+, et vous pouvez leur assigner une coloration de syntaxe personnalisée. La coloration de syntaxe vous offre une aide visuelle sur la structure et l’état de votre code.  
  
### Pour définir vos propres mots clés Visual C\+\+  
  
1.  Utilisez l’[éditeur de code et de texte](http://msdn.microsoft.com/fr-fr/508e1f18-99d5-48ad-b5ad-d011b21c6ab1) ou Notepad.exe pour créer un fichier texte nommé `usertype.dat`.  
  
2.  Dans `usertype.dat`, tapez chaque mot clé défini par l’utilisateur sur une ligne distincte.  
  
3.  Enregistrez `usertype.dat` dans le répertoire qui contient devenv.exe. Par défaut, le chemin de ce répertoire est *\<lecteur\>*:\\Program Files\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)] *\<numéro\_version\_principale.secondaire\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../misc/includes/tla2sharptla_ide_md.md)]. Dans la mesure où ce répertoire est en lecture seule par défaut, vous devez disposer d’informations d’identification d’administration pour enregistrer `usertype.dat`.  
  
4.  Quittez Visual Studio, puis redémarrez\-le.  
  
    > [!NOTE]
    >  Vous ne pouvez pas renommer ou recharger le fichier `usertype.dat` pendant une session d’édition, car ce fichier est lu durant l’initialisation. Tous les paramètres de couleur précédemment définis sont prioritaires, car le mécanisme de coloration de syntaxe vérifie le fichier `usertype.dat` en dernier.  
  
5.  Dans le menu **Outils**, cliquez sur **Options**. Dans la boîte de dialogue **Options**, cliquez sur **Environnement**, sur **Polices et couleurs**, puis dans la liste **Éléments affichés**, cliquez sur **Mots clés d’utilisateur C\/C\+\+**.  
  
6.  Définissez les propriétés de police et de couleur des mots clés définis par l’utilisateur, comme décrit dans [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Pour plus d'informations, consultez [Mots clés C\+\+](/visual-cpp/cpp/keywords-cpp).  
  
## Voir aussi  
 [Exécution en tant que membre du groupe Utilisateurs](/visual-cpp/top/running-as-a-member-of-the-users-group)   
 [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md)