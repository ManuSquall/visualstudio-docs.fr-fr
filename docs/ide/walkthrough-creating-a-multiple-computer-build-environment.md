---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un environnement de build sur plusieurs ordinateurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "environnement d'une build, MSBuild"
  - "MSBuild, génération sur plusieurs ordinateurs"
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un environnement de build sur plusieurs ordinateurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez créer un environnement de version dans votre organisation en installant Visual Studio sur un ordinateur hôte puis en copiant plusieurs fichiers et paramètres dans un autre ordinateur afin de pouvoir participer aux versions.  Vous ne devez pas installer Visual Studio sur un autre ordinateur.  
  
 Ce document ne confère pas de droits pour redistribuer le logiciel externe ou fournir des environnements de version à un tiers.  
  
||  
|-|  
|Exclusion de responsabilité<br /><br /> Ce document se trouve sur une base « telle quelle ».  Bien que nous avons testé les étapes décrites, nous ne pouvons pas tester exhaustivement chaque configuration.  Nous tenterons de garder le document à jour avec toutes les informations supplémentaires apprises.  Les informations et points de vue exprimés dans ce document, y compris les adresses URL et les autres références à des sites Internet, pourront faire l'objet de modifications sans préavis.  Microsoft n'offre aucune garantie, exprimée ou implicite, concernant les informations fournies ici.  Vous assumez le risque de l'utiliser.<br /><br /> Ce document ne vous donne aucun droit légal à quelque propriété intellectuelle que ce soit dans n'importe quel produit Microsoft.  Vous pouvez copier et utiliser ce document à des fins personnelles et référencées.<br /><br /> Vous n'avez aucune obligation de faire à Microsoft des suggestions, commentaires ou autre retour concernant ce document.  Toutefois, tout commentaire que vous fournissez volontairement peut être utilisé dans des produits de Microsoft et des spécifications liées ou d'autres documentations \(collectivement, « Offres Microsoft »\) qui peuvent elles\-mêmes être utilisées par des tiers pour développer leurs propres produits.  Par conséquent, si vous envoyez des retours sous forme de commentaire à Microsoft concernant n'importe quelle version de ce document ou n'importe quelle offre proposée par Microsoft auxquels ils s'appliquent, vous acceptez les points suivants : \(a\) Microsoft peut librement utiliser, reproduire, autoriser, distribuer, et commercialiser sans frais votre commentaire dans toute offre Microsoft ; \(B\) Vous n'accorderez également aux tiers, sans frais, que les propriétés industrielles nécessaires pour permettre à d'autres produits d'utiliser ou interagir avec toutes les parties spécifiques d'un produit Microsoft qui incorporent vos commentaires ; et \(C\) vous vous engagez à ne donner à Microsoft aucun commentaire \(i\) pour lequel vous avez une raison de croire qu'il est soumis à un brevet, copyright ou toute autre revendication de propriété intellectuelle ou droit envers un tiers ; ou \(ii\) qui soit soumis aux termes du contrat de licence qui exige de demander que toute offre Microsoft ou dérivé d'un tel commentaire, ou d'une autre propriété intellectuelle Microsoft, ait l'autorisation ou a défaut soit partagé avec un tiers.|  
  
 Cette procédure pas à pas a été validée par rapport aux systèmes d'exploitation suivants, en exécutant MSBuild en ligne de commande et en utilisant Team Foundation Build.  
  
-   Windows 8 \(x86 et x64\)  
  
-   Windows 7 Édition Intégrale  
  
-   Windows Server 2008 R2 Standard  
  
 Après avoir effectué les étapes de cette procédure, vous pouvez utiliser l'environnement de plusieurs ordinateurs pour générer ces types d'applications :  
  
-   Applications de bureau C\+\+ qui utilisent Windows 8 SDK  
  
-   Applications de bureau Visual Basic ou C\# qui ciblent .NET Framework 4.5  
  
 L'environnement à plusieurs ordinateur ne peut pas être utilisé pour générer ces types d'applications :  
  
-   Applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  Pour générer des applications d'[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], vous devez installer Visual Studio sur l'ordinateur de version.  
  
-   Applications de bureau qui ciblent .NET Framework 4 ou version antérieure.  Pour générer ce genre d'applications, vous devez installer Visual Studio ou les ensembles de référence et les outils .NET \(Windows 7,1 SDK\) sur l'ordinateur de version.  
  
 Cette procédure pas à pas est divisée en les parties suivantes :  
  
