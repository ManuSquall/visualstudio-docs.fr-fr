---
title: "Proc&#233;dure&#160;: utiliser le concepteur d&#39;importations | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Proc&#233;dure&#160;: utiliser le concepteur d&#39;importations
Le concepteur d'importations vous permet d'entrer des espaces de noms pour les types que vous utiliserez dans vos expressions.Très comparable aux mots clés **Imports** ou **using** dans Visual Basic .NET et C\#, la spécification d'espaces de noms dans le concepteur d'importations vous permet d'entrer simplement un nom de type dans votre expression plutôt qu'un nom de type de version complet.  
  
 Le concepteur d'importations réagit aux modifications apportées à l'interface utilisateur ainsi qu'aux modifications apportées lors de l'enregistrement du workflow.Lorsque le workflow est enregistré, des espaces de noms peuvent être automatiquement ajoutés au concepteur d'importations.Notamment :  
  
-   les espaces de noms pour tout type utilisé dans les déclarations de variables et d'arguments ;  
  
-   les espaces de noms pour tout type utilisé dans des expressions ;  
  
-   tous les autres espaces de noms requis pour la sérialisation du workflow \(par exemple, les espaces de noms utilisés par les activités personnalisées déposées dans le workflow\).  
  
 Lorsque le workflow est enregistré, vous pouvez remarquer que certains espaces de noms que vous avez supprimés manuellement sont automatiquement à nouveau ajoutés au concepteur d'importations en raison de la logique décrite dans la liste précédente.  
  
### Pour ajouter un espace de noms à la liste d'espaces de noms importés  
  
1.  Ouvrez une application de service de workflow WCF, une application console de workflow ou un projet de bibliothèque d'activités dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] ou une application de workflow réhébergée.  
  
2.  Cliquez sur **Importations** en bas de la zone de dessin principale.Le concepteur d'importations s'affiche.  
  
3.  Entrez ou sélectionnez un espace de noms dans le contrôle de liste déroulante situé en haut du concepteur d'importations.  
  
     À mesure que vous tapez, une liste d'espaces de noms valides qui correspondent aux caractères tapés s'affiche.  
  
4.  Appuyez sur **Entrée** pour ajouter l'espace de noms à la liste.  
  
5.  Si vous voulez supprimer un espace de noms de la liste, sélectionnez\-le, puis appuyez sur la touche **Suppr** de votre clavier.Notez qu'un espace de noms peut être supprimé s'il n'est pas valide pour une raison quelconque, par exemple si l'assembly qui contient l'espace de noms n'est plus référencé par le projet.