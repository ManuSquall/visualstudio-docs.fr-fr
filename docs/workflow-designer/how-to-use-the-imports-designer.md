---
title: "Comment : utiliser le Concepteur d’importations | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d6e530a82c1edfa221203b6c99f06151fe901af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-the-imports-designer"></a>Procédure : utiliser le concepteur d'importations
Le concepteur d'importations vous permet d'entrer des espaces de noms pour les types que vous utiliserez dans vos expressions. Tout comme le **importe** ou **à l’aide de** activer de mots clés dans Visual Basic .NET et c#, en spécifiant les espaces de noms dans le Concepteur d’importations vous permet d’entrer simplement un nom de type dans votre expression plutôt qu’un complet nom de type version.  
  
 Le concepteur d'importations réagit aux modifications apportées à l'interface utilisateur ainsi qu'aux modifications apportées lors de l'enregistrement du workflow. Lorsque le workflow est enregistré, des espaces de noms peuvent être automatiquement ajoutés au concepteur d'importations. Notamment :  
  
-   les espaces de noms pour tout type utilisé dans les déclarations de variables et d'arguments ;  
  
-   les espaces de noms pour tout type utilisé dans des expressions ;  
  
-   tous les autres espaces de noms requis pour la sérialisation du workflow (par exemple, les espaces de noms utilisés par les activités personnalisées déposées dans le workflow).  
  
 Lorsque le workflow est enregistré, vous pouvez remarquer que certains espaces de noms que vous avez supprimés manuellement sont automatiquement à nouveau ajoutés au concepteur d'importations en raison de la logique décrite dans la liste précédente.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Pour ajouter un espace de noms à la liste d'espaces de noms importés  
  
1.  Ouvrez une application de service de workflow WCF, une application console de workflow ou un projet de bibliothèque d'activités dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ou une application de workflow réhébergée.  
  
2.  Cliquez sur **importations** au bas de la zone de dessin principale. Le concepteur d'importations s'affiche.  
  
3.  Entrez ou sélectionnez un espace de noms dans le contrôle de liste déroulante situé en haut du concepteur d'importations.  
  
     À mesure que vous tapez, une liste d'espaces de noms valides qui correspondent aux caractères tapés s'affiche.  
  
4.  Appuyez sur **entrée** pour ajouter l’espace de noms à la liste.  
  
5.  Si vous souhaitez supprimer un espace de noms de la liste, sélectionnez l’espace de noms et appuyez sur la **supprimer** clé de votre clavier. Notez qu'un espace de noms peut être supprimé s'il n'est pas valide pour une raison quelconque, par exemple si l'assembly qui contient l'espace de noms n'est plus référencé par le projet.