-   [Installation du logiciel sur les ordinateurs](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [Copie de fichiers à partir de l'ordinateur hôte à l'ordinateur de version](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [Création des paramètres du Registre](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [Paramètres des variables d'environnement sur l'ordinateur de version](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [Installation d'ensembles MSBuild dans le Global Assembly Cache (GAC) sur l'ordinateur de version.](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [Génération de projets](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [Création de l'environnement de version afin qu'il puisse être archivé dans le contrôle de code source](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## Composants requis  
  
-   Une copie sous licence de Visual Studio Ultimate, Visual Studio Premium, ni de Visual Studio Professional  
  
-   Une copie du .NET Framework 4.5.1, que vous pouvez télécharger depuis le [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software) sur le site Web.  
  
##  <a name="InstallingSoftware"></a> Installation du logiciel sur les ordinateurs  
 D'abord, installez l'ordinateur hôte puis installez l'ordinateur de version.  
  
 Lorsque vous installez Visual Studio sur l'ordinateur hôte, vous créez des fichiers et des paramètres que vous copierez sur l'ordinateur de version ultérieurement.  Vous pouvez installer Visual Studio sur un ordinateur x86 ou x64, mais l'architecture de l'ordinateur de version doit correspondre à l'architecture de l'ordinateur hôte.  
  
#### Pour installer le logiciel sur les ordinateurs  
  
1.  Sur l'ordinateur hôte, installez Visual Studio.  
  
2.  Sur l'ordinateur de version, installez .NET Framework 4.5. Pour vérifier qu'il est installé, assurez\-vous que la valeur de la clé de registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full@Version commence par "4.5".  
  
##  <a name="CopyingFiles"></a> Copie de fichiers à partir de l'ordinateur hôte à l'ordinateur de version  
 Cette section décrit la copie des fichiers spécifiques, des compilateurs, des outils de génération, des composants MSBuild, et des paramètres du Registre depuis l'ordinateur hôte vers l'ordinateur de version.  Ces instructions supposent que vous avez installé Visual Studio à l'emplacement par défaut sur l'ordinateur hôte ; si vous l'avez installé à un autre emplacement, ajustez les étapes en conséquence.  
  
-   Sur un ordinateur x86, l'emplacement par défaut est C:\\Program Files\\Microsoft Visual Studio 11.0 \\  
  
-   Sur un ordinateur x64, l'emplacement par défaut est C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0 \\  
  
 Notez que le nom du dossier Program Files dépend du système d'exploitation installée.  Sur un ordinateur x86, le nom est \\Program Files\\; sur l'ordinateur x64, le nom est \\Program Files \(x86\) \\.  Indépendamment de l'architecture du système, cette procédure pas à pas fait référence au dossier Program Files comme %ProgramFiles%.  
  
> [!NOTE]
>  Sur l'ordinateur de version, tous les fichiers utiles doivent être sur le même lecteur ; Toutefois, la lettre de lecture de ce lecteur peut être différente de la lettre de lecture pour le lecteur où Visual Studio est installé sur l'ordinateur hôte.  Dans tous les cas, vous devez identifier l'emplacement des fichiers lorsque vous créez des entrées du Registre comme décrit plus loin dans ce document.  
  
#### Pour copier les fichiers du Kit de développement logiciel Windows à l'ordinateur de version  
  
1.  Si vous avez uniquement le Kit de développement logiciel pour Windows 8 installé, copiez ces dossiers de manière récursive à partir de l'ordinateur hôte vers l'ordinateur de version :  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\bin \\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\catalogues \\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\DesignTime \\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Include \\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Lib\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Redist \\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\références \\  
  
     Si vous avez également ces autres kits Windows 8…  
  
    -   Kit de Déploiement et d'Evaluation Microsoft Windows  
  
    -   Kit de pilote Microsoft Windows  
  
    -   Kit de certification du matériel Microsoft Windows  
  
     … ils peuvent avoir installé les fichiers dans les dossiers %ProgramFiles%\\Windows Kits\\8.0\\, lesquels sont répertoriés dans l'étape précédente, et les termes du contrat de licence peuvent ne pas autoriser les droits de serveur de versions pour ces fichiers.  Vérifiez les termes du contrat de licence pour chaque Kit Windows installé pour vérifier si les fichiers peuvent être copiés vers votre ordinateur de version.  Si les termes du contrat de licence n'autorisent pas les droits de serveur de versions, supprimez les fichiers de l'ordinateur de version.  
  
2.  Copiez les dossiers suivants de manière récursive à partir de l'ordinateur hôte vers l'ordinateur de version :  
  
    -   %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\  
  
    -   %ProgramFiles%\\Common Files\\Merge Modules\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\ProjectComponents \\  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\V110\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETFramework\\v4.5\\  
  
3.  Copiez ces fichiers à partir de l'ordinateur hôte à l'ordinateur de version :  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msobj110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbcore.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbsrv.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msvcdis110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\makehm.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\vsvars32.bat  
  
4.  Les bibliothèques runtime Visual C\+\+ suivantes sont requises uniquement si vous exécutez des sorties de version sur l'ordinateur de version—par exemple, dans le cadre du test automatisé.  Les fichiers sont généralement situés dans les sous\-dossiers du dossier %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x86\\ ou %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x64 \\, selon l'architecture du système.  Sur les systèmes x86, copiez les fichiers binaires x86 dans le dossier \\Windows\\System32\\.  Sur les systèmes x64, copiez les fichiers binaires x86 dans le dossier Windows\\SysWOW64 \\, et les binaires x64 dans le dossier Windows\\System32\\.  
  
    -   \\Microsoft.VC110.ATL\\atl110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcp110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcr110.dll  
  
    -   \\Microsoft.VC110.CXXAMP\\vcamp110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110u.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110u.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110chs.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110cht.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110enu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110esn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110fra.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110ita.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110jpn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110kor.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110rus.dll  
  
    -   \\Microsoft.VC110.OPENMP\\vcomp110.dll  
  
5.  Copiez uniquement les fichiers suivants depuis le dossier \\Project Debug\_NonRedist\\x86\\ ou \\Debug\_NonRedist\\x64\\ vers l'ordinateur de version, comme décrit dans [Préparation d'un ordinateur de test pour lancer un exécutable de débogage](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable).  Aucun autre fichier ne peut être copié.  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcp110d.dll  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcr110d.dll  
  
    -   \\Microsoft.VC110.DebugCXXAMP\\vcamp110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110d.dll  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcr110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110ud.dll  
  
    -   \\Microsoft.VC110.DebugOpenMP\\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Création des paramètres du Registre  
 Vous devez créer des entrées du Registre pour configurer des paramètres pour MSBuild.  
  
#### Pour créer les paramètres de Registre  
  
1.  Identifiez le dossier parent pour les entrées du Registre.  Toutes les entrées du Registre sont créées sous la même clé de parent.  Sur un ordinateur x86, la clé parente est HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.  Sur un ordinateur x64, la clé parente est HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.  Indépendamment de l'architecture du système, cette procédure pas à pas fait référence à la clé parente comme %RegistryRoot%.  
  
    > [!NOTE]
    >  Si l'architecture de votre ordinateur hôte diffère de celle de votre ordinateur de version, veillez à utiliser la clé parent appropriée sur chaque ordinateur.  C'est particulièrement important si vous automatisez le processus d'exportation.  
    >   
    >  Pars ailleurs, si vous utilisez une lettre de lecture différente dans l'ordinateur de version de celle que vous utilisez sur l'ordinateur hôte, veillez à modifier les valeurs des entrées du Registre pour rester concordant.  
  
2.  Créez les entrées du Registre suivantes sur l'ordinateur de version.  Toutes ces entrées sont des chaînes \(Type \=\= "REG\_SZ" dans le Registre\).  Définissez les valeurs de ces entrées identiques à celles des valeurs des entrées comparables sur l'ordinateur hôte.  
  
    -   %RegistryRoot%\\.NETFramework\\v4.0.30319\\AssemblyFoldersEx\\VCMSBuild Public Assemblies@\(Default\)  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x86@InstallationFolder  
  
    -   %RegistryRoot%\\VisualStudio\\11.0@Source Directories  
  
    -   %RegistryRoot%\\VisualStudio\\11.0\\Setup\\VC@ProductDir  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkVer32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkVer64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@11.0  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VS7@11.0  
  
    -   %RegistryRoot%\\Windows Kits\\Installed Roots@KitsRoot  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
     Sur un ordinateur de version x64, créez également l'entrée suivante du Registre et reportez\-vous à l'ordinateur hôte pour déterminer la définir.  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x64@InstallationFolder  
  
     Si votre ordinateur de version est x64 et utiliser la version 64 bits de MSBuild, ou si vous utilisez le service de build Team Foundation Server sur un ordinateur x64, vous devez créer les entrées suivantes du Registre dans le Registre 64 bits natif.  Reportez\-vous à l'ordinateur hôte pour déterminer comment définir ces entrées.  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Setup\\VS@ProductDir  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Paramètres des variables d'environnement sur l'ordinateur de version  
 Pour utiliser MSBuild sur l'ordinateur de version, vous devez définir les variables d'environnement PATH.  Vous pouvez utiliser vcvarsall.bat pour définir les variables, ou vous pouvez les configurer manuellement.  
  
#### Pour utiliser vcvarsall.bat afin de définir les variables d'environnement  
  
-   Ouvrez une fenêtre d'invite de commandes sur l'ordinateur de version et le lancez %Program Files%\\Microsoft Visual Studio 11.0\\VC\\vcvarsall.bat.  Utilisez un argument de ligne de commande pour spécifier l'ensemble d'outils que vous souhaitez utiliser — x86, natif x64, ou compilateur croisé x64.  Si vous ne spécifiez pas d'argument de ligne de commande, l'ensemble d'outils x86 est utilisé.  
  
     Ce tableau décrit les arguments pris en charge pour vcvarsall.bat.  
  
    |Argument Vcvarsall.bat|Compilateur|Architecture informatique de génération|Architecture de sortie de génération|  
    |----------------------------|-----------------|---------------------------------------------|------------------------------------------|  
    |x86 \(valeur par défaut\)|Natif 32 bits|x86, x64|x86|  
    |x86\_amd64|x64 Croisé|x86, x64|x64|  
    |amd64|x64 Natif|x64|x64|  
  
     Si vcvarsall.bat réussi à se lancer — autrement dit, si aucun message d'erreur ne s'affiche — ignorez l'étape suivante et passez à la section [Installation d'ensembles MSBuild dans le Global Assembly Cache (GAC) sur l'ordinateur de version.](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) de ce document.  
  
#### Pour configurer manuellement les variables d'environnement  
  
1.  Pour configurer manuellement l'environnement de ligne de commande, ajoutez ce chemin à la variable d'environnement PATH :  
  
    -   %Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE  
  
2.  Éventuellement, vous pouvez également ajouter des chemins suivants à la variable PATH pour faciliter l'utilisation de MSBuild lors de la génération de vos solutions.  
  
     Si vous souhaitez utiliser MSBuild 32 bits natif, ajoutez ces chemins d'accès à la variable de PATH :  
  
    -   %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools  
  
    -   %windir%\\Microsoft.NET\\Framework\\v4.0.30319  
  
     Si vous souhaitez utiliser MSBuild 64 bits natif, ajoutez ces chemins d'accès à la variable de PATH :  
  
    -   %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\x64  
  
    -   %windir%\\Microsoft.NET\\Framework64\\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> Installation d'ensembles MSBuild dans le Global Assembly Cache \(GAC\) sur l'ordinateur de version.  
 MSBuild requiert certains ensembles supplémentaires à installer dans le GAC sur l'ordinateur de version.  
  
#### Pour copier des ensembles à partir de l'ordinateur hôte et les installer sur l'ordinateur de version  
  
1.  Copiez les ensembles suivants à partir de l'ordinateur hôte vers l'ordinateur de version.  Comme ils seront installés dans le GAC, il pas lorsque vous les placez sur l'ordinateur de version.  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\CommonExtensions\\Microsoft\\VC\\projet\\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\PublicAssemblies\\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Pour installer des ensembles dans le GAC, localisez gacutil.exe sur l'ordinateur de version — généralement, il se trouve dans %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\.  Si vous ne pouvez pas trouver ce dossier, répétez les étapes de la section [Copie de fichiers à partir de l'ordinateur hôte à l'ordinateur de version](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de cette procédure.  
  
     Ouvrez une fenêtre d'invite de commandes qui dispose des droits d'administration et exécutée cette commande pour chaque fichier :  
  
     **gacutil \-i \<file\>**  
  
    > [!NOTE]
    >  Un redémarrage peut être requis pour un assembly pour installer complètement le GAC.  
  
##  <a name="BuildingProjects"></a> Génération de projets  
 Utilisez Team Foundation Build pour générer des projets et des solutions [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ou générez\-les en ligne de commande.  Lorsque vous utilisez Team Foundation Build pour générer des projets, il invoque le fichier exécutable MSBuild qui correspond à l'architecture du système.  En ligne de commande, vous pouvez utiliser MSBuild 32 bits ou MSBuild 64 bits, et vous pouvez choisir l'architecture MSBuild en définissant la variable d'environnement PATH ou en appelant directement le fichier exécutable MSBuild d'architecture spécifique.  
  
 Pour utiliser msbuild.exe à l'invite de commandes, exécutez la commande suivante, où *solution.sln* est un espace réservé pour le nom de votre solution.  
  
 **msbuild** *solution.sln*  
  
 Pour plus d'informations sur l'utilisation de MSBuild en ligne de commande [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Pour générer des projets d'[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous devez utiliser l'ensemble d'outils de la plateforme « v110 ».  Si vous ne souhaitez pas modifier les fichiers projet d'[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez définir l'ensemble d'outils de plateforme à l'aide de cet argument de ligne de commande :  
>   
>  **msbuild** *solution.sln* **\/p:PlatformToolset\=v110**  
  
##  <a name="CreatingForSourceControl"></a> Création de l'environnement de version afin qu'il puisse être archivé dans le contrôle de code source  
 Vous pouvez créer un environnement de version qui peut être déployé sur plusieurs ordinateurs et ne requiert pas de fichiers de GAC ou de modification des paramètres du Registre de modification.  Les étapes suivantes sont une seule façon d'y parvenir.  Adapte ces étapes aux caractéristiques uniques de votre environnement de version.  
  
> [!NOTE]
>  Vous devez désactiver la création incrémentielle afin que tracker.exe ne lève pas d'erreur pendant une génération.  Pour désactiver la génération incrémentielle, définissez ce paramètre de génération :  
>   
>  **msbuild** *solution.sln* **\/p:TrackFileAccess\=false**  
  
#### Pour créer un environnement de génération qui peut être archivé dans le contrôle de code source  
  
1.  Créez un répertoire « cible » sur l'ordinateur hôte.  
  
     Ces étapes renvoient au répertoire comme %Depot%.  
  
2.  Copiez les répertoires et les fichiers comme décrit dans la section [Copie de fichiers à partir de l'ordinateur hôte à l'ordinateur de version](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de cette procédure, collez les dans le répertoire de %Depot% que vous venez de créer.  Par exemple, copiez depuis %ProgramFiles%\\Windows Kits\\8.0\\bin\\à %Depot%\\Windows Kits\\8.0\\bin \\.  
  
3.  Lorsque les fichiers sont collés dans %Depot%, apportez ces modifications :  
  
    -   Dans %Depot%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110 \\, de Microsoft.CPP.Targets\\Microsoft.Cpp.InvalidPlatforms.targets \\,\\Microsoft.cppbuild.targets \\, et\\Microsoft.CppCommon.targets \\, modifiez chaque instance de  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110, Version\= 4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a »  
  
         en  
  
         AssemblyFile\= " $ \(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll ».  
  
         L'attribution précédente repose sur l'assembly en cours GAC.  
  
    -   Dans %Depot%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPPClean.Targets, modifiez chaque instance de  
  
         AssemblyName\= " Microsoft.Build.CppTasks.Common.v110, Version\= 4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a »  
  
         en  
  
         AssemblyFile\= "$\(VCTargetsPath11\) Microsoft.Build.CppTasks.Common.v110.dll ».  
  
4.  Créez un fichier .props — par exemple, Partner.AutoImports.props — et mettez\-la à la racine du dossier qui contient vos projets.  Ce fichier est utilisé pour définir les variables utilisées par MSBuild pour rechercher différentes ressources.  Si les variables ne sont pas définies par ce fichier, elles sont définies par d'autres fichiers .props et fichiers .targets qui reposent sur des valeurs de Registre.  Comme nous ne définissons aucune valeur de Registre, ces variables seraient vides et la génération échouerait.  À la place, ajoutez ceci à Partner.AutoImports.props :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  Dans chacun de vos fichiers projet, ajoutez la ligne suivante au début, après la ligne d'`<Project Default Targets…>`.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Modifiez l'environnement de ligne de commande comme suit :  
  
    -   Set Depot\=*location of the Depot directory that you created in step 1*  
  
    -   Ensemble path\=%path% ;*location of MSBuild on the computer*; %Depot%\\Windows\\System32;%Depot%\\Windows\\SysWOW64 ; %Depot%\\Microsoft Visual Studio 11.0\\Common7\\IDE \\  
  
         Pour la génération 64 bits natif, pointez sur MSBuild 64 bits.  
  
## Voir aussi  
 [Préparation d'un ordinateur de test pour lancer un exécutable de débogage](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)