---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
Le processeur de ressources utilisé pour transformer les fichiers .resx en ressources binaires a échoué.  La raison spécifique de l'erreur \(le cas échéant\) est ajoutée à la fin de la chaîne.  Le processus de génération échoue si cette erreur se produit.  
  
 La cause la plus probable de cette erreur est un fichier .resx incorrect.  Il se peut par exemple que le fichier ait été ouvert et modifié dans un éditeur de texte.  
  
 Si vous recevez une \<raison\> de type "L'élément a déjà été ajouté.  Clé du dictionnaire : 'NewControlName.\<Nom de propriété\>'  Clé ajoutée : 'ControlName.\<Nom de propriété\>'", lisez les étapes suivantes pour reproduire et corriger l'erreur.  
  
### Pour reproduire cette erreur  
  
1.  Créez une nouvelle application Windows.  Par défaut, Form1 est créé.  
  
2.  Dans le menu **Affichage**, cliquez sur **Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété **Localisable** la valeur `True`.  
  
4.  Dans la fenêtre **Propriétés**, cliquez sur **Langue** et affectez\-lui la valeur Japonais.  
  
5.  À partir de la boîte à outils, faites glisser un bouton dans le formulaire.  
  
6.  Renommez le bouton de "Button1" en "BUTTON1".  
  
7.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
### Pour corriger cette erreur  
  
1.  Dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Fichier**.  
  
2.  Repérez le fichier Form1.resx, puis cliquez sur **OK**.  Form1.resx est affiché.  
  
3.  Repérez les valeurs de clés d'origine, et puis supprimez\-les manuellement dans la liste des données.  Par exemple, vous avez un bouton nommé "Button1".  Vous changez le nom de ce bouton en "BUTTON1".  Les valeurs de clés pour "Button1" et "BUTTON1" sont dans Form1.resx.  Supprimez toutes les entrées de "Button1", puis régénérez le projet.  
  
## Voir aussi  
 [Resources in .Resx File Format](http://msdn.microsoft.com/fr-fr/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/fr-fr/f793852c-da06-4d52-a826-65f635844772)