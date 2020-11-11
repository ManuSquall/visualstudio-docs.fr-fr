---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493528"
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, il est d’usage de commenter explicitement le code non achevé ou sur lequel vous avez des doutes ainsi que les solutions de contournement rapides, avec des avertissements. Les jetons de signal par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Les jetons personnalisés peuvent être définis dans **Visual Studio > préférences > environnement > tâches** , comme illustré dans l’image suivante :

![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Exemple :

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en les mettant en surbrillance dans la fenêtre de **liste des tâches** , qui peut être affichée à l’aide du menu **Afficher > tâches** :

![Fenêtre Liste des tâches, avec un seul élément TODO](media/source-editor-image11.png)

## <a name="see-also"></a>Voir aussi

- [Utiliser la liste des tâches (Visual Studio sur Windows)](/visualstudio/ide/using-the-task-list)