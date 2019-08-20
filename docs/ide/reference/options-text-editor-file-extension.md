---
title: Options, Éditeur de texte, Extension de fichier
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.File_Extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13c79a4cae482990369fc8218bf0b7226ab05942
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919058"
---
# <a name="options-text-editor-file-extension"></a>Options, Éditeur de texte, Extension de fichier

Cette boîte de dialogue Options permet de spécifier comment tous les fichiers avec une extension donnée seront gérés par l’environnement de développement intégré (IDE) Visual Studio. Pour chaque **Extension** que vous entrez, vous pouvez sélectionner un éditeur. Cela vous permet de choisir l’éditeur IDE ou le concepteur dans lequel les documents d’un certain type s’ouvriront. Pour afficher ces options, choisissez **Options** dans le menu **Outils**, développez le nœud **Éditeur de texte**, puis sélectionnez **Extension de fichier**.

Quand vous sélectionnez une option « avec encodage », une boîte de dialogue s’affiche chaque fois que vous ouvrez un document de ce type et vous permet de sélectionner un schéma de codage pour le document. Ce comportement peut être utile si vous préparez des versions de vos documents de projet pour les utiliser sur différentes plateformes ou dans des langages cibles différents.

## <a name="uielement-list"></a>Liste UIElement

**Extension**

Tapez l’extension de fichier pour laquelle vous souhaitez définir un Éditeur choisi dans l’IDE.

**Éditeur**

Sélectionnez l’éditeur IDE ou le concepteur dans lequel les documents avec cette extension de fichier s’ouvriront. Quand vous sélectionnez une option « avec encodage », une boîte de dialogue s’affiche chaque fois que vous ouvrez un tel document et vous permet de sélectionner un schéma de codage.

**Ajouter**

Ajoute à la liste des extensions une entrée qui inclut l’**Extension** et l’**Éditeur choisi** spécifiés.

**Supprimer**

Supprime l’entrée sélectionnée de la liste des extensions.

**Liste d’extensions**

Répertorie toutes les extensions pour lesquelles un Éditeur choisi a été spécifié.

**Mapper les fichiers sans extension vers**

Sélectionnez cette option si vous souhaitez spécifier comment les fichiers sans extension doivent être gérés par l’IDE.

**Options des fichiers sans extensions**

Fournit la même liste que l’option **Éditeur**. Sélectionnez l’éditeur IDE ou le concepteur dans lequel les documents sans extension de fichier s’ouvriront.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour gérer les modes de l’éditeur](../../ide/how-to-manage-editor-modes.md)