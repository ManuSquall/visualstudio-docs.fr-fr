---
title: "Guide pratique pour ajouter un fichier app.config à un projet dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Comment : ajouter un fichier de configuration d'application à un projet C#

En ajoutant un fichier de configuration d’application (fichier app.config) à un projet C#, vous pouvez personnaliser la façon dont le CLR (Common Language Runtime) localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration d’application, consultez [Méthode de localisation des assemblys par le runtime (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Les applications UWP ne contiennent aucun fichier app.config.

Lorsque vous générez votre projet, l’environnement de développement copie automatiquement votre fichier app.config, modifie le nom de fichier de la copie pour qu’il corresponde à votre fichier exécutable, puis déplace la copie vers le répertoire **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Pour ajouter un fichier de configuration d’application à un projet C#

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

1. Développez **Installé** > **Éléments Visual C#**, puis choisissez le modèle **Fichier de configuration de l’application**.

3. Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter**.

     A file named app.config is added to your project.

## <a name="see-also"></a>Voir aussi

[Gestion des paramètres d’une application (.NET)](../ide/managing-application-settings-dotnet.md)  
[Schéma des fichiers de configuration (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Configuration d'applications (.NET Framework)](/dotnet/framework/configure-apps/index)