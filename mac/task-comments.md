---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 23ce804476b6495d45e114728b287c1f5f85d1d9
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956635"
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