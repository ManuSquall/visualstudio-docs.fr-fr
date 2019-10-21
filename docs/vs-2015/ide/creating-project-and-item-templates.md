---
title: Création de modèles de projet et d’élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 995696dafce64cdcb1fbb11d0788bbe13453c440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619298"
---
# <a name="creating-project-and-item-templates"></a>Création de modèles de projet et d’élément
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles de projet et d'élément [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offrent aux utilisateurs, via des stubs réutilisables, du code de base et des structures qu'ils peuvent utiliser pour leurs propres besoins.

## <a name="visual-studio-templates"></a>Modèles Visual Studio
 L'installation de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inclut également un certain nombre de modèles prédéfinis pour des projets et des éléments. Les modèles d’application Windows Forms et de bibliothèque de classes [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../includes/csprcs-md.md)], disponibles dans la boîte de dialogue **Nouveau projet**, sont des exemples de modèles de projet. Les modèles d’élément installés sont disponibles dans la boîte de dialogue **Ajouter un nouvel élément** et incluent des éléments tels que des fichiers de code, des fichiers XML, des pages HTML et des feuilles de style.

 Ces modèles fournissent un point de départ aux utilisateurs pour commencer à créer des projets ou à développer des projets existants. Les modèles de projet fournissent les fichiers nécessaires à un type de projet particulier, incluent des références d'assembly standard et définissent les propriétés de projet ainsi que les options du compilateur par défaut. Les modèles d'élément peuvent être aussi simples qu'un unique fichier vide doté de l'extension de nom de fichier appropriée, ou aussi complexes qu'un élément à plusieurs fichiers contenant, par exemple, des fichiers de code source avec un code stub, des fichiers d'informations sur le concepteur et des ressources incorporées.

 Outre les modèles installés présents dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, vous pouvez créer vos propres modèles, ou télécharger et utiliser des modèles créés par la communauté. Pour plus d’informations, consultez [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md) et [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Contenu d'un modèle
 Tous les modèles de projet et d'élément, qu'ils soient installés avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou créés par vous, fonctionnent selon les mêmes principes et ont les mêmes contenus. Tous les modèles contiennent les éléments suivants :

- Les fichiers à créer lors de l'utilisation du modèle. Ce sont les fichiers de code source, les ressources incorporées, les fichiers projet, etc.

- Un fichier .vstemplate. Ce fichier contient les métadonnées qui fournissent à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les informations nécessaires pour afficher le modèle dans les boîtes de dialogue **Nouveau projet** et **Ajouter un nouvel élément**, ainsi que pour créer un projet ou un élément à partir du modèle. Pour plus d’informations sur les fichiers .vstemplate, consultez [Paramètres de modèle](../ide/template-parameters.md).

  Lorsque ces fichiers sont compressés dans un fichier .zip et placés dans le dossier approprié, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les affiche automatiquement. Les modèles de projet s’affichent dans la section **Mes modèles** de la boîte de dialogue **Nouveau projet**, et les modèles d’élément s’affichent dans la boîte de dialogue **Ajouter un nouvel élément**. Pour plus d’informations sur les dossiers de modèles, consultez [Guide pratique pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Starter Kits
 Les Starter Kits sont des modèles améliorés qui peuvent être partagés avec d'autres membres de la communauté. Un Starter Kit inclut, parmi d'autres ressources, des exemples de code compilables et une documentation pour aider les utilisateurs à découvrir de nouveaux outils et techniques de programmation tout en générant des applications utiles et réelles. Le contenu et les procédures de base sont identiques, qu'il s'agisse de Starter Kits ou de modèles. Pour plus d’informations, consultez [Guide pratique pour créer des Starter Kits](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Voir aussi
 [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md) [Comment : créer des modèles d’élément](../ide/how-to-create-item-templates.md) [paramètres de modèle](../ide/template-parameters.md) [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md) [Comment : créer des Starter Kits](../ide/how-to-create-starter-kits.md)
