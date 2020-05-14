---
title: Découverte de modèles de dépannage dans Visual Studio (fr) Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698935"
---
# <a name="troubleshooting-template-installation"></a>Installation de modèle de dépannage

Si vous rencontrez des problèmes de déploiement de votre projet ou de vos modèles d’objets, vous pouvez activer l’enregistrement diagnostique.

::: moniker range="vs-2017"

1. Créez un fichier pkgdef dans le dossier *Common7-IDE-CommonExtensions* pour votre installation. Par exemple, *les fichiers C:-Program (x86) -Microsoft Visual Studio-2017-Enterprise-Common7-IDE-CommonExtensions-EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Créez un fichier pkgdef dans le dossier *Common7-IDE-CommonExtensions* pour votre installation. Par exemple, *les fichiers C:-Program (x86) -Microsoft Visual Studio-2019-Enterprise-Common7-IDE-CommonExtensions-EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Ajouter ce qui suit au fichier pkgdef :

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Ouvrez une invite de commande `devenv /updateConfiguration`de [développeur](/dotnet/framework/tools/developer-command-prompt-for-vs) pour votre installation et exécutez.

::: moniker range="vs-2017"

4. Ouvrez Visual Studio et lancez les boîtes de dialogue New Project et New Item pour initialiser les deux arbres modèles.

   Le journal de modèle apparaît maintenant dans **%LOCALAPPDATA%-Microsoft-VisualStudio-15.0[instanceid]-VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). Chaque modélisation de l’arbre appendule les entrées à ce journal.

::: moniker-end

::: moniker range=">=vs-2019"

4. Ouvrez Visual Studio et **lancez** le Créer un nouveau projet et des boîtes de dialogue **New Item** pour initialiser les deux arbres modèles.

   Le journal de modèle apparaît maintenant dans **%LOCALAPPDATA%-Microsoft-VisualStudio-16.0[instanceid]-VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). Chaque modélisation de l’arbre appendule les entrées à ce journal.

::: moniker-end

Le fichier journal contient les colonnes suivantes :

- **FullPathToTemplate**, qui a les valeurs suivantes:

  - 1 pour le déploiement à base de manifestes

  - 0 pour le déploiement sur disque

- **TemplateFileName (en)**

- Autres propriétés de modèle

> [!NOTE]
> Pour désactiver l’enregistrement, soit supprimer le fichier pkgdef, ou changer la valeur de `EnableTemplateDiscoveryLog` , puis exécuter `dword:00000000` `devenv /updateConfiguration` à nouveau.

## <a name="see-also"></a>Voir aussi

- [Création de modèles de projets et d’objets personnalisés](creating-custom-project-and-item-templates.md)
