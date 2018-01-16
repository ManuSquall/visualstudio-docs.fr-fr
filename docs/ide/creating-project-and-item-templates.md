---
title: "Modèles Visual Studio pour les projets et les fichiers | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>Modèles de projet et d’élément

Les modèles de projet et d’élément offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu’ils peuvent personnaliser selon leurs propres besoins.

## <a name="visual-studio-templates"></a>Modèles Visual Studio

L’installation de Visual Studio inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments. Par exemple, les modèles **Application Windows Forms** et **Bibliothèque de classes**, figurant dans la boîte de dialogue **Nouveau projet**, sont des modèles de projet. Les modèles d’élément figurent dans la boîte de dialogue **Ajouter un nouvel élément** et contiennent des éléments tels que des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style.

Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants. Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut. Les modèles d’élément peuvent être aussi simples qu’un unique fichier vide portant une extension de fichier particulière ou aussi complexes qu’un élément à plusieurs fichiers contenant, par exemple, des fichiers de code source avec un code stub, des fichiers d’informations sur le concepteur et des ressources incorporées.

En plus des modèles installés présents dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, vous pouvez créer vos propres modèles, ou bien télécharger et utiliser des modèles créés par la communauté. Pour plus d’informations, consultez [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenu d’un modèle

Tous les modèles de projet et d’élément, qu’ils soient installés avec Visual Studio ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus. Tous les modèles contiennent les éléments suivants :

- Les fichiers à créer lors de l'utilisation du modèle. Ce sont les fichiers de code source, les ressources incorporées, les fichiers projet, etc.

- Un fichier .vstemplate. Ce fichier contient les métadonnées qui fournissent les informations nécessaires pour afficher le modèle dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, ainsi que pour créer un projet ou un élément à partir du modèle. Pour plus d’informations sur les fichiers .vstemplate, consultez [Paramètres de modèle](../ide/template-parameters.md).

Lorsque ces fichiers sont compressés dans un fichier .zip et placés dans le dossier approprié, Visual Studio les affiche automatiquement aux emplacements suivants :

- Les modèles de projet s’affichent dans la boîte de dialogue **Nouveau projet**.

- Les modèles d’élément s’affichent dans la boîte de dialogue **Ajouter un nouvel élément**.

Pour plus d’informations sur les dossiers de modèles, consultez [Guide pratique pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Starter Kits

Les Starter Kits sont des modèles améliorés qui peuvent être partagés avec d'autres membres de la communauté. Un Starter Kit inclut, parmi d'autres ressources, des exemples de code compilables et une documentation pour aider les utilisateurs à découvrir de nouveaux outils et techniques de programmation tout en générant des applications utiles et réelles. Le contenu et les procédures de base sont identiques, qu'il s'agisse de Starter Kits ou de modèles. Pour plus d’informations, consultez [Guide pratique pour créer des Starter Kits](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)  
[Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md)  
[Paramètres de modèle](../ide/template-parameters.md)  
[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)  
[Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)