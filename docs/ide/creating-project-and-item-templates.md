---
title: Modèles pour les projets et les fichiers
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30a20e5810d5c361fddf8cd934863fcb1186b5d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793450"
---
# <a name="project-and-item-templates"></a>Modèles de projet et d’élément

Les modèles de projet et d’élément offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu’ils peuvent personnaliser selon leurs propres besoins.

## <a name="visual-studio-templates"></a>modèles Visual Studio

L’installation de Visual Studio inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments. Ces modèles, comme les modèles **Application web ASP.NET** et **Bibliothèque de classes**, sont disponibles quand vous créez un projet. Les modèles d’élément, comme des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style, apparaissent dans la boîte de dialogue **Ajouter un nouvel élément**.

Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants. Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut. La complexité des modèles d’éléments peut aller d’un fichier unique vide ayant une extension de fichier particulière à plusieurs fichiers de code source contenant du code stub, des fichiers d’informations sur le concepteur et des ressources incorporées.

Vous pouvez utiliser des modèles installés, créer vos propres modèles, ou bien télécharger et utiliser des modèles créés par la communauté. Pour plus d'informations, voir [Procédure : créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenu d’un modèle

Tous les modèles de projet et d’élément, qu’ils soient installés avec Visual Studio ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus. Tous les modèles contiennent les éléments suivants :

- Les fichiers à créer lors de l'utilisation du modèle. Il s’agit des fichiers de code source, des ressources incorporées, des fichiers projet, etc.

::: moniker range="vs-2017"

- Un fichier *.vstemplate* contenant les métadonnées nécessaires pour créer un projet ou un élément à partir du modèle, et pour afficher le modèle dans les fenêtres **Nouveau projet** et **Ajouter un nouvel élément**.

::: moniker-end

::: moniker range=">=vs-2019"

- Un fichier *.vstemplate* contenant les métadonnées nécessaires pour créer un projet ou un élément à partir du modèle, et pour afficher le modèle dans la page **Créer un projet** ou dans la boîte de dialogue **Ajouter un nouvel élément**.

::: moniker-end

   Pour plus d’informations sur les fichiers *.vstemplate*, consultez [Paramètres de modèle](../ide/template-parameters.md).

Quand ces fichiers sont compressés dans un fichier *.zip* et placés dans le dossier approprié, Visual Studio les affiche automatiquement aux emplacements suivants :

::: moniker range="vs-2017"

- Les modèles de projet apparaissent dans la fenêtre **Nouveau projet**.

::: moniker-end

::: moniker range=">=vs-2019"

- Les modèles de projet apparaissent dans la page **Créer un projet**.

::: moniker-end

- Les modèles d’élément apparaissent dans la fenêtre **Ajouter un nouvel élément**.

Pour plus d’informations sur les dossiers de modèles, consultez [Guide pratique pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)
- [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)