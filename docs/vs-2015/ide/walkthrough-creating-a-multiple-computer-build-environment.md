---
title: 'Procédure pas à pas : création d’un environnement de build sur plusieurs ordinateurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d0fccb5694e538cdf71844d2cc18640114ec735
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672310"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Procédure pas à pas : création d'un environnement de build sur plusieurs ordinateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer un environnement de build dans votre organisation en installant Visual Studio sur un ordinateur hôte, puis en copiant plusieurs fichiers et paramètres sur un autre ordinateur afin qu’il puisse participer aux builds. Vous n’avez pas à installer Visual Studio sur un autre ordinateur.

 Ce document ne confère pas de droits pour redistribuer le logiciel en externe ou pour fournir des environnements de build à des tiers.

||
|-|
|Clause d'exclusion de responsabilité<br /><br /> Ce document est fourni "en l’état". Nous avons testé les étapes décrites, mais nous ne pouvons pas tester exhaustivement chaque configuration. Nous tenterons de maintenir le document à jour avec toute information supplémentaire obtenue. Les informations et les points de vue exprimés dans ce document, y compris les URL et autres références à des sites web, peuvent être modifiés sans préavis. Microsoft exclut toute garantie, expresse ou implicite, concernant les informations fournies ici. Vous assumez les risques liés à leur utilisation.<br /><br /> Ce document ne vous fournit aucun droit légal de propriété intellectuelle de tout produit Microsoft. Vous pouvez copier le présent document pour une utilisation interne à des fins de référence.<br /><br /> Vous n’avez aucune obligation de faire à Microsoft des suggestions, commentaires ou autre retour concernant ce document. Toutefois, tout commentaire que vous fournissez volontairement peut être utilisé dans des produits Microsoft et les spécifications liées ou dans une autre documentation (collectivement, les "Offres Microsoft") qui peuvent elles-mêmes être utilisées par des tiers pour développer leurs propres produits. Par conséquent, si vous envoyez des retours sous forme de commentaires à Microsoft concernant n’importe quelle version de ce document ou les Offres Microsoft auxquelles ils s’appliquent, vous acceptez les points suivants : (a) Microsoft peut librement utiliser, reproduire, autoriser, distribuer et commercialiser vos commentaires dans toute Offre Microsoft ; (b) vous n’accorderez également aux tiers, sans frais, que les droits de brevet nécessaires pour permettre à d’autres produits d’utiliser ou d’interagir avec toutes les parties spécifiques d’un produit Microsoft qui incorporent vos commentaires ; et (c) vous n’enverrez à Microsoft aucun commentaire (i) pour lequel vous avez une raison de croire qu’il est soumis à un brevet, un copyright ou une autre revendication de propriété intellectuelle ou un autre droit envers un tiers ; ou (ii) qui soit soumis aux termes d’un contrat de licence exigeant que toute Offre Microsoft intégrant ou dérivée de ces commentaires, ou d’une autre propriété intellectuelle Microsoft, soit fournie sous licence à tout tiers ou partagée avec celui-ci.|

 Cette procédure pas à pas a été validée par rapport aux systèmes d’exploitation suivants, en exécutant MSBuild à partir de la ligne de commande et en utilisant Team Foundation Build.

- Windows 8 (x86 et x64)

- Windows 7 Édition Intégrale

- Windows Server 2008 R2 Standard

  Après avoir effectué les étapes de cette procédure, vous pouvez utiliser l’environnement à plusieurs ordinateurs pour générer les types d’applications suivants :

- Applications de bureau C++ qui utilisent Windows 8 SDK

- Applications de bureau Visual Basic ou C# qui ciblent .NET Framework 4.5

  Il n’est pas possible d’utiliser l’environnement à plusieurs ordinateurs pour générer les types d’applications suivants :

- Applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Pour générer des applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], vous devez installer Visual Studio sur l’ordinateur de build.

- Applications de bureau qui ciblent .NET Framework 4 ou version antérieure. Pour générer ce genre d’applications, vous devez installer Visual Studio ou bien les outils et assemblys de référence .NET (à partir du SDK Windows 7.1) sur l’ordinateur de build.

  Cette procédure pas à pas est divisée en différentes parties, notamment les suivantes :

- [Installation du logiciel sur les ordinateurs](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)

