---
title: Résoudre les problèmes de découverte de modèles dans Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836151"
---
# <a name="troubleshooting-template-installation"></a>Résolution des problèmes d’installation du modèle

Si vous rencontrez des problèmes de déploiement de vos modèles de projet ou un élément, vous pouvez activer la journalisation des Diagnostics.

1. Créez un fichier pkgdef dans le dossier Common7\IDE\CommonExtensions pour votre installation (par exemple, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) avec le contenu suivant :

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Ouvrez une « invite de commande développeur » pour votre installation en le recherchant dans la recherche de Windows et exécutez `devenv /updateConfiguration`.

1. Démarrez Visual Studio et lancer les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle. Le journal de modèle s’affiche désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). L’initialisation de chaque arborescence de modèle ajoute des entrées dans ce fichier journal.

Le fichier journal contient les colonnes suivantes :

- **FullPathToTemplate**, qui a les valeurs suivantes :

    - 1 pour le déploiement basé sur les manifestes

    - 0 pour le déploiement basé sur le disque

- **TemplateFileName**

- Autres propriétés de modèle

> [!NOTE]
> Pour désactiver la journalisation, supprimez le fichier pkgdef, ou modifiez la valeur de `EnableTemplateDiscoveryLog` à `dword:00000000`, puis exécutez `devenv /updateConfiguration` à nouveau.

## <a name="see-also"></a>Voir aussi

[Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)