---
title: Guide pratique pour ajouter un fichier app.config à un projet dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b2182b0175d57d7283e63bdf408249fa7566da00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Guide pratique pour ajouter un fichier de configuration d’application à un projet C#

En ajoutant un fichier de configuration d’application (un fichier *app.config*) à un projet C#, vous pouvez personnaliser la façon dont le CLR (Common Language Runtime) localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration d’application, consultez [Méthode de localisation des assemblys par le runtime (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Les applications UWP ne contiennent pas de fichier *app.config*.

Quand vous générez votre projet, l’environnement de développement copie automatiquement votre fichier *app.config*, modifie le nom de fichier de la copie pour qu’il corresponde à votre fichier exécutable, puis déplace la copie dans le répertoire **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Pour ajouter un fichier de configuration d’application à un projet C#

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

1. Développez **Installé** > **Éléments Visual C#**, puis choisissez le modèle **Fichier de configuration de l’application**.

1. Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter**.

     Un fichier nommé *app.config* est ajouté à votre projet.

## <a name="see-also"></a>Voir aussi

- [Gérer les paramètres d’application (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma des fichiers de configuration (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurer les applications (.NET Framework)](/dotnet/framework/configure-apps/index)