- [Copie de fichiers de l’ordinateur hôte vers l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)

- [Création des paramètres du Registre](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)

- [Définition de variables d’environnement sur l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)

- [Installation d’assemblys MSBuild dans le global assembly cache (GAC) sur l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)

- [Génération de projets](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)

- [Création de l’environnement de build afin qu’il puisse être archivé dans le contrôle de code source](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)

## <a name="prerequisites"></a>Prérequis

- Une copie sous licence de Visual Studio Ultimate, Visual Studio Premium ou Visual Studio Professional

- Une copie de .NET Framework 4.5.1, que vous pouvez télécharger à partir du site web [Microsoft](https://www.microsoft.com/download/details.aspx?id=40779).

## <a name="installing-software-on-the-computers"></a><a name="InstallingSoftware"></a> Installation d’un logiciel sur les ordinateurs
 Configurez tout d’abord l’ordinateur hôte, puis l’ordinateur de build.

 En installant Visual Studio sur l’ordinateur hôte, vous créez des fichiers et des paramètres que vous copierez ultérieurement sur l’ordinateur de build. Vous pouvez installer Visual Studio sur un ordinateur x86 ou x64, mais l’architecture de l’ordinateur de build doit correspondre à l’architecture de l’ordinateur hôte.

#### <a name="to-install-software-on-the-computers"></a>Pour installer le logiciel sur les ordinateurs

1. Sur l’ordinateur hôte, installez Visual Studio.

2. Sur l’ordinateur de build, installez .NET Framework 4.5. Pour vérifier qu’il est installé, assurez-vous que la valeur de la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version commence par "4.5".

## <a name="copying-files-from-the-host-computer-to-the-build-computer"></a><a name="CopyingFiles"></a> Copie de fichiers de l’ordinateur hôte vers l’ordinateur de build
 Cette section décrit la copie de fichiers, compilateurs, outils de génération, composants MSBuild et paramètres de Registre spécifiques à partir de l’ordinateur hôte vers l’ordinateur de build. Ces instructions supposent que vous avez installé Visual Studio à l’emplacement par défaut sur l’ordinateur hôte ; si vous l’avez installé à un autre emplacement, ajustez les étapes en conséquence.

- Sur un ordinateur x86, l’emplacement par défaut est C:\Program Files\Microsoft Visual Studio 11.0\

- Sur un ordinateur x64, l’emplacement par défaut est C:\Program Files (x86)\Microsoft Visual Studio 11.0\

  Notez que le nom du dossier Program Files dépend du système d’exploitation installé. Sur un ordinateur x86, le nom est \Program Files\\ ; sur l’ordinateur x64, le nom est \Program Files (x86)\\. Indépendamment de l’architecture du système, cette procédure pas à pas fait référence au dossier Program Files sous la forme %ProgramFiles%.

> [!NOTE]
> Sur l’ordinateur de build, tous les fichiers appropriés doivent se trouver sur le même lecteur ; toutefois, la lettre de ce lecteur peut être différente de la lettre du lecteur sur lequel Visual Studio est installé sur l’ordinateur hôte. Dans tous les cas, vous devez tenir compte de l’emplacement des fichiers quand vous créez des entrées de Registre, comme décrit plus loin dans ce document.

#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Pour copier les fichiers du SDK Windows sur l’ordinateur de build

1. Si seul le SDK Windows pour Windows 8 est installé, copiez ces dossiers de manière récursive de l’ordinateur hôte sur l’ordinateur de build :

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

     Si les autres Kits Windows 8 suivants le sont aussi...

   - Kit de déploiement et d’évaluation Microsoft Windows

   - Microsoft Windows Driver Kit

   - Kit de certification de matériel Microsoft Windows

     ...ils peuvent avoir installé des fichiers dans les dossiers %ProgramFiles%\Windows Kits\8.0\ indiqués à l’étape précédente, et les termes du contrat de licence peuvent ne pas autoriser les droits de serveur de builds pour ces fichiers. Consultez les termes du contrat de licence pour chaque Kit Windows installé afin de vérifier si les fichiers peuvent être copiés vers votre ordinateur de build. Si ces termes n’autorisent pas les droits de serveur de builds, supprimez les fichiers de l’ordinateur de build.

2. Copiez les dossiers suivants de manière récursive de l’ordinateur hôte vers l’ordinateur de build :

   - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

   - %ProgramFiles%\Common Files\Merge Modules\

   - %ProgramFiles%\Microsoft Visual Studio 11.0\VC\

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\

   - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. Copiez les fichiers suivants de l’ordinateur hôte vers l’ordinateur de build :

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat

4. Les bibliothèques runtime Visual C++ suivantes sont nécessaires uniquement si vous exécutez des sorties de génération sur l’ordinateur de build, par exemple dans le cadre de tests automatisés. Les fichiers sont généralement situés dans les sous-dossiers du dossier %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86\ ou %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64\, selon l’architecture du système. Sur les systèmes x86, copiez les fichiers binaires x86 dans le dossier \Windows\System32\. Sur les systèmes x64, copiez les fichiers binaires x86 dans le dossier Windows\SysWOW64\, et les binaires x64 dans le dossier Windows\System32\.

   - \Microsoft.VC110.ATL\atl110.dll

   - \Microsoft.VC110.CRT\msvcp110.dll

   - \Microsoft.VC110.CRT\msvcr110.dll

   - \Microsoft.VC110.CXXAMP\vcamp110.dll

   - \Microsoft.VC110.MFC\mfc110.dll

   - \Microsoft.VC110.MFC\mfc110u.dll

   - \Microsoft.VC110.MFC\mfcm110.dll

   - \Microsoft.VC110.MFC\mfcm110u.dll

   - \Microsoft.VC110.MFCLOC\mfc110chs.dll

   - \Microsoft.VC110.MFCLOC\mfc110cht.dll

   - \Microsoft.VC110.MFCLOC\mfc110deu.dll

   - \Microsoft.VC110.MFCLOC\mfc110enu.dll

   - \Microsoft.VC110.MFCLOC\mfc110esn.dll

   - \Microsoft.VC110.MFCLOC\mfc110fra.dll

   - \Microsoft.VC110.MFCLOC\mfc110ita.dll

   - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

   - \Microsoft.VC110.MFCLOC\mfc110kor.dll

   - \Microsoft.VC110.MFCLOC\mfc110rus.dll

   - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Copiez uniquement les fichiers suivants du dossier \Debug_NonRedist\x86\ ou \Debug_NonRedist\x64\ vers l’ordinateur de build, comme décrit dans [Préparation d’un ordinateur de test pour lancer un exécutable de débogage](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Aucun autre fichier ne peut être copié.

   - \Microsoft.VC110.DebugCRT\msvcp110d.dll

   - \Microsoft.VC110.DebugCRT\msvcr110d.dll

   - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110ud.dll

   - \Microsoft.VC110.DebugMFC\mfcm110d.dll

   - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

   - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="creating-registry-settings"></a><a name="CreatingRegistry"></a> Création de paramètres du Registre
 Vous devez créer des entrées de Registre pour configurer des paramètres pour MSBuild.

#### <a name="to-create-registry-settings"></a>Pour créer des paramètres du Registre

1. Identifiez le dossier parent des entrées du Registre. Toutes les entrées du Registre sont créées sous la même clé parente. Sur un ordinateur x86, la clé parente est HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Sur un ordinateur x64, la clé parente est HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Indépendamment de l’architecture du système, cette procédure pas à pas fait référence à la clé parente sous la forme %RegistryRoot%.

   > [!NOTE]
   > Si l’architecture de votre ordinateur hôte diffère de celle de votre ordinateur de build, veillez à utiliser la clé parente appropriée sur chaque ordinateur. Cela est particulièrement important si vous automatisez le processus d’exportation.
   >
   >  De plus, si vous utilisez une lettre de lecteur différente sur l’ordinateur de build de celle que vous utilisez sur l’ordinateur hôte, veillez à changer les valeurs des entrées de Registre pour qu’elles correspondent.

2. Créez les entrées de Registre suivantes sur l’ordinateur de build. Toutes ces entrées sont des chaînes (Type == "REG_SZ" dans le Registre). Définissez les valeurs de ces entrées identiques à celles des entrées comparables sur l’ordinateur hôte.

   - %RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder

   - %RegistryRoot%\VisualStudio\11.0@Source Directories

   - %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64

   - %RegistryRoot%\VisualStudio\SxS\VC7@11.0

   - %RegistryRoot%\VisualStudio\SxS\VS7@11.0

   - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

     Sur un ordinateur de build x64, créez également l’entrée de Registre suivante, et reportez-vous à l’ordinateur hôte pour déterminer comment la définir.

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder

     Si votre ordinateur de build est un ordinateur x64 et que vous voulez utiliser la version 64 bits de MSBuild, ou si vous utilisez le service de build Team Foundation Server sur un ordinateur x64, vous devez créer les entrées de Registre suivantes dans le Registre 64 bits natif. Reportez-vous à l’ordinateur hôte pour savoir comment définir ces entrées.

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

## <a name="setting-environment-variables-on-the-build-computer"></a><a name="SettingEnvVariables"></a> Définition de variables d’environnement sur l’ordinateur de build
 Pour utiliser MSBuild sur l’ordinateur de build, vous devez définir les variables d’environnement PATH. Pour ce faire, vous pouvez utiliser vcvarsall.bat, ou vous pouvez les configurer manuellement.

#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Pour définir des variables d’environnement à l’aide de vcvarsall.bat

- Ouvrez une fenêtre d’invite de commandes sur l’ordinateur de build, puis exécutez %Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat. Vous pouvez utiliser un argument de ligne de commande pour spécifier l’ensemble d’outils à utiliser : compilateur croisé x64, x64 natif ou x86. Si vous ne spécifiez pas d’argument de ligne de commande, l’ensemble d’outils x86 est utilisé.

     Le tableau suivant décrit les arguments pris en charge pour vcvarsall.bat :

    |Argument Vcvarsall.bat|Compilateur|Architecture de l’ordinateur de build|Architecture de sortie de génération|
    |----------------------------|--------------|---------------------------------|-------------------------------|
    |x86 (valeur par défaut)|Natif 32 bits|x86, x64|x86|
    |x86_amd64|x64 croisé|x86, x64|x64|
    |amd64|x64 natif|x64|x64|

     Si vcvarsall.bat s’exécute correctement, autrement dit, si aucun message d’erreur ne s’affiche, vous pouvez ignorer l’étape suivante et passer à la section [Installation d’assemblys MSBuild dans le GAC (Global Assembly Cache) sur l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) de ce document.

#### <a name="to-manually-set-environment-variables"></a>Pour définir manuellement des variables d’environnement

1. Pour configurer manuellement l’environnement de ligne de commande, ajoutez le chemin suivant à la variable d’environnement PATH :

   - %Program Files%\Microsoft Visual Studio 11.0\Common7\IDE

2. Si vous le souhaitez, vous pouvez également ajouter les chemins suivants à la variable PATH afin de faciliter l’utilisation de MSBuild pour générer vos solutions.

    Si vous voulez utiliser MSBuild 32 bits natif, ajoutez les chemins suivants à la variable PATH :

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

     Si vous voulez utiliser MSBuild 64 bits natif, ajoutez les chemins suivants à la variable PATH :

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="installing-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="InstallingMSBuildToGAC"></a> Installation d’assemblys de MSBuild dans le GAC (Global Assembly Cache) sur l’ordinateur de build
 MSBuild exige que certains assemblys supplémentaires soient installés dans le GAC sur l’ordinateur de build.

#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Pour copier des assemblys à partir de l’ordinateur hôte et les installer sur l’ordinateur de build

1. Copiez les assemblys suivants à partir de l’ordinateur hôte vers l’ordinateur de build. Étant donné qu’ils seront installés dans le GAC, l’emplacement où vous les placez sur l’ordinateur de build n’a pas d’importance.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Pour installer les assemblys dans le GAC, recherchez gacutil.exe sur l’ordinateur de build (il se trouve généralement dans %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\). Si vous ne trouvez pas ce dossier, répétez les étapes de la section [Copie de fichiers de l’ordinateur hôte vers l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de cette procédure pas à pas.

     Ouvrez une fenêtre d’invite de commandes disposant de droits d’administration, puis exécutez la commande suivante pour chaque fichier :

     **gacutil-i \<file>**

    > [!NOTE]
    > Pour qu’un assembly s’installe totalement dans le GAC, un redémarrage peut être nécessaire.

## <a name="building-projects"></a><a name="BuildingProjects"></a> Génération de projets
 Vous pouvez utiliser Team Foundation Build pour générer des projets et des solutions [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. Vous pouvez également les générer sur la ligne de commande. Quand vous utilisez Team Foundation Build pour générer des projets, il appelle l’exécutable MSBuild correspondant à l’architecture système.  Sur la ligne de commande, vous pouvez utiliser MSBuild 32 bits ou MSBuild 64 bits, et vous pouvez choisir l’architecture de MSBuild en définissant la variable d’environnement PATH ou en appelant directement l’exécutable MSBuild spécifique à l’architecture.

 Pour utiliser msbuild.exe à l’invite de commandes, exécutez la commande suivante, dans laquelle *solution.sln* est un espace réservé pour le nom de votre solution.

 **msbuild** *solution.sln*

 Pour plus d’informations sur l’utilisation de MSBuild sur la ligne de commande, consultez [référence de la ligne de commande](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Pour générer des projets [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous devez utiliser l’ensemble d’outils de plateforme "v110". Si vous ne souhaitez pas modifier les fichiers projet [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous pouvez définir l’ensemble d’outils de plateforme en utilisant l’argument de ligne de commande suivant :
>
> **msbuild** *solution.sln* **/p:PlatformToolset=v110**

## <a name="creating-the-build-environment-so-that-it-can-be-checked-into-source-control"></a><a name="CreatingForSourceControl"></a> Création de l’environnement de build pour qu’il puisse être archivé dans le contrôle de code source
 Vous pouvez créer un environnement de build qui peut être déployé sur plusieurs ordinateurs et qui ne nécessite pas d’installer des fichiers dans le GAC ou de modifier des paramètres du Registre. Les étapes suivantes sont juste une manière d’accomplir cette opération. Adaptez ces étapes aux caractéristiques propres à votre environnement de build.

> [!NOTE]
> Vous devez désactiver la génération incrémentielle afin que tracker.exe ne provoque pas d’erreur lors de la génération. Pour désactiver une génération incrémentielle, définissez le paramètre de build suivant :
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Pour créer un environnement de build pouvant être archivé dans le contrôle de code source

1. Créez un répertoire de dépôt ("Depot") sur l’ordinateur hôte.

     Les étapes suivantes font référence à ce répertoire sous la forme %Depot%.

2. Copiez les répertoires et fichiers, comme décrit dans la section [Copie de fichiers de l’ordinateur hôte vers l’ordinateur de build](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de cette procédure pas à pas, puis collez-les dans le répertoire %Depot% que vous venez de créer. Par exemple, effectuez la copie de %ProgramFiles%\Windows Kits\8.0\bin\ vers %Depot%\Windows Kits\8.0\bin\\.

3. Une fois les fichiers collés dans %Depot%, apportez les modifications suivantes :

    - Dans %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ et \Microsoft.CppCommon.targets\\, remplacez toutes les instances de

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         par celle-ci :

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll”.

         Le nommage précédent dépend de l’assembly installé dans le GAC.

    - Dans %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets, remplacez chaque instance de

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         par celle-ci :

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll”.

4. Créez un fichier .props (par exemple, Partner.AutoImports.props), puis placez-le à la racine du dossier qui contient vos projets. Ce fichier sert à définir les variables qui sont utilisées par MSBuild pour rechercher diverses ressources. Si les variables ne sont pas définies par ce fichier, elles sont définies par d’autres fichiers .props et des fichiers .targets qui reposent sur des valeurs de Registre. Comme nous ne définissons aucune valeur de Registre, ces variables seraient vides et la génération échouerait. À la place, ajoutez ceci à Partner.AutoImports.props :

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

5. Dans chacun de vos fichiers projet, ajoutez la ligne suivante en haut, après la ligne `<Project Default Targets…>`.

    ```
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Changez l’environnement de ligne de commande comme suit :

    - Set Depot=*emplacement du répertoire Depot que vous avez créé à l’étape 1*

    - Set path=%path%;*emplacement de MSBuild sur l’ordinateur*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 11.0\Common7\IDE\

         Pour une génération 64 bits native, pointez sur MSBuild 64 bits.

## <a name="see-also"></a>Voir aussi
 [Préparation d’un ordinateur de test pour exécuter une](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable) [référence de ligne de commande](../msbuild/msbuild-command-line-reference.md) exécutable de débogage
