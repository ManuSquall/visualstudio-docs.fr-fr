---
title: 'Le Concepteur de flux de travail - Comment : utiliser le Concepteur d’importations'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de974ebba6fbe746a4d7acb4c1a20fefa5488a8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970646"
---
# <a name="how-to-use-the-imports-designer"></a>Procédure : utiliser le concepteur d'importations

Le concepteur d'importations vous permet d'entrer des espaces de noms pour les types que vous utiliserez dans vos expressions. Tout comme le **importe** ou **à l’aide de** mots clés dans Visual Basic et c#, en spécifiant les espaces de noms dans le Concepteur d’importations vous permet d’entrer simplement un nom de type dans votre expression plutôt qu’un complet activer nom de type version.

Le concepteur d'importations réagit aux modifications apportées à l'interface utilisateur ainsi qu'aux modifications apportées lors de l'enregistrement du workflow. Lorsque le workflow est enregistré, des espaces de noms peuvent être automatiquement ajoutés au concepteur d'importations. Notamment :

-   les espaces de noms pour tout type utilisé dans les déclarations de variables et d'arguments ;

-   les espaces de noms pour tout type utilisé dans des expressions ;

-   tous les autres espaces de noms requis pour la sérialisation du workflow (par exemple, les espaces de noms utilisés par les activités personnalisées déposées dans le workflow).

 Lorsque le workflow est enregistré, vous pouvez remarquer que certains espaces de noms que vous avez supprimés manuellement sont automatiquement à nouveau ajoutés au concepteur d'importations en raison de la logique décrite dans la liste précédente.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Pour ajouter un espace de noms à la liste d'espaces de noms importés

1.  Ouvrez une application de service de Workflow WCF, une application console de workflow ou un projet de bibliothèque d’activités dans Visual Studio 2010 ou une application de workflow réhébergé.

2.  Cliquez sur **importations** au bas de la zone de dessin principale. Le concepteur d'importations s'affiche.

3.  Entrez ou sélectionnez un espace de noms dans le contrôle de liste déroulante situé en haut du concepteur d'importations.

     À mesure que vous tapez, une liste d'espaces de noms valides qui correspondent aux caractères tapés s'affiche.

4.  Appuyez sur **entrée** pour ajouter l’espace de noms à la liste.

5.  Si vous souhaitez supprimer un espace de noms de la liste, sélectionnez l’espace de noms et appuyez sur la **supprimer** clé de votre clavier. Notez qu'un espace de noms peut être supprimé s'il n'est pas valide pour une raison quelconque, par exemple si l'assembly qui contient l'espace de noms n'est plus référencé par le projet.