---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692323"
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, il est d’usage de commenter explicitement le code non achevé ou sur lequel vous avez des doutes ainsi que les solutions de contournement rapides, avec des avertissements. Les jetons de signal par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Vous pouvez définir les jetons personnalisés sous **Visual Studio > Préférences > Environnement > Tâches**, comme illustré dans l’image suivante :

![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Par exemple :

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en les mettant en surbrillance dans la zone **Liste des tâches**, que vous pouvez afficher en accédant à **Affichage > Panneaux > Tâche** :

![Panneau Liste des tâches](media/source-editor-image11.png)

## <a name="see-also"></a>Voir aussi

- [Utiliser la liste des tâches (Visual Studio sur Windows)](/visualstudio/ide/using-the-task-list)