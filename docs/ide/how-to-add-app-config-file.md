---
title: Guide pratique pour ajouter un fichier app.config à un projet
description: Découvrez comment ajouter un fichier app.config à un projet C# pour personnaliser la façon dont le common language runtime localise et charge les fichiers d’assembly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e9280451d7841755cb3085726843bf6fc1443f8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948281"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Guide pratique pour ajouter un fichier de configuration d’application à un projet C#

En ajoutant un fichier de configuration d’application (un fichier *app.config*) à un projet C#, vous pouvez personnaliser la façon dont le CLR (Common Language Runtime) localise et charge les fichiers d’assembly. Pour plus d’informations sur les fichiers de configuration d’application, consultez [Méthode de localisation des assemblys par le runtime (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Les applications UWP ne contiennent pas de fichier *app.config*.

Quand vous générez votre projet, l’environnement de développement copie automatiquement votre fichier *app.config*, modifie le nom de fichier de la copie pour qu’il corresponde à votre fichier exécutable, puis déplace la copie dans le répertoire **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Pour ajouter un fichier de configuration d’application à un projet C#

1. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

1. Développez   >  **éléments Visual C#** installés, puis choisissez le modèle **fichier de configuration** de l’application.

1. Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter**.

     Un fichier nommé *app.config* est ajouté à votre projet.

## <a name="see-also"></a>Voir aussi

- [Gérer les paramètres d’application (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schéma des fichiers de configuration (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurer les applications (.NET Framework)](/dotnet/framework/configure-apps/index)
