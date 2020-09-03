---
title: Commentaires des tâches
description: Ajout de commentaires sur des tâches à votre code
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 4f7f3d1567972c3841af6deb37677a7e01cdb825
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985173"
---
# <a name="task-comments"></a>Commentaires des tâches

Quand vous écrivez du code, il est d’usage de commenter explicitement le code non achevé ou sur lequel vous avez des doutes ainsi que les solutions de contournement rapides, avec des avertissements. Les jetons de signal par défaut fournis par Visual Studio pour Mac sont TODO, HACK, FIXME et UNDONE. Les jetons personnalisés peuvent être définis dans **Visual Studio > préférences > environnement > tâches**, comme illustré dans l’image suivante :

![Préférences de la liste des tâches](media/source-editor-image10.png)

Pour ajouter un nouveau commentaire de tâche, ajoutez un commentaire qui inclut le mot clé « task ». Par exemple :

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pour Mac attire l’attention sur ces marqueurs en les mettant en surbrillance dans le panneau **liste des tâches** , qui peut être affiché en accédant à **afficher > Pad > tâche**:

![Panneau Liste des tâches](media/source-editor-image11.png)

## <a name="see-also"></a>Voir aussi

- [Utiliser la liste des tâches (Visual Studio sur Windows)](/visualstudio/ide/using-the-task-list)