---
title: "Commentaires des tâches"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, une pratique standard est de commenter explicitement le code non achevé ou sur lequel vous avez des doutes, ainsi que les solutions de contournement rapides avec des avertissements. Les jetons de signalement par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Vous pouvez cependant définir des jetons personnalisés dans **Visual Studio > Préférences... > Environnement > Tâches**, comme illustré ci-dessous :

 ![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Exemple :

```
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en mettant les mettant en surbrillance dans la zone Liste des tâches, qui peut être affichée en accédant à **Afficher > Panneaux > Tâche** :

![Panneau Liste des tâches](media/source-editor-image11.png)