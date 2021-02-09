---
title: 'Concepteur de flux de travail-comment : utiliser le concepteur d’importations'
description: Découvrez comment le concepteur d’importations vous permet d’entrer des espaces de noms pour les types que vous allez utiliser dans vos expressions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd736c01843d746ee43a82e6bb6f5239da1c660e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894047"
---
# <a name="how-to-use-the-imports-designer"></a>Procédure : utiliser le concepteur d'importations

Le concepteur d'importations vous permet d'entrer des espaces de noms pour les types que vous utiliserez dans vos expressions. À l’instar des **importations** ou de **l’utilisation** de mots clés dans Visual Basic et C#, la spécification d’espaces de noms dans le concepteur d’importations vous permet d’entrer simplement un nom de type dans votre expression plutôt qu’un nom de type de version complet.

Le concepteur d'importations réagit aux modifications apportées à l'interface utilisateur ainsi qu'aux modifications apportées lors de l'enregistrement du workflow. Lorsque le workflow est enregistré, des espaces de noms peuvent être automatiquement ajoutés au concepteur d'importations. Leurs thèmes sont les suivants :

- les espaces de noms pour tout type utilisé dans les déclarations de variables et d’arguments ;

- les espaces de noms pour tout type utilisé dans des expressions ;

- tous les autres espaces de noms requis pour la sérialisation du workflow (par exemple, les espaces de noms utilisés par les activités personnalisées déposées dans le workflow).

  Lorsque le workflow est enregistré, vous pouvez remarquer que certains espaces de noms que vous avez supprimés manuellement sont automatiquement à nouveau ajoutés au concepteur d'importations en raison de la logique décrite dans la liste précédente.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Pour ajouter un espace de noms à la liste d'espaces de noms importés

1. Ouvrez une application de service de workflow WCF, une application console de workflow ou un projet de bibliothèque d’activités dans Visual Studio ou une application de flux de travail réhébergée.

2. Cliquez sur **importations** en bas de la zone de dessin principale. Le concepteur d'importations s'affiche.

3. Entrez ou sélectionnez un espace de noms dans le contrôle de liste déroulante situé en haut du concepteur d'importations.

     À mesure que vous tapez, une liste d'espaces de noms valides qui correspondent aux caractères tapés s'affiche.

4. Appuyez sur **entrée** pour ajouter l’espace de noms à la liste.

5. Si vous souhaitez supprimer un espace de noms de la liste, sélectionnez l’espace de noms, puis appuyez sur la touche **Suppr** de votre clavier. Notez qu'un espace de noms peut être supprimé s'il n'est pas valide pour une raison quelconque, par exemple si l'assembly qui contient l'espace de noms n'est plus référencé par le projet.
