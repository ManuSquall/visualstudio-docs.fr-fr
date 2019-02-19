---
title: Guide de l’administrateur Help Viewer │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e0f63555cbda069c3db0a3a1d5819292fc3cda14
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799703"
---
# <a name="help-viewer-administrator-guide"></a>Guide de l'administrateur Help Viewer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visionneuse d’aide vous permet de gérer les installations locales d’aide pour les environnements réseau avec ou sans accès à Internet. Le contenu d’aide locale est configuré sur la base de l’ordinateur. Par défaut, les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour leur installation d’aide locale.  
  
 Si votre environnement réseau permet aux clients d’accéder à Internet, la visionneuse d’aide vous permet d’utiliser les scripts de ligne de commande pour déployer le contenu d’aide locale depuis Internet.  
  
 Si votre environnement réseau ne permet pas aux clients d’accéder à Internet, la visionneuse d’aide peut déployer le contenu d’aide locale depuis un intranet ou un partage réseau. Vous pouvez également désactiver les options d’aide de l’IDE de Visual Studio, telles que l’aide en ligne ou hors connexion, l’installation du contenu au premier lancement de l’IDE, la désignation d’un service de contenu intranet, et la gestion de contenu à l’aide de substitutions de clés de Registre.  
  
 La syntaxe de base est la suivante :  
  
 \<*chemin d’accès au*> \HlpCtntmgr.exe /operation \< *argument*> /catalogname \< *nom*> /locale \< *deparamètresrégionaux*>/SourceUri \< *chemin d’accès .msha ou URL*>  
  
 Pour plus d’informations sur la syntaxe de ligne de commande HlpCtntMgr.exe, consultez [Arguments de ligne de commande pour Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Pour plus d’informations sur la création de contenu, la création d’un point de terminaison de service intranet et les types d’activités similaires, consultez le Kit de développement logiciel (SDK) de la visionneuse d’aide.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Déploiement de contenu d’aide locale à partir d’Internet  
 Vous pouvez utiliser le service de module de ressources MSDN pour déployer le contenu d’aide locale d’Internet aux ordinateurs clients. Utilisez la syntaxe suivante :  
  
 \\<*chemin vers*>\v2.2\HlpCtntmgr.exe /operation \<*nom*> /catalogname \<*nomcatalogue*> /locale \<*paramètres régionaux*>  
  
 Pour plus d’informations sur la syntaxe de ligne de commande HlpCtntMgr.exe, consultez [Arguments de ligne de commande pour Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Configuration requise :  
  
- Les ordinateurs clients doivent avoir accès à Internet.  
  
- Les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour, ajouter ou supprimer le contenu d’aide locale une fois celui-ci installé.  
  
  Avertissements :  
  
- La source par défaut de l’aide sera toujours en ligne.  
  
  > [!TIP]
  >  Vous pouvez modifier la source par défaut de l’aide en modifiant la clé de Registre HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Pour plus d’informations, consultez [Substitutions dans Help Content Manager](../ide/help-content-manager-overrides.md).  
  
- Les clients seront toujours invités à installer le contenu d’aide de base lors du premier démarrage de Visual Studio. Vous pouvez désactiver cette invite en modifiant la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant installe le contenu en anglais pour Visual Studio sur un ordinateur client.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Pour installer le contenu en anglais à partir d’Internet  
  
1.  Choisissez **Démarrer**, puis **Exécuter**.  
  
2.  Tapez la commande suivante :  
  
     C:\Program Files (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us  
  
3.  Appuyez sur Entrée.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Déploiement du contenu d’aide locale préinstallé sur les ordinateurs clients  
 Vous pouvez installer un ensemble de contenu à partir d’une source en ligne sur un ordinateur, puis copier cet ensemble de contenu installé sur d’autres ordinateurs.  
  
 Configuration requise :  
  
- L’ordinateur sur lequel vous installez l’ensemble du contenu doit avoir accès à Internet.  
  
- Les utilisateurs doivent disposer des droits d’administrateur pour mettre à jour, ajouter ou supprimer le contenu d’aide locale une fois celui-ci installé.  
  
  > [!TIP]
  >  Si les utilisateurs ne disposent pas des droits d’administrateur, nous vous recommandons de désactiver l’onglet Gérer le contenu de la visionneuse d’aide. Pour plus d’informations, consultez [Substitutions dans Help Content Manager](../ide/help-content-manager-overrides.md).  
  
  Avertissements :  
  
- Si les utilisateurs ne disposent pas des droits d’administrateur, nous vous recommandons de désactiver l’onglet Gérer le contenu de la visionneuse d’aide. Pour plus d’informations, consultez [Substitutions dans Help Content Manager](../ide/help-content-manager-overrides.md).  
  
- La source par défaut de l’aide sera toujours en ligne.  
  
- Les clients seront toujours invités à installer le contenu d’aide de base lors du premier démarrage de Visual Studio. Pour plus d’informations, consultez [Substitutions dans Help Content Manager](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>Créer l’ensemble de contenu  
 Avant de pouvoir créer l’ensemble de contenu de base, vous devez d’abord désinstaller tout le contenu local de Visual Studio sur l’ordinateur cible.  
  
##### <a name="to-uninstall-local-help"></a>Pour désinstaller l’aide locale  
  
1. Dans Help Viewer, choisissez l’onglet **Gérer le contenu**.  
  
2. Sous **Documentation disponible**, accédez à l’ensemble de documents de Visual Studio.  
  
3. Choisissez **Supprimer** à côté de chaque sous-élément.  
  
4. Sélectionnez **Démarrer** pour désinstaller.  
  
5. Accédez à *n*:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 et vérifiez que le dossier contient uniquement le fichier catalogType.xml.  
  
   Une fois que vous avez supprimé tout le contenu local installé précédemment à l’aide de Visual Studio, vous êtes prêt à télécharger l’ensemble de contenu de base.  
  
##### <a name="to-download-the-content"></a>Pour télécharger le contenu  
  
1. Dans Help Viewer, choisissez l’onglet **Gérer le contenu**.  
  
2. Sous **Documentation disponible**, accédez aux ensembles de documents à télécharger, puis sélectionnez **Ajouter**.  
  
3. Choisissez **Démarrer**.  
  
   Vous devez ensuite créer un package du contenu pour qu’il puisse être déployé sur les ordinateurs clients.  
  
##### <a name="to-package-the-content"></a>Pour créer un package du contenu  
  
1.  Créez un répertoire pour copier le contenu en vue d’un déploiement ultérieur.  
  
     Par exemple : c:\VS12Help.  
  
2.  Ouvrez cmd.exe avec des autorisations d’administrateur.  
  
3.  Accédez au dossier créé à l’étape 1.  
  
4.  Tapez la commande suivante :  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*nomdossier*>\ /y /e /k /o  
  
     Exemple : `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`.  
  
### <a name="deploying-the-content"></a>Déploiement du contenu  
  
##### <a name="to-deploy-the-content"></a>Pour déployer le contenu  
  
1.  Créez un partage réseau et copiez le contenu d’aide à cet emplacement.  
  
     Par exemple, copiez le contenu du dossier c:\VS12Help dans \\\monserveur\VS12Help.  
  
2.  Créez un fichier .bat pour contenir le script de déploiement du contenu d’aide. Comme le client est susceptible de ne pas pouvoir lire les fichiers en cours de suppression dans le cadre de l’émission, vous devez désactiver le client avant d’émettre des mises à jour.  
  
     Par exemple :  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Exécutez le fichier bat sur les ordinateurs locaux sur lesquels le contenu d’aide doit être installé.  
  
## <a name="see-also"></a>Voir aussi  
 [Arguments de ligne de commande pour Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Substitutions Help Content Manager](../ide/help-content-manager-overrides.md)
