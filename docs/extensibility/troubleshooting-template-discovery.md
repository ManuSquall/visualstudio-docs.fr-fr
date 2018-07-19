---
title: Résoudre les problèmes de détection de modèle dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136726"
---
# <a name="troubleshooting-template-installation"></a>Résolution des problèmes d’installation du modèle

Si vous rencontrez des problèmes de déploiement de vos modèles de projet ou un élément, vous pouvez activer la journalisation des Diagnostics.

1. Créer un fichier pkgdef dans le dossier Common7\IDE\CommonExtensions pour votre installation (par exemple, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) avec le contenu suivant :

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Ouvrez un « invite de commandes développeur » pour votre installation en le recherchant dans la recherche Windows et exécutez `devenv /updateConfiguration`.

1. Démarrez Visual Studio et lancer les boîtes de dialogue Nouveau projet et un nouvel élément pour initialiser les deux arborescences du modèle. Le journal de modèle apparaît désormais dans **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid correspond à l’ID d’installation de votre instance de Visual Studio). L’initialisation de chaque arborescence de modèle ajoute des entrées dans ce fichier journal.

Le fichier journal contient les colonnes suivantes :

- **FullPathToTemplate**, qui a les valeurs suivantes :

    - 1 basé sur les manifestes de déploiement

    - 0 pour le déploiement basé sur le disque

- **TemplateFileName**

- Autres propriétés de modèle

> [!NOTE]
> Pour désactiver la journalisation, supprimez le fichier pkgdef, ou modifiez la valeur de `EnableTemplateDiscoveryLog` à `dword:00000000`, puis exécutez `devenv /updateConfiguration` à nouveau.

## <a name="see-also"></a>Voir aussi

[Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)