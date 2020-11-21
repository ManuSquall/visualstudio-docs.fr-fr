---
title: Modèles pour les projets et les fichiers
description: Découvrez comment les modèles de projet et d’élément fournissent des stubs réutilisables qui fournissent aux utilisateurs un code et une structure de base.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f7ce85818e0cce4a6e78f5e2ec5901452ebd83f9
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006300"
---
# <a name="project-and-item-templates"></a>Modèles de projet et d’élément

Les modèles de projet et d’élément offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu’ils peuvent personnaliser selon leurs propres besoins.

## <a name="visual-studio-templates"></a>modèles Visual Studio

L’installation de Visual Studio inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments. Ces modèles, comme les modèles **Application web ASP.NET** et **Bibliothèque de classes**, sont disponibles quand vous créez un projet. Les modèles d’élément, comme des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style, apparaissent dans la boîte de dialogue **Ajouter un nouvel élément**.

Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants. Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut. La complexité des modèles d’éléments peut aller d’un fichier unique vide ayant une extension de fichier particulière à plusieurs fichiers de code source contenant du code stub, des fichiers d’informations sur le concepteur et des ressources incorporées.

Vous pouvez utiliser des modèles installés, créer vos propres modèles, ou bien télécharger et utiliser des modèles créés par la communauté. Pour plus d’informations, consultez [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Comment : créer des modèles d’élément](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenu d’un modèle

Tous les modèles de projet et d’élément, qu’ils soient installés avec Visual Studio ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus. Tous les modèles contiennent les éléments suivants :

- Les fichiers à créer lors de l'utilisation du modèle. Il s’agit des fichiers de code source, des ressources incorporées, des fichiers projet, etc.

::: moniker range="vs-2017"

- Un fichier *.vstemplate* contenant les métadonnées nécessaires pour créer un projet ou un élément à partir du modèle, et pour afficher le modèle dans les fenêtres **Nouveau projet** et **Ajouter un nouvel élément**.

::: moniker-end

::: moniker range=">=vs-2019"

- Un fichier *.vstemplate* contenant les métadonnées nécessaires pour créer un projet ou un élément à partir du modèle, et pour afficher le modèle dans la page **Créer un projet** ou dans la boîte de dialogue **Ajouter un nouvel élément**.

::: moniker-end

   Pour plus d’informations sur les fichiers *.vstemplate*, consultez [Paramètres de balise](template-tags.md) and [Paramètres de modèle](../ide/template-parameters.md).

Quand ces fichiers sont compressés dans un fichier *.zip* et placés dans le dossier approprié, Visual Studio les affiche automatiquement aux emplacements suivants :

::: moniker range="vs-2017"

- Les modèles de projet apparaissent dans la fenêtre **Nouveau projet**.

::: moniker-end

::: moniker range=">=vs-2019"

- Les modèles de projet apparaissent dans la page **Créer un projet**.

::: moniker-end

- Les modèles d’élément apparaissent dans la fenêtre **Ajouter un nouvel élément**.

Pour plus d’informations sur les dossiers de modèles, consultez Guide pratique [pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi

- [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md)
- [Comment : créer des modèles d’élément](../ide/how-to-create-item-templates.md)
- [Balises de modèle](template-tags.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Personnaliser des modèles](../ide/customizing-project-and-item-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
