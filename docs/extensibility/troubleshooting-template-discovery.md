---
title: Résoudre les problèmes de découverte de modèles dans Visual Studio | Microsoft Docs
description: Découvrez comment activer la journalisation des diagnostics pour résoudre les problèmes de déploiement de projets et de modèles personnalisés dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff864e1a244d058b2c5ec1de33d116cfdcfe22db
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716044"
---
# <a name="troubleshooting-template-installation"></a>Dépannage de l’installation du modèle

Si vous rencontrez des problèmes lors du déploiement de vos modèles de projet ou d’élément, vous pouvez activer la journalisation des Diagnostics.

::: moniker range="vs-2017"

1. Créez un fichier pkgdef dans le dossier *Common7\IDE\CommonExtensions* de votre installation. Par exemple, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Créez un fichier pkgdef dans le dossier *Common7\IDE\CommonExtensions* de votre installation. Par exemple, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Ajoutez le code suivant au fichier pkgdef :

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Ouvrez une [invite de commandes développeur](/dotnet/framework/tools/developer-command-prompt-for-vs) pour votre installation et exécutez `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Ouvrez Visual Studio et lancez les boîtes de dialogue Nouveau projet et nouvel élément pour initialiser les deux arborescences de modèles.

   Le journal de modèle apparaît désormais dans **%LocalAppData%\Microsoft\VisualStudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId correspond à l’ID d’installation de votre instance de Visual Studio). Chaque initialisation d’arborescence de modèle ajoute des entrées à ce journal.

::: moniker-end

::: moniker range=">=vs-2019"

4. Ouvrez Visual Studio et lancez les boîtes de dialogue **créer un nouveau projet** et **nouvel élément** pour initialiser les deux arborescences de modèles.

   Le journal de modèle apparaît désormais dans **%LocalAppData%\Microsoft\VisualStudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId correspond à l’ID d’installation de votre instance de Visual Studio). Chaque initialisation d’arborescence de modèle ajoute des entrées à ce journal.

::: moniker-end

Le fichier journal contient les colonnes suivantes :

- **FullPathToTemplate**, qui a les valeurs suivantes :

  - 1 pour un déploiement basé sur un manifeste

  - 0 pour le déploiement sur disque

- **TemplateFileName**

- Autres propriétés de modèle

> [!NOTE]
> Pour désactiver la journalisation, supprimez le fichier pkgdef ou modifiez la valeur de `EnableTemplateDiscoveryLog` en `dword:00000000` , puis réexécutez `devenv /updateConfiguration` .

## <a name="see-also"></a>Voir aussi

- [Création de modèles de projet et d’élément personnalisés](creating-custom-project-and-item-templates.md)
- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
