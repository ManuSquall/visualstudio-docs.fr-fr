---
title: Installation d’une application Shell isolée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a077173a0d095ee10cc1fa16da3db1f3744dafa8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301157"
---
# <a name="installing-an-isolated-shell-application"></a>Installation d’une application avec Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour installer une application Shell, vous devez effectuer les étapes suivantes.  
  
- Préparez votre solution.  
  
- Créez un package Windows Installer (MSI) pour votre application.  
  
- Créez un programme d’amorçage du programme d’installation.  
  
  Tout l’exemple de code de ce document provient de l' [exemple de déploiement d’environnement](https://go.microsoft.com/fwlink/?LinkId=262245), que vous pouvez télécharger à partir de la Galerie de code sur le site Web MSDN. L’exemple montre les résultats de l’exécution de chacune de ces étapes.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter les procédures décrites dans cette rubrique, les outils suivants doivent être installés sur votre ordinateur.  
  
- Le kit de développement logiciel Visual Studio  
  
- [Ensemble d’outils XML Windows Installer](https://go.microsoft.com/fwlink/?LinkId=82720) version 3,6  
  
  L’exemple requiert également le kit de développement logiciel (SDK) de visualisation et de modélisation Microsoft, ce qui n’est pas obligatoire pour tous les Shell.  
  
## <a name="preparing-your-solution"></a>Préparation de votre solution  
 Par défaut, les modèles d’environnement s’appuient sur des packages VSIX, mais ce comportement est principalement destiné à des fins de débogage. Lorsque vous déployez une application Shell, vous devez utiliser des packages MSI pour permettre l’accès au registre et pour les redémarrages au cours de l’installation. Pour préparer votre application pour le déploiement de MSI, procédez comme suit.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Pour préparer une application Shell pour le déploiement MSI  
  
1. Modifiez chaque fichier. vsixmanifest dans votre solution.  
  
     Dans l’élément `Identifier`, ajoutez un élément `InstalledByMSI` et un élément `SystemComponent`, puis définissez leurs valeurs sur `true`.  
  
     Ces éléments empêchent le programme d’installation VSIX d’essayer d’installer vos composants et l’utilisateur de les désinstaller à l’aide de la boîte de dialogue **extensions et mises à jour** .  
  
2. Pour chaque projet qui contient un manifeste VSIX, modifiez les tâches de génération pour générer le contenu à l’emplacement à partir duquel votre MSI sera installé. Incluez le manifeste VSIX dans la sortie de la génération, mais ne générez pas de fichier. vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Création d’un MSI pour votre shell  
 Pour générer votre package MSI, nous vous recommandons d’utiliser l' [ensemble d’outils XML Windows Installer](https://go.microsoft.com/fwlink/?LinkId=82720) , car il offre une plus grande flexibilité qu’un projet d’installation standard.  
  
 Dans votre fichier Product. wxs, définissez des blocs de détection et la disposition des composants de l’interpréteur de commandes.  
  
 Ensuite, créez des entrées de Registre, à la fois dans le fichier. reg de votre solution et dans ApplicationRegistry. wxs.  
  
### <a name="detection-blocks"></a>Blocs de détection  
 Un bloc de détection se compose d’un élément `Property` qui spécifie une condition préalable à détecter et un élément `Condition` qui spécifie un message à retourner si le composant requis n’est pas présent sur l’ordinateur. Par exemple, votre application Shell nécessite le package redistribuable Microsoft Visual Studio Shell et le bloc de détection ressemble au balisage suivant.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Disposition des composants de l’interpréteur de commandes  
 Vous devez ajouter des éléments pour identifier la structure de répertoire cible et les composants à installer.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Pour définir la disposition des composants de l’interpréteur de commandes  
  
1. Créez une hiérarchie d’éléments `Directory` pour représenter tous les répertoires à créer sur le système de fichiers sur l’ordinateur cible, comme le montre l’exemple suivant.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Ces répertoires sont référencés par `Id` lorsque des fichiers qui doivent être installés sont spécifiés.  
  
2. Identifiez les composants requis par l’interpréteur de commandes et votre application Shell, comme le montre l’exemple suivant.  
  
    > [!NOTE]
    > Certains éléments peuvent faire référence à des définitions dans d’autres fichiers. wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. L’élément `ComponentRef` fait référence à un autre fichier. wxs qui identifie les fichiers requis par le composant actuel. Par exemple, GeneralProfile a la définition suivante dans HelpAbout. wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         L’élément `DirectoryRef` spécifie l’emplacement où ces fichiers sont placés sur l’ordinateur de l’utilisateur. L’élément `Directory` spécifie qu’il sera installé dans un sous-répertoire, et chaque élément `File` représente un fichier généré ou qui existe dans le cadre de la solution et identifie l’emplacement où ce fichier peut être trouvé lors de la création du fichier MSI.  
  
    2. L’élément `ComponentGroupRef` fait référence à un groupe d’autres composants (ou des composants et des groupes de composants). Par exemple, `ComponentGroupRef` sous ApplicationGroup est défini comme suit dans application. wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Les dépendances requises pour les applications de Shell (isolé) sont les suivantes : DebuggerProxy, MasterPkgDef, Resources (en particulier le fichier. winprf), application et PkgDefs.  
  
### <a name="registry-entries"></a>Entrées de Registre  
 Le modèle de projet Shell (isolé) comprend un fichier *ProjectName*. reg pour les clés de Registre à fusionner lors de l’installation. Ces entrées de Registre doivent faire partie du MSI à des fins d’installation et de nettoyage. Vous devez également créer des blocs de Registre correspondants dans ApplicationRegistry. wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Pour intégrer des entrées de Registre dans le MSI  
  
1. Dans le dossier de personnalisation de l' **interpréteur** de commandes, ouvrez *ProjectName*. reg.  
  
2. Remplacez toutes les instances du $RootFolder $ Token par le chemin d’accès du répertoire d’installation cible.  
  
3. Ajoutez toutes les autres entrées de Registre requises par votre application.  
  
4. Ouvrez ApplicationRegistry. wxs.  
  
5. Pour chaque entrée de Registre dans *ProjectName*. reg, ajoutez un bloc de Registre correspondant, comme le montrent les exemples suivants.  
  
    |*NomProjet*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \CLSID\\{bb431796-A179-4df7-B65D-c0df6bda7cc6}]<br /><br /> @ = « Objet DTE de PhotoStudio »|\<RegistryKey ID = 'DteClsidRegKey’root = 'HKCR’key = ' $ (var. DteClsidRegKey) 'action = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue type = 'String’name = ' @ 'value = ' $ (var. ShortProductName) objet DTE'/><br /><br /> \</RegistryKey >|  
    |[HKEY_CLASSES_ROOT \CLSID\\{bb431796-A179-4df7-B65D-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = 'DteLocSrv32RegKey’root = 'HKCR’key = ' $ (var. DteClsidRegKey) \LocalServer32 'action = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue type = 'String’name = ' @ 'value = ' [INSTALLDIR] $ (var. ShortProductName). exe'/><br /><br /> \</RegistryKey >|  
  
     Dans cet exemple, var. DteClsidRegKey correspond à la clé de Registre dans la ligne supérieure. Var. ShortProductName correspond à `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Création d’un programme d’amorçage du programme d’installation  
 Votre MSI est installé uniquement si toutes les conditions préalables sont installées en premier. Pour faciliter l’expérience de l’utilisateur final, créez un programme d’installation qui recueille et installe toutes les conditions préalables avant d’installer votre application. Pour garantir la réussite de l’installation, effectuez les actions suivantes :  
  
- Appliquer l’installation par l’administrateur.  
  
- Détecte si le shell Visual Studio (isolé) est installé.  
  
- Exécutez l’un des deux programmes d’installation de Shell dans l’ordre.  
  
- Gérer les demandes de redémarrage.  
  
- Exécutez votre MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Application de l’installation par l’administrateur  
 Cette procédure est requise pour permettre au programme d’installation d’accéder aux répertoires requis, tels que \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Pour appliquer l’installation par l’administrateur  
  
1. Ouvrez le menu contextuel du projet d’installation, puis choisissez **Propriétés**.  
  
2. Sous **Propriétés de configuration/éditeur de liens/fichier manifeste**, définissez le **niveau d’exécution UAC** sur **requireAdministrator**.  
  
     Cette propriété met l’attribut qui requiert que le programme soit exécuté en tant qu’administrateur dans le fichier manifeste incorporé.  
  
### <a name="detecting-shell-installations"></a>Détection des installations de Shell  
 Pour déterminer si le shell Visual Studio (isolé) doit être installé, commencez par déterminer s’il est déjà installé en vérifiant la valeur de Registre HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Ces valeurs sont également lues par le bloc de détection de Shell dans Product. wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder spécifie l’emplacement d’installation de l’interpréteur de commandes Visual Studio et vous pouvez y rechercher des fichiers.  
  
 Pour obtenir un exemple de détection de l’installation d’un interpréteur de commandes, consultez la `GetProductDirFromReg` fonction de Utilities. cpp dans l’exemple de déploiement d’environnement.  
  
 Si l’un des shells Visual Studio requis par votre package n’est pas installé sur l’ordinateur, vous devez les ajouter à la liste des composants à installer. Pour obtenir un exemple, consultez la fonction `ComponentsPage::OnInitDialog` de ComponentsPage. cpp dans l’exemple de déploiement d’environnement.  
  
### <a name="running-the-shell-installers"></a>Exécution des programmes d’installation de l’interpréteur de commandes  
 Pour exécuter les programmes d’installation de l’interpréteur de commandes, appelez les fichiers redistribuables du shell Visual Studio à l’aide des arguments de ligne de commande appropriés. Au minimum, vous devez utiliser les arguments de ligne de commande **/norestart/q** et surveiller le code de retour pour déterminer ce qui doit être effectué par la suite. L’exemple suivant exécute le package redistribuable de l’interpréteur de commandes (isolé).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Exécution des programmes d’installation du module linguistique de Shell  
 Si, à la place, vous trouvez que le shell ou les interpréteurs de commandes ont été installés et qu’ils ont juste besoin d’un module linguistique, vous pouvez installer les modules linguistiques comme le montre l’exemple suivant.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Déchiffrement des valeurs de retour  
 Sur certains systèmes d’exploitation, l’installation de Visual Studio Shell (isolé) nécessite un redémarrage. Cette condition peut être déterminée par le code de retour de l’appel à `ExecCmd`.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installation terminée. Vous pouvez maintenant installer votre application.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installation terminée. Vous pouvez installer votre application une fois que l’ordinateur a été redémarré.|  
|3015|L’installation est en cours. Un redémarrage de l’ordinateur est nécessaire pour continuer l’installation.|  
  
### <a name="handling-restarts"></a>Gestion des redémarrages  
 Lorsque vous avez exécuté le programme d’installation de Shell à l’aide de l’argument **/norestart** , vous avez spécifié qu’il ne redémarre pas l’ordinateur ou n’a pas demandé la redémarrage de l’ordinateur. Toutefois, un redémarrage peut être nécessaire et vous devez vous assurer que votre programme d’installation se poursuit après le redémarrage de l’ordinateur.  
  
 Pour gérer correctement les redémarrages, assurez-vous qu’un seul programme d’installation est configuré pour reprendre et que le processus de reprise sera géré correctement.  
  
 Si ERROR_SUCCESS_REBOOT_REQUIRED ou 3015 est retourné, votre code doit redémarrer l’ordinateur avant que l’installation ne se poursuive.  
  
 Pour gérer les redémarrages, effectuez les actions suivantes :  
  
- Configurez le registre pour reprendre l’installation au démarrage de Windows.  
  
- Effectuez un double redémarrage du programme d’amorçage.  
  
- Supprimez la clé ResumeData du programme d’installation de l’interpréteur de commandes.  
  
- Redémarrez Windows.  
  
- Réinitialisez le chemin d’accès de démarrage du MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Configuration du Registre pour reprendre l’installation au démarrage de Windows  
 La clé de Registre HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ s’exécute au démarrage du système avec des autorisations d’administration, puis est effacée. HKEY_CURRENT_USER contient une clé similaire, mais elle s’exécute en tant qu’utilisateur normal et n’est pas appropriée pour les installations. Vous pouvez reprendre l’installation en plaçant une valeur de chaîne dans la clé RunOnce qui appelle votre programme d’installation. Toutefois, nous vous recommandons d’appeler le programme d’installation à l’aide d’un paramètre **/restart** ou similaire pour notifier l’application qu’elle reprend au lieu de démarrer. Vous pouvez également inclure des paramètres pour indiquer l’endroit où vous vous trouvez dans le processus d’installation, ce qui est particulièrement utile dans les installations qui peuvent nécessiter plusieurs redémarrages.  
  
 L’exemple suivant montre une valeur de clé de Registre RunOnce pour reprendre une installation.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Installation du double redémarrage du programme d’amorçage  
 Si le programme d’installation est utilisé directement à partir de RunOnce, le Bureau ne pourra pas se charger complètement. Pour rendre l’interface utilisateur complète disponible, vous devez créer une autre exécution de l’installation et terminer l’instance RunOnce.  
  
 Vous devez exécuter de nouveau le programme d’installation afin qu’il obtienne les autorisations appropriées, et vous devez lui fournir suffisamment d’informations pour savoir où vous avez arrêté avant le redémarrage, comme le montre l’exemple suivant.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Suppression de la clé ResumeData du programme d’installation de Shell  
 Le programme d’installation de l’interpréteur de commandes définit la clé de Registre HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData avec des données pour reprendre l’installation après le redémarrage. Étant donné que votre application, et non le programme d’installation de l’interpréteur de commandes, est en reprise, supprimez cette clé de Registre, comme le montre l’exemple suivant.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Redémarrage de Windows  
 Une fois que vous avez défini les clés de Registre requises, vous pouvez redémarrer Windows. L’exemple suivant appelle les commandes de redémarrage pour les différents systèmes d’exploitation Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Réinitialisation du chemin d’accès de démarrage de MSI  
 Avant le redémarrage, le répertoire actif est l’emplacement de votre programme d’installation, mais après le redémarrage, l’emplacement devient le répertoire system32. Votre programme d’installation doit réinitialiser le répertoire actif avant chaque appel MSI, comme le montre l’exemple suivant.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Exécution du MSI de l’application  
 Une fois que le programme d’installation de Visual Studio Shell a retourné ERROR_SUCCESS, vous pouvez exécuter le MSI pour votre application. Étant donné que votre programme d’installation fournit l’interface utilisateur, démarrez votre MSI en mode silencieux ( **/q**) et avec la journalisation ( **/l**), comme le montre l’exemple suivant.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
