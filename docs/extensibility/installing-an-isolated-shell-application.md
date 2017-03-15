---
title: "Installation d&#39;une Application de Shell isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Déploiement d'applications basées sur l'interface de shell (Visual Studio)"
  - "Shell Visual Studio, déployer des applications shell"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 40
---
# Installation d&#39;une Application de Shell isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour installer une application d'interpréteur de commandes, vous devez effectuer les étapes suivantes.  
  
-   Préparer votre solution.  
  
-   Créer un package Windows Installer \(MSI\) pour votre application.  
  
-   Créer un programme d'amorçage du programme d'installation.  
  
 Tout le code d'exemple dans ce document est fourni à partir de la [exemple de déploiement d'interpréteur de commandes](http://go.microsoft.com/fwlink/?LinkId=262245), que vous pouvez télécharger à partir de la galerie de Code sur le site Web MSDN. L'exemple montre les résultats de la réalisation de chacune de ces étapes.  
  
## Composants requis  
 Pour effectuer les procédures de cette rubrique, les outils suivants doivent être installés sur votre ordinateur.  
  
-   Le Kit de développement logiciel de Visual Studio  
  
-   Le [ensemble d'outils XML de Windows Installer](http://go.microsoft.com/fwlink/?LinkId=82720) version 3.6  
  
 L'exemple requiert également les Microsoft Visualization Modeling SDK, qui nécessite des shells pas.  
  
## Préparation de votre Solution  
 Par défaut, génèrent des modèles de l'interpréteur de commandes de packages VSIX, mais ce comportement est destiné principalement à des fins de débogage. Lorsque vous déployez une application d'environnement, vous devez utiliser les packages MSI pour autoriser pour accéder au Registre et les redémarrages pendant l'installation. Pour préparer votre application pour le déploiement du MSI, procédez comme suit.  
  
#### Pour préparer une application d'environnement pour le déploiement du MSI  
  
1.  Modifier chaque fichier .vsixmanifest dans votre solution.  
  
     Dans la `Identifier` élément, ajouter un `InstalledByMSI` élément et un `SystemComponent` élément, puis définissez leurs valeurs `true`.  
  
     Ces éléments éviter l'installateur VSIX tente d'installer les composants et l'utilisateur de les désinstaller à l'aide de la **Extensions et mises à jour** boîte de dialogue.  
  
2.  Pour chaque projet qui contient un manifeste VSIX, modifier les tâches de génération pour générer le contenu à l'emplacement à partir duquel l'installation de votre fichier MSI. Inclure le manifeste VSIX dans la sortie de génération, mais ne créez pas un fichier .vsix.  
  
## Création d'un fichier MSI pour votre interpréteur de commandes  
 Pour créer votre package MSI, nous vous recommandons d'utiliser le [ensemble d'outils XML de Windows Installer](http://go.microsoft.com/fwlink/?LinkId=82720) car elle offre une plus grande flexibilité à un projet d'installation standard.  
  
 Dans votre fichier Product.wxs, définissez des blocs de détection et la disposition des composants de l'interpréteur de commandes.  
  
 Puis créez les entrées de Registre, dans le fichier .reg pour votre solution et ApplicationRegistry.wxs.  
  
### Blocs de détection  
 Un bloc de détection se compose d'un `Property` élément qui spécifie une condition préalable pour détecter et un `Condition` élément qui spécifie un message à renvoyer si la condition préalable n'est pas présente sur l'ordinateur. Par exemple, votre application nécessite Microsoft Visual Studio Shell redistribuable, et le bloc de détection ressemblent à la balise suivante.  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### Présentation des composants de l'interpréteur de commandes  
 Vous devez ajouter des éléments pour identifier la structure du répertoire cible et les composants à installer.  
  
##### Pour définir la disposition des composants de l'interpréteur de commandes  
  
1.  Créer une hiérarchie de `Directory` éléments pour représenter tous les répertoires à créer sur le système de fichiers sur l'ordinateur cible, comme le montre l'exemple suivant.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     Ces répertoires sont appelés par `Id` lorsque les fichiers qui doivent être installés sont spécifiées.  
  
2.  Identifier les composants qui nécessitent l'interpréteur de commandes et de votre application, comme le montre l'exemple suivant.  
  
    > [!NOTE]
    >  Certains éléments peuvent faire référence aux définitions dans d'autres fichiers .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  Le `ComponentRef` élément fait référence à un autre fichier .wxs qui identifie les fichiers requis par le composant actuel. Par exemple, GeneralProfile a la définition suivante dans HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         Le `DirectoryRef` élément indique où ces fichiers sur l'ordinateur de l'utilisateur. Le `Directory` élément indique qu'il sera installé dans un sous\-répertoire et chaque `File` élément représente un fichier qui est généré ou qui existe dans le cadre de la solution et identifie où ce fichier se trouve lorsque le fichier MSI est créé.  
  
    2.  Le `ComponentGroupRef` élément fait référence à un groupe d'autres composants \(ou des composants et des groupes de composants\). Par exemple, `ComponentGroupRef` sous ApplicationGroup est définie comme suit dans Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Requis pour les applications du Shell \(isolé\), les dépendances sont : DebuggerProxy, MasterPkgDef, ressources \(notamment le fichier .winprf\), des applications et PkgDefs.  
  
### Entrées de Registre  
 Le modèle de projet Shell \(isolé\) inclut un *nom\_projet*fichier .reg pour les clés de Registre pour la fusion sur l'installation. Ces entrées de Registre doivent faire partie de MSI pour l'installation et à des fins de nettoyage. Vous devez également créer des blocs de Registre correspondante dans ApplicationRegistry.wxs.  
  
##### Pour intégrer les entrées de Registre dans le fichier MSI  
  
1.  Dans le **Personnalisation du Shell** dossier, ouvrez *nom\_projet*. reg.  
  
2.  Remplacez toutes les instances du jeton $ $RootFolder par le chemin d'accès du répertoire d'installation cible.  
  
3.  Ajoutez toutes les autres entrées de Registre nécessaires à votre application.  
  
4.  Ouvrez ApplicationRegistry.wxs.  
  
5.  Pour chaque entrée de Registre de *nom\_projet*.reg, ajout d'un bloc de Registre correspondante, comme le montrent les exemples suivants.  
  
    |*Nom\_projet*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= « PhotoStudio DTE objet »|\< Id de la clé de Registre \= « DteClsidRegKey » Root \= « HKCR » Key \=' $\(var.\) DteClsidRegKey\)' Action \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue Type \= « chaîne » nom \= « @ » valeur \=' $\(var.\) Objet de ShortProductName\) DTE » \/ \><br /><br /> \< \/ la clé de Registre \>|  
    |\[\\LocalServer32 HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= « $RootFolder$\\PhotoStudio.exe »|\< Id de la clé de Registre \= « DteLocSrv32RegKey » Root \= « HKCR » Key \=' $\(var.\) DteClsidRegKey\) \\LocalServer32' Action \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue Type \= « chaîne » nom \= « @ » valeur \='\[INSTALLDIR\] $\(var.\) ShortProductName\) .exe » \/ \><br /><br /> \< \/ la clé de Registre \>|  
  
     Dans cet exemple, Var.DteClsidRegKey correspond à la clé de Registre dans la ligne supérieure. Var.ShortProductName correspond à `PhotoStudio`.  
  
## Création d'un programme d'amorçage d'installation  
 Votre fichier MSI terminée installera uniquement si tous les composants requis sont installés en premier. Pour faciliter l'expérience utilisateur, créez un programme d'installation qui rassemble et installe tous les composants requis avant d'installer votre application. Pour vérifier une installation réussie, effectuez ces actions :  
  
-   Installation par l'administrateur est appliquée.  
  
-   Détecter si Visual Studio Shell \(isolé\) est installé.  
  
-   Exécuter un ou plusieurs programmes d'installation du Shell.  
  
-   Gérer les demandes de redémarrage.  
  
-   Exécutez votre fichier MSI.  
  
### Application d'Installation par l'administrateur  
 Cette procédure est requise pour activer le programme d'installation accéder aux répertoires requis par exemple \\Program.  
  
##### Pour appliquer l'installation par l'administrateur  
  
1.  Ouvrez le menu contextuel du projet d'installation, puis choisissez **propriétés**.  
  
2.  Sous **fichier de Configuration de l'éditeur de liens\/propriétés\/manifeste**, définissez **niveau d'exécution UAC** à **requireAdministrator**.  
  
     Cette propriété place l'attribut qui requiert le programme à exécuter en tant qu'administrateur dans le fichier de manifeste incorporé.  
  
### Détecter les Installations de Shell  
 Pour déterminer si Visual Studio Shell \(isolé\) doit être installé, tout d'abord déterminer si celui\-ci est installé en vérifiant la valeur de Registre de HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install.  
  
> [!NOTE]
>  Ces valeurs sont également lues par le bloc de détection de Shell dans Product.wxs.  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder Spécifie l'emplacement où Visual Studio Shell a été installé, et vous pouvez rechercher des fichiers.  
  
 Pour obtenir un exemple montrant comment détecter une installation de l'interpréteur de commandes, consultez le `GetProductDirFromReg` fonction de Utilities.cpp dans l'exemple de déploiement d'interpréteur de commandes.  
  
 Si une ou les deux le shell Visual Studio requis par votre package n'est pas installé sur l'ordinateur, vous devez les ajouter à la liste des composants à installer. Pour obtenir un exemple, consultez la `ComponentsPage::OnInitDialog` fonction de ComponentsPage.cpp dans l'exemple de déploiement d'interpréteur de commandes.  
  
### Les programmes d'installation de l'interpréteur de commandes en cours d'exécution  
 Pour exécuter les programmes d'installation de l'interpréteur de commandes, appelez les redistribuables Visual Studio Shell en utilisant les arguments de ligne de commande correctes. Au minimum, vous devez utiliser les arguments de ligne de commande **\/norestart \/q** et regardez le code de retour déterminer ce qui doit être effectué par la suite. L'exemple suivant exécute le Shell \(isolé\) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### Les programmes d'installation du Pack de langue Shell en cours d'exécution  
 Si vous trouvez plutôt que l'interpréteur de commandes ou les interpréteurs de commandes ont été installés et simplement besoin un module linguistique, vous pouvez installer les modules linguistiques comme le montre l'exemple suivant.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### Déchiffrer des valeurs de retour  
 Sur certains systèmes d'exploitation, l'installation de Visual Studio Shell \(isolé\) nécessite un redémarrage. Cette condition peut être déterminée par le code de retour de l'appel à `ExecCmd`.  
  
|Valeur de retour|Description|  
|----------------------|-----------------|  
|ERROR\_SUCCESS|Installation est terminée. Vous pouvez désormais installer votre application.|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|Installation est terminée. Vous pouvez installer votre application après le redémarrage de l'ordinateur.|  
|3015|L'installation est en cours. Un redémarrage est requis pour poursuivre l'installation.|  
  
### Gestion des redémarrages  
 Lorsque vous avez exécuté le programme d'installation de l'interpréteur de commandes à l'aide de la **\/norestart** argument, que vous avez spécifié qu'il n'aurait pas redémarrer l'ordinateur ou demandez à l'ordinateur de redémarrer. Toutefois, un redémarrage peut être requis, et vous devez vous assurer que votre programme d'installation se poursuit après le redémarrage de l'ordinateur.  
  
 Pour gérer correctement les redémarrages, veillez à que ce qu'un seul programme d'installation est défini sur Reprendre et que le processus de reprise est géré correctement.  
  
 Si ERROR\_SUCCESS\_REBOOT\_REQUIRED ou 3015 est retourné, votre code doit redémarrez l'ordinateur avant l'installation se poursuit.  
  
 Pour gérer les redémarrages, effectuez ces actions :  
  
-   Configurer le Registre afin de reprendre l'installation au démarrage de Windows.  
  
-   Effectuer un redémarrage du programme d'amorçage double.  
  
-   Supprimez la clé ResumeData du programme d'installation Shell.  
  
-   Redémarrage de Windows.  
  
-   Réinitialiser le chemin d'accès de démarrage de MSI.  
  
### Le Registre pour reprendre l'installation au démarrage de Windows  
 Le HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ s'exécute au démarrage du système avec des autorisations administratives de clé de Registre et puis sont effacée.HKEY\_CURRENT\_USER contient une clé similaire, mais il s'exécute comme un utilisateur normal et n'est pas appropriée pour les installations. Vous pouvez reprendre l'installation en plaçant une valeur de chaîne dans la clé RunOnce qui appelle votre programme d'installation. Toutefois, nous vous recommandons d'appeler le programme d'installation en utilisant un **\/restart** ou un paramètre similaire pour notifier l'application il reprend au lieu de démarrer. Vous pouvez également inclure des paramètres pour indiquer au cours du processus d'installation, ce qui est particulièrement utile dans les installations qui peuvent nécessiter plusieurs redémarrages.  
  
 L'exemple suivant montre une valeur de clé de Registre RunOnce pour reprendre l'installation.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### L'installation de Double redémarrage du programme d'amorçage  
 Si le programme d'installation est utilisé directement à partir de RunOnce, le bureau sera en mesure de charger complètement. Pour rendre l'interface utilisateur, vous devez créer une autre exécution du programme d'installation et mettre fin à l'instance de RunOnce.  
  
 Vous devez réexécuter le programme d'installation afin qu'il obtient les autorisations appropriées, et vous devez lui donner suffisamment d'informations pour savoir où vous avez arrêté avant le redémarrage, comme le montre l'exemple suivant.  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### Suppression de la clé ResumeData du programme d'installation Shell  
 Les jeux de programme d'installation de Shell du HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData clé de Registre avec des données à reprendre l'installation après le redémarrage. Étant donné que votre application, pas le programme d'installation Shell, reprise, supprimez cette clé de Registre, comme le montre l'exemple suivant.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Le redémarrage de Windows  
 Après avoir défini les clés de Registre requises, vous pouvez redémarrer Windows. L'exemple suivant appelle les commandes de redémarrage pour différents systèmes d'exploitation Windows.  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### Réinitialiser le chemin d'accès de démarrage de MSI  
 Avant le redémarrage, le répertoire actif est l'emplacement de votre programme d'installation, mais après le redémarrage, l'emplacement devient le répertoire system32. Votre programme d'installation doit réinitialiser le répertoire actif avant chaque appel MSI, comme le montre l'exemple suivant.  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### Exécution de l'Application MSI  
 Une fois le programme d'installation de Visual Studio Shell retourne ERROR\_SUCCESS, vous pouvez exécuter le fichier MSI pour votre application. Étant donné que votre programme d'installation fournit l'interface utilisateur, démarrez votre fichier MSI en mode silencieux \(**\/q**\) et avec la journalisation \(**\/L**\), comme le montre l'exemple suivant.  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## Voir aussi  
 [Procédure pas à pas : Création d'une Application de base de Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)