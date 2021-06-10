---
title: Créer un package de programme d’amorçage localisé | Microsoft Docs
description: Découvrez comment créer des versions localisées du package du programme d’amorçage dans ClickOnce en créant deux fichiers supplémentaires pour chaque paramètre régional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a9d1fc91dcb385a9250dde3adb47c0d9553147f
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877713"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Guide pratique pour créer un package du programme d'amorçage localisé
Après avoir créé un package du programme d’amorçage, vous pouvez créer des versions localisées du package du programme d’amorçage en créant deux fichiers supplémentaires pour chaque paramètre régional : un fichier de termes de contrat de licence logiciel (tel que *EULA. rtf*) et un manifeste de package (*package.xml*).

 Par défaut, Visual Studio 2010 inclut des packages de programme d'amorçage localisés uniquement pour .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 et F# Runtime 4.0. Vous pouvez créer des packages localisés pour d'autres programmes d'amorçage en trois étapes.

1. Créez un dossier nommé d’après le nom des paramètres régionaux dans *\Program Files (x86) \Microsoft SDKs\ClickOnce Bootstrapper\Packages \\ \<BootstrapperPackageName>*.

2. Créez un fichier qui contient les termes du contrat de licence logiciel du package du programme d’amorçage et placez-le dans le nouveau dossier.

3. Créez un manifeste de package nommé *package.xml*, mettez à jour les chaînes et la culture, puis placez le fichier dans le nouveau dossier. Si vous avez déjà créé un programme d’amorçage de Visual Studio dans la langue cible, vous pouvez copier le fichier de *package.xml* Visual Studio et le modifier dans cette étape.

> [!NOTE]
> Si vous utilisez un projet d’installation pour déployer les applications, vous pouvez localiser votre application en changeant la propriété **Localization**.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Pour créer un package de programme d'amorçage localisé

1. Créez un dossier nommé en fonction du nom des paramètres régionaux.

     Sur les ordinateurs 32 bits, créez le dossier dans le dossier *\Program Files\Microsoft SDKs\ClickOnce \\ \<BootstrapperPackageName> \\ Bootstrapper\Packages*

     Sur les ordinateurs 64 bits, créez le dossier dans le dossier *\Program Files (x86) \Microsoft SDKs\ClickOnce \\ \<BootstrapperPackageName> \\ Bootstrapper\Packages*

     Le tableau suivant indique les noms de dossiers qui peuvent correspondre à des paramètres régionaux.

    |Paramètres régionaux|Nom de dossier|
    |------------|-----------------|
    |Chinois (simplifié)|zh-Hans|
    |Chinois (traditionnel)|zh-Hant|
    |Tchèque|cs|
    |Allemand|de|
    |Anglais|en|
    |Espagnol|es|
    |Français|fr|
    |Italien|it|
    |Coréen|ko|
    |Japonais|ja|
    |Polonais|pl|
    |Portugais (Brésil)|pt-br|
    |Russe|ru|
    |Turc|tr|

2. Créez un fichier qui contient les termes du contrat de licence logiciel du package du programme d’amorçage et placez-le dans le nouveau dossier.

3. Créez un manifeste de package nommé *package.xml* et placez-le dans le nouveau dossier. Pour plus d’informations, consultez [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md).

4. Mettez à jour la section `<Strings>` du manifeste du package pour que les chaînes soient dans la langue appropriée en fonction des paramètres régionaux.

5. Changez la valeur de `<String Name="Culture">` pour qu'elle corresponde au nom du dossier.

6. Enregistrez le fichier *package.xml* .

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Pour créer un package de programme d'amorçage pour .NET Framework 3.5 Service Pack 1 localisé en français

1. Créez un dossier nommé *fr*. Le nom du dossier doit correspondre au nom des paramètres régionaux.

     Sur les ordinateurs 32 bits, créez le dossier dans le dossier *\Program Files\Microsoft SDKs\ClickOnce \\ Bootstrapper\Packages\DotNetFX35SP1*

     Sur les ordinateurs 64 bits, créez le dossier dans le dossier *\Program Files (x86) \Microsoft SDKs\ClickOnce \\ Bootstrapper\Packages\DotNetFX35SP1*

2. Placez une version localisée des termes du contrat de licence logiciel dans le dossier *fr* .

3. Copiez le fichier *\Program Files (x86) \Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* dans le dossier *fr* , puis ouvrez le fichier dans le concepteur XML.

4. Mettez à jour la section `<Strings>` du manifeste du package pour que les chaînes d'erreur soient en français.

5. Remplacez la `<String Name="Culture">` valeur par *fr*.

6. Enregistrez le fichier *package.xml* .

>[!NOTE]
> À compter de Visual Studio 2019 Update 7 Release, les packages du programme d’amorçage seront également découverts sous le chemin *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

## <a name="see-also"></a>Voir aussi
- [Créer des packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md)
- [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)
- [Guide pratique pour créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md)