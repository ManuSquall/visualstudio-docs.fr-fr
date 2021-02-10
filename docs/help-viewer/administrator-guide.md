---
title: Guide de l’administrateur Help Viewer
description: Lisez le Guide de l’administrateur Microsoft Help Viewer. Déployez le contenu de l’aide locale à partir d’Internet ou déployez le contenu d’aide locale préinstallé sur les ordinateurs clients.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e52b03b01f53a8064dc6ec691f751c86266af6a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944301"
---
# <a name="help-viewer-administrator-guide"></a>Guide de l’administrateur Help Viewer

La visionneuse d’aide vous permet de gérer les installations locales d’aide pour les environnements réseau avec ou sans accès à Internet. Le contenu d’aide locale est configuré sur la base de l’ordinateur. Par défaut, les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour leur installation d’aide locale.

Si votre environnement réseau permet aux clients d’accéder à Internet, vous pouvez utiliser l’exécutable **Help Content Manager** pour déployer le contenu de l’aide locale à partir d’Internet. Pour plus d’informations sur *HlpCtntMgr.exe* syntaxe de ligne de commande, consultez [arguments de ligne de commande pour Help Content Manager](../help-viewer/command-line-arguments.md).

Pour obtenir des informations sur la création de contenu, la création d’un point de terminaison de service intranet et les types d’activités similaires, consultez [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Si votre environnement réseau n’offre pas de connectivité Internet, Help Viewer peut déployer le contenu de l’aide locale à partir de l’intranet ou d’un partage réseau. Vous pouvez également désactiver des options de l’aide de l’IDE de Visual Studio en utilisant des [substitutions de clé de Registre](../help-viewer/behavior-overrides.md) pour les fonctionnalités suivantes :

- Aide en ligne et aide hors connexion

- Installation du contenu au premier démarrage de l’IDE

- Spécification d’un service de contenu intranet

- Gestion du contenu

## <a name="deploy-local-help-content-from-the-internet"></a>Déployer le contenu de l’aide locale à partir d’Internet

Vous pouvez utiliser **Help Content Manager** (*HlpCtntMgr.exe*) pour déployer le contenu de l’aide locale depuis Internet sur des ordinateurs clients. Utilisez la syntaxe suivante :

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Pour plus d’informations sur *HlpCtntMgr.exe* syntaxe de ligne de commande, consultez [arguments de ligne de commande pour Help Content Manager](../help-viewer/command-line-arguments.md).

Conditions requises :

- Les ordinateurs clients doivent avoir accès à Internet.

- Les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour, ajouter ou supprimer le contenu d’aide locale une fois celui-ci installé.

Avertissements :

- La source par défaut de l’aide sera toujours en ligne.

### <a name="example"></a>Exemple

L’exemple suivant installe le contenu en anglais pour Visual Studio sur un ordinateur client.

#### <a name="to-install-english-content-from-the-internet"></a>Pour installer le contenu en anglais à partir d’Internet

1. Choisissez **Démarrer**, puis **Exécuter**.

2. Tapez la commande suivante :

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3. Appuyez sur **Entrée**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Déployer le contenu de l’aide locale préinstallé sur les ordinateurs clients

Vous pouvez installer un ensemble de contenu à partir d’une source en ligne sur un ordinateur, puis copier cet ensemble de contenu installé sur d’autres ordinateurs.

Conditions requises :

- L’ordinateur sur lequel vous installez l’ensemble du contenu doit avoir accès à Internet.

- Les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour, ajouter ou supprimer le contenu d’aide locale une fois celui-ci installé.

    > [!TIP]
    > Si les utilisateurs ne disposent pas de droits d’administrateur, nous vous recommandons de désactiver l’onglet **Gérer le contenu** dans Help Viewer. Pour plus d’informations, consultez [l’aide sur les remplacements du gestionnaire de contenu](../help-viewer/behavior-overrides.md).

Avertissements :

- La source par défaut de l’aide sera toujours en ligne.

### <a name="create-the-content-set"></a>Créer l’ensemble de contenu

Avant de pouvoir créer l’ensemble de contenu de base, vous devez d’abord désinstaller tout le contenu local de Visual Studio sur l’ordinateur cible.

#### <a name="to-uninstall-local-help"></a>Pour désinstaller l’aide locale

1. Dans Help Viewer, choisissez l’onglet **Gérer le contenu**.

2. Accédez à l’ensemble de documents Visual Studio.

3. Choisissez **Supprimer** à côté de chaque sous-élément.

4. Choisissez **Mettre à jour** pour désinstaller l’aide locale.

5. Accédez à *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* et vérifiez que le dossier contient uniquement le fichier *catalogType.xml*.

   Une fois que vous avez supprimé tout le contenu local installé précédemment à l’aide de Visual Studio, vous êtes prêt à télécharger l’ensemble de contenu de base.

#### <a name="to-download-the-content"></a>Pour télécharger le contenu

1. Dans Help Viewer, choisissez l’onglet **Gérer le contenu**.

2. Sous **Documentation recommandée** ou **Documentation disponible**, accédez aux ensembles de documents à télécharger, puis choisissez **Ajouter**.

3. Choisissez **Mettre à jour**.

Vous devez ensuite créer un package du contenu pour qu’il puisse être déployé sur les ordinateurs clients.

#### <a name="to-package-the-content"></a>Pour créer un package du contenu

1. Créez un répertoire pour copier le contenu en vue d’un déploiement ultérieur. Par exemple : *C:\VSHelp*.

2. Ouvrez *cmd.exe* avec les autorisations d’administrateur.

3. Accédez au dossier créé à l’étape 1.

4. Tapez la commande suivante :

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Par exemple : `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Déployer le contenu

1. Créez un partage réseau et copiez le contenu d’aide à cet emplacement.

     Par exemple, copiez le contenu dans *C:\VSHelp* dans *\\ \myserver\VSHelp*.

2. Créez un fichier *.bat* qui va contenir le script de déploiement du contenu d’aide. Comme le client est susceptible de ne pas pouvoir lire les fichiers en cours de suppression dans le cadre de l’émission, vous devez désactiver le client avant d’émettre des mises à jour. Par exemple :

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Exécutez le fichier *. bat* sur les ordinateurs locaux sur lesquels vous souhaitez installer le contenu de l’aide.

## <a name="see-also"></a>Voir aussi

- [Arguments de ligne de commande pour Help Content Manager](../help-viewer/command-line-arguments.md)
- [Remplacements de Help Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
- [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)