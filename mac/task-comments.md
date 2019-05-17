---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999737"
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