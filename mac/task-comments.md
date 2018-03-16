---
title: "Commentaires des tâches"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 674bae5b22c5b9ecc5d6fda4a9a4e30e4fcd1660
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, une pratique standard est de commenter explicitement le code non achevé ou sur lequel vous avez des doutes, ainsi que les solutions de contournement rapides avec des avertissements. Les jetons de signal par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Les jetons personnalisés peuvent être définis sous **Visual Studio > Préférences... > Environnement > Tâches**, comme illustré dans l’image suivante :

 ![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Exemple :

```
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en mettant les mettant en surbrillance dans la zone Liste des tâches, qui peut être affichée en accédant à **Afficher > Panneaux > Tâche** :

![Panneau Liste des tâches](media/source-editor-image11.png)