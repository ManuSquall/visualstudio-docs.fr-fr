---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224191"
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, une pratique standard est de commenter explicitement le code non achevé ou sur lequel vous avez des doutes, ainsi que les solutions de contournement rapides avec des avertissements. Les jetons de signal par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Les jetons personnalisés peuvent être définis sous **Visual Studio > Préférences... > Environnement > Tâches**, comme illustré dans l’image suivante :

 ![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Exemple :

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en mettant les mettant en surbrillance dans la zone Liste des tâches, qui peut être affichée en accédant à **Afficher > Panneaux > Tâche** :

![Panneau Liste des tâches](media/source-editor-image11.png)