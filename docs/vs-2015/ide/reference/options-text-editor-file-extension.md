---
title: Options, Éditeur de texte, Extension de fichier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26c53633bc55efcf95ffbc579e24d2d61e4a0932
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662272"
---
# <a name="options-text-editor-file-extension"></a>Options, Éditeur de texte, Extension de fichier
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette boîte de dialogue Options permet de spécifier comment tous les fichiers avec une extension donnée seront gérés par l’environnement de développement intégré (IDE) Visual Studio. Pour chaque **Extension** que vous entrez, vous pouvez sélectionner un éditeur. Cela vous permet de choisir l’éditeur IDE ou le concepteur dans lequel les documents d’un certain type s’ouvriront. Pour afficher ces options, choisissez **Options** dans le menu **Outils**, développez le nœud **Éditeur de texte**, puis sélectionnez **Extension de fichier**.

 Quand vous sélectionnez une option « avec encodage », une boîte de dialogue s’affiche chaque fois que vous ouvrez un document de ce type et vous permet de sélectionner un schéma de codage pour le document. Ce comportement peut être utile si vous préparez des versions de vos documents de projet pour les utiliser sur différentes plateformes ou dans des langages cibles différents.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="uielement-list"></a>Liste des éléments d’interface
 **Extension** Tapez l’extension de fichier dont vous souhaitez définir l’expérience d’édition dans l’IDE.

 **Éditeur** Sélectionnez l’éditeur IDE ou le concepteur dans lequel les documents avec cette extension de fichier s’ouvriront. Quand vous sélectionnez une option « avec encodage », une boîte de dialogue s’affiche chaque fois que vous ouvrez un tel document et vous permet de sélectionner un schéma de codage.

 **Ajouter** Ajoute à la liste des extensions une entrée qui inclut l’**Extension** et l’**Éditeur choisi** spécifiés.

 **Supprimer** Supprime l’entrée sélectionnée de la liste d’extensions.

 Liste d’extensions répertorie toutes les extensions pour lesquelles une expérience d’édition a été spécifiée.

 **Mapper les fichiers sans extension vers** Sélectionnez cette option si vous souhaitez spécifier comment les fichiers sans extension seront gérés par l’IDE.

 **Options de fichier sans extension** Fournit la même liste que l' **éditeur**. Sélectionnez l’éditeur IDE ou le concepteur dans lequel les documents sans extension de fichier s’ouvriront.

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour gérer les modes de l’éditeur](../../ide/how-to-manage-editor-modes.md)
