---
title: Résoudre les problèmes de découverte de modèles dans Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323998"
---
# <a name="troubleshooting-template-installation"></a>Résolution des problèmes d’installation du modèle

Si vous rencontrez des problèmes de déploiement de vos modèles de projet ou un élément, vous pouvez activer la journalisation des Diagnostics.

::: moniker range="vs-2017"

1. Créez un fichier pkgdef dans le *Common7\IDE\CommonExtensions* dossier pour votre installation. Par exemple, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Créez un fichier pkgdef dans le *Common7\IDE\CommonExtensions* dossier pour votre installation. Par exemple, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Ajoutez le code suivant au fichier pkgdef :

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Ouvrir un [invite de commandes développeur](/dotnet/framework/tools/developer-command-prompt-for-vs) pour votre installation et l’exécutez `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Démarrez Visual Studio et lancer les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle.

   Le journal de modèle s’affiche désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). L’initialisation de chaque arborescence de modèle ajoute des entrées dans ce fichier journal.

::: moniker-end

::: moniker range=">=vs-2019"

4. Démarrez Visual Studio et lancer les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle.

   Le journal de modèle s’affiche désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). L’initialisation de chaque arborescence de modèle ajoute des entrées dans ce fichier journal.

::: moniker-end

Le fichier journal contient les colonnes suivantes :

- **FullPathToTemplate**, qui a les valeurs suivantes :

    - 1 pour le déploiement basé sur les manifestes

    - 0 pour le déploiement basé sur le disque

- **TemplateFileName**

- Autres propriétés de modèle

> [!NOTE]
> Pour désactiver la journalisation, supprimez le fichier pkgdef, ou modifiez la valeur de `EnableTemplateDiscoveryLog` à `dword:00000000`, puis exécutez `devenv /updateConfiguration` à nouveau.

## <a name="see-also"></a>Voir aussi

- [Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)