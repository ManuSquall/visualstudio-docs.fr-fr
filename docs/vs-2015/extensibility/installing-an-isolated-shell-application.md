---
title: Installation d’une Application de Shell isolé | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ecec7963b66c20ef08d1e5f3f0917a66f885aa0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796302"
---
# <a name="installing-an-isolated-shell-application"></a>Installation d’une Application de Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour installer une application de Shell, vous devez effectuer les étapes suivantes.  
  
- Préparer votre solution.  
  
- Créer un package Windows Installer (MSI) pour votre application.  
  
- Créer un programme d’amorçage du programme d’installation.  
  
  Tout le code d’exemple dans ce document est fourni à partir de la [exemple de déploiement d’interpréteur de commandes](http://go.microsoft.com/fwlink/?LinkId=262245), que vous pouvez télécharger à partir de la galerie de Code sur le site Web MSDN. L’exemple montre les résultats de l’exécution de chacune de ces étapes.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer les procédures décrites dans cette rubrique, les outils suivants doivent être installés sur votre ordinateur.  
  
- Le SDK Visual Studio  
  
- Le [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) version 3.6  
  
  L’exemple nécessite également le Microsoft Visualization et Modeling SDK, qui nécessitent pas tous les interpréteurs de commandes.  
  
## <a name="preparing-your-solution"></a>Préparation de votre Solution  
 Par défaut, les modèles de l’interpréteur de commandes de la build vers les packages VSIX, mais ce comportement est destiné principalement à des fins de débogage. Lorsque vous déployez une application de Shell, vous devez utiliser les packages MSI pour autoriser pour accéder au Registre et les redémarrages pendant l’installation. Pour préparer votre application pour le déploiement MSI, procédez comme suit.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Pour préparer une application de Shell pour déploiement MSI  
  
1.  Modifier chaque fichier .vsixmanifest dans votre solution.  
  
     Dans le `Identifier` élément, ajoutez un `InstalledByMSI` élément et un `SystemComponent` élément, puis définissez leurs valeurs `true`.  
  
     Ces éléments éviter le programme d’installation VSIX tente d’installer vos composants et l’utilisateur à partir de leur désinstallation à l’aide de la **Extensions et mises à jour** boîte de dialogue.  
  
2.  Pour chaque projet qui contient un manifeste VSIX, modifier les tâches de génération pour générer le contenu à l’emplacement à partir de laquelle l’installation de votre identité MSI. Inclure le manifeste VSIX dans la sortie de génération, mais ne créez pas un fichier .vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Création d’un fichier MSI pour votre interpréteur de commandes  
 Pour générer votre package MSI, nous vous recommandons d’utiliser le [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) , car il offre davantage de flexibilité à un projet d’installation standard.  
  
 Dans votre fichier Product.wxs, définir des blocs de détection et la disposition des composants de l’interpréteur de commandes.  
  
 Puis créez les entrées de Registre, à la fois dans le fichier .reg pour votre solution et ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Blocs de détection  
 Un bloc de détection se compose d’un `Property` élément qui spécifie une condition préalable pour détecter et un `Condition` élément qui spécifie un message à retourner si la condition préalable n’est pas présente sur l’ordinateur. Par exemple, votre application de Shell nécessite Microsoft Visual Studio Shell redistribuable, et le bloc de détection se présenteront comme le balisage suivant.  
  
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
  
1.  Créer une hiérarchie de `Directory` éléments pour représenter tous les répertoires à créer sur le système de fichiers sur l’ordinateur cible, comme le montre l’exemple suivant.  
  
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
  
     Ces répertoires sont désignés par `Id` lorsque les fichiers qui doivent être installées sont spécifiés.  
  
2.  Identifier les composants qui nécessitent l’interpréteur de commandes et de votre application de Shell, comme le montre l’exemple suivant.  
  
    > [!NOTE]
    >  Certains éléments peuvent faire référence aux définitions dans d’autres fichiers .wxs.  
  
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
  
    1.  Le `ComponentRef` élément fait référence à un autre fichier .wxs qui identifie les fichiers requis par le composant actuel. Par exemple, GeneralProfile a la définition suivante dans HelpAbout.wxs.  
  
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
  
         Le `DirectoryRef` élément spécifie où ces fichiers sont placés sur l’ordinateur de l’utilisateur. Le `Directory` élément spécifie qu’il sera installé dans un sous-répertoire et chaque `File` élément représente un fichier qui est généré ou qui existe dans le cadre de la solution et identifie où ce fichier est accessible lorsque le fichier MSI est créé.  
  
    2.  Le `ComponentGroupRef` élément fait référence à un groupe d’autres composants (ou composants et groupes de composants). Par exemple, `ComponentGroupRef` sous ApplicationGroup est défini comme suit dans Application.wxs.  
  
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
    >  Requis sont des dépendances pour des applications de Shell (isolé) : DebuggerProxy, MasterPkgDef, ressources (en particulier le fichier .winprf), Application et PkgDefs.  
  
### <a name="registry-entries"></a>Entrées de Registre  
 Le modèle de projet Shell (isolé) inclut un *nom_projet*fichier .reg pour les clés de Registre à fusionner lors de l’installation. Ces entrées de Registre doivent faire partie de la MSI pour l’installation et à des fins de nettoyage. Vous devez également créer des blocs de Registre correspondante dans ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Pour intégrer les entrées de Registre dans le fichier MSI  
  
1.  Dans le **personnalisation du Shell** dossier, ouvrez *nom_projet*. reg.  
  
2.  Remplacez toutes les instances du jeton $ $RootFolder par le chemin d’accès du répertoire d’installation cible.  
  
3.  Ajoutez toutes les entrées de Registre nécessaires à votre application.  
  
4.  Ouvrez ApplicationRegistry.wxs.  
  
5.  Pour chaque entrée de Registre dans *nom_projet*.reg, ajoutez un bloc de Registre correspondante, comme le montrent les exemples suivants.  
  
    |*Nom_projet*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= « PhotoStudio DTE Object »|\<Id de clé de Registre = 'DteClsidRegKey' racine = clé 'HKCR' =' $(var.) DteClsidRegKey)' Action = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue Type = 'string' nom = « @ » valeur =' $(var.) Objet de ShortProductName) DTE » / ><br /><br /> \</ Clé de Registre >|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @= « $RootFolder$\PhotoStudio.exe »|\<Id de clé de Registre = 'DteLocSrv32RegKey' racine = clé 'HKCR' =' $(var.) DteClsidRegKey) \LocalServer32' Action = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue Type = 'string' nom = « @ » valeur ='[INSTALLDIR] $(var.) ShortProductName) .exe » / ><br /><br /> \</ Clé de Registre >|  
  
     Dans cet exemple, Var.DteClsidRegKey correspond à la clé de Registre dans la ligne du haut. Var.ShortProductName se résout en `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Création d’un programme d’amorçage du programme d’installation  
 Votre identité MSI terminée est installé uniquement si toutes les conditions préalables sont d’abord installés. Pour faciliter l’expérience utilisateur, créez un programme d’installation qui rassemble et installe toutes les conditions préalables avant d’installer votre application. Pour garantir une installation réussie, effectuez ces actions :  
  
-   Appliquer l’installation par l’administrateur.  
  
-   Détecter si Visual Studio Shell (isolé) est installé.  
  
-   Exécutez une ou les deux programmes d’installation d’interpréteur de commandes dans l’ordre.  
  
-   Gérer les demandes de redémarrage.  
  
-   Exécutez votre identité MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Application de l’Installation par l’administrateur  
 Cette procédure est nécessaire pour activer le programme d’installation accéder aux répertoires requis, tels que les fichiers de \Program\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Pour appliquer l’installation par l’administrateur  
  
1.  Ouvrez le menu contextuel du projet d’installation, puis choisissez **propriétés**.  
  
2.  Sous **fichier de Configuration de l’éditeur de liens/propriétés/manifeste**, affectez la valeur **niveau d’exécution UAC** à **requireAdministrator**.  
  
     Cette propriété place l’attribut qui nécessite le programme à exécuter en tant qu’administrateur dans le fichier de manifeste incorporé.  
  
### <a name="detecting-shell-installations"></a>Détection des Installations de l’interpréteur de commandes  
 Pour déterminer si Visual Studio Shell (isolé) doit être installé, vous devez d’abord déterminer si elle est déjà installée en vérifiant la valeur de Registre de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Ces valeurs sont également lues par le bloc de détection d’interpréteur de commandes dans Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Spécifie l’emplacement où le Shell Visual Studio a été installé, et vous pouvez rechercher les fichiers.  
  
 Pour obtenir un exemple montrant comment détecter une installation de l’interpréteur de commandes, consultez le `GetProductDirFromReg` fonction de Utilities.cpp dans l’exemple de déploiement d’interpréteur de commandes.  
  
 Si une ou les deux les interpréteurs de commandes Visual Studio requis par votre package n’est pas installé sur l’ordinateur, vous devez les ajouter à votre liste des composants à installer. Pour obtenir un exemple, consultez le `ComponentsPage::OnInitDialog` fonction de ComponentsPage.cpp dans l’exemple de déploiement d’interpréteur de commandes.  
  
### <a name="running-the-shell-installers"></a>Les programmes d’installation de l’interpréteur de commandes en cours d’exécution  
 Pour exécuter les programmes d’installation de l’interpréteur de commandes, appelez les redistribuables du Shell Visual Studio en utilisant les arguments de ligne de commande corrects. Au minimum, vous devez utiliser les arguments de ligne de commande **/norestart /q** et regardez le code de retour déterminer ce qui doit être fait ensuite. L’exemple suivant exécute le Shell (isolé) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Les programmes d’installation du Pack de langue interpréteur de commandes en cours d’exécution  
 Si vous trouvez à la place que l’interpréteur de commandes ou les interpréteurs de commandes ont été installés et simplement besoin un module linguistique, vous pouvez installer les modules linguistiques comme le montre l’exemple suivant.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Déchiffrer des valeurs de retour  
 Sur certains systèmes d’exploitation, l’installation de Visual Studio Shell (isolé) nécessite un redémarrage. Cette condition peut être déterminée par le code de retour de l’appel à `ExecCmd`.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installation est terminée. Vous pouvez maintenant installer votre application.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installation est terminée. Vous pouvez installer votre application après le redémarrage de l’ordinateur.|  
|3015|L’installation est en cours d’exécution. Un redémarrage de l’ordinateur est requis pour poursuivre l’installation.|  
  
### <a name="handling-restarts"></a>Gestion des redémarrages  
 Lorsque vous avez exécuté le programme d’installation de l’interpréteur de commandes à l’aide de la **/norestart** argument, que vous avez spécifié qu’il n’aurait pas de redémarrer l’ordinateur ou de demander le redémarrage de l’ordinateur. Toutefois, un redémarrage peut être nécessaire, et vous devez vous assurer que votre programme d’installation se poursuit après le redémarrage de l’ordinateur.  
  
 Pour gérer correctement les redémarrages, veillez à que ce qu’un seul programme d’installation est défini sur Reprendre et que le processus de reprise sont géré correctement.  
  
 Si ERROR_SUCCESS_REBOOT_REQUIRED ou 3015 est retourné, votre code doit redémarrer l’ordinateur avant l’installation se poursuit.  
  
 Pour gérer les redémarrages, effectuez ces actions :  
  
-   Configurer le Registre afin de reprendre l’installation lorsque Windows démarre.  
  
-   Effectuer un redémarrage double du programme d’amorçage.  
  
-   Supprimer la clé de ResumeData de Shell programme d’installation.  
  
-   Redémarrez Windows.  
  
-   Réinitialiser le chemin d’accès de démarrage de service administré.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Le Registre pour reprendre le programme d’installation au démarrage de Windows  
 La clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ exécute au démarrage du système avec des autorisations administratives et puis est effacée. HKEY_CURRENT_USER contient une clé similaire, mais il s’exécute en mode utilisateur normal et n’est pas approprié pour les installations. Vous pouvez reprendre l’installation en plaçant une valeur de chaîne dans la clé RunOnce qui appelle votre programme d’installation. Toutefois, nous vous recommandons d’appeler le programme d’installation à l’aide un **/redémarrer** ou un paramètre similaire pour avertir l’application de reprise d’activité au lieu de démarrer. Vous pouvez également inclure des paramètres pour indiquer où vous êtes dans le processus d’installation, qui est particulièrement utile dans les installations qui peuvent nécessiter plusieurs redémarrages.  
  
 L’exemple suivant montre une valeur de clé de Registre RunOnce pour la reprise d’une installation.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>L’installation de Double redémarrage du programme d’amorçage  
 Si le programme d’installation est utilisé directement à partir de RunOnce, le bureau sera en mesure de charger complètement. Pour rendre l’interface utilisateur complète soit disponible, vous devez créer une autre exécution du programme d’installation et mettre fin à l’instance de RunOnce.  
  
 Vous devez réexécuter le programme d’installation afin qu’il obtient les autorisations appropriées, et vous devez lui donner suffisamment d’informations pour savoir où vous avez arrêtés avant le redémarrage, comme le montre l’exemple suivant.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Suppression de la clé de ResumeData de Shell programme d’installation  
 Le programme d’installation de l’interpréteur de commandes définit la clé de Registre HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData avec des données pour reprendre le programme d’installation après le redémarrage. Étant donné que votre application, pas le programme d’installation Shell, est reprise, supprimez cette clé de Registre, comme le montre l’exemple suivant.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Le redémarrage de Windows  
 Après avoir défini les clés de Registre requises, vous pouvez redémarrer Windows. L’exemple suivant appelle les commandes de redémarrage pour les systèmes d’exploitation Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Réinitialiser le chemin d’accès de démarrage de MSI  
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
  
### <a name="running-the-application-msi"></a>Exécution de l’Application MSI  
 Une fois que le programme d’installation de Visual Studio Shell retourne ERROR_SUCCESS, vous pouvez exécuter le fichier MSI pour votre application. Étant donné que votre programme d’installation fournit l’interface utilisateur, commencer votre identité MSI en mode silencieux (**/q**) et avec la journalisation (**/l**), comme illustré dans l’exemple suivant.  
  
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

