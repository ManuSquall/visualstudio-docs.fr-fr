---
title: Guide pratique pour ajouter un fichier app.config à un projet
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4c34a0d8f2a04718ff409ed5256eea1c07287f95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992475"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procédure : ajouter un fichier de configuration d’application à un projet C#

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