---
title: Les commandes qui doivent être exécutées après l’Installation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8a59e1a6613936c586c5529dcfc6a56a957112c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341988"
---
# <a name="commands-that-must-be-run-after-installation"></a>Commandes qui doivent être exécutées après l’installation
Si vous déployez votre extension via un *.msi* fichier, vous devez exécuter **devenv /setup** dans le cadre de votre installation afin que Visual Studio de découvrir vos extensions.

> [!NOTE]
> Les informations contenues dans cette rubrique s’applique à la recherche *devenv.exe* avec Visual Studio 2008 et versions antérieures. Pour plus d’informations sur la découverte *devenv.exe* avec les versions ultérieures de Visual Studio, consultez [détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Trouver devenv.exe
 Vous pouvez localiser de chaque version *devenv.exe* à partir de Registre des valeurs qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écrivant des programmes d’installation, à l’aide de la table RegLocator et AppSearch tables pour stocker les valeurs de Registre en tant que propriétés. Pour plus d’informations, consultez [détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Lignes de la table RegLocator pour localiser devenv.exe à partir de différentes versions de Visual Studio

|Signature|Racine|Touche|Nom|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Lignes de la table pour les lignes correspondantes de la table RegLocator AppSearch

|Propriété|Signature|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Par exemple, le programme d’installation de Visual Studio écrit la valeur de Registre de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** comme *C:\VS2008\Common7\IDE\devenv.exe*, un chemin d’accès complet au fichier exécutable du programme d’installation doit s’exécuter.

> [!NOTE]
> Colonne de Type de la table RegLocator est 2, il n’est pas nécessaire de spécifier des informations de version supplémentaires dans la table de la Signature.

## <a name="run-devenvexe"></a>Run devenv.exe
 Après avoir AppSearch action standard s’exécute dans le programme d’installation, chaque propriété de la table AppSearch a une valeur qui pointe vers le *devenv.exe* fichier pour la version correspondante de Visual Studio. Si les valeurs de Registre spécifiée ne sont pas présents, car cette version de Visual Studio n’est pas installée, la propriété spécifiée est définie avec la valeur null.

 Programme d’installation de Windows prend en charge un exécutable vers lequel pointe une propriété via l’action personnalisée tapez 50. L’action personnalisée doit inclure les options d’exécution dans le script, `msidbCustomActionTypeInScript` (1024) et `msidbCustomActionTypeCommit` (512), pour vous assurer que le VSPackage a été correctement installé avant leur intégration dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [CustomAction table](https://docs.microsoft.com/windows/desktop/msi/customaction-table) et [options d’exécution dans le script des actions personnalisées](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Actions personnalisées de type 50 spécifient la propriété contenant le fichier exécutable en tant que la valeur de la colonne Source et les arguments de ligne de commande dans la colonne cible.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Lignes de la table CustomAction pour exécuter devenv.exe

|Action|Type|Source|une cible|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Actions personnalisées doivent être créées dans la table InstallExecuteSequence à planifier leur exécution pendant l’installation. Utilisez la propriété correspondante dans chaque ligne de la colonne de la Condition pour éviter que l’action personnalisée en cours d’exécution si cette version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’est pas installé sur le système.

> [!NOTE]
> Évaluent les propriétés de valeur null à `False` lorsqu’il est utilisé dans les conditions.

 La valeur de la colonne de séquence pour chaque action personnalisée dépend d’autres valeurs de séquence dans votre package de programme d’installation de Windows. Les valeurs de séquence doivent être telle que la *devenv.exe* actions personnalisées, exécuter en tant que proches que possible et immédiatement avant l’action standard de InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Table InstallExecuteSequence pour planifier les actions personnalisées de devenv.exe

|Action|Condition|Séquence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Voir aussi
- [Installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)