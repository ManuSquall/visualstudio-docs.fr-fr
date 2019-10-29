---
title: Commandes qui doivent être exécutées après l’installation | Microsoft Docs
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
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982020"
---
# <a name="commands-that-must-be-run-after-installation"></a>Commandes qui doivent être exécutées après l’installation
Si vous déployez votre extension par le biais d’un fichier *. msi* , vous devez exécuter **devenv/setup** dans le cadre de votre installation afin que Visual Studio puisse découvrir vos extensions.

> [!NOTE]
> Les informations contenues dans cette rubrique s’appliquent à la recherche de *devenv. exe* avec Visual Studio 2008 et versions antérieures. Pour plus d’informations sur la façon de découvrir *devenv. exe* avec les versions ultérieures de Visual Studio, consultez [détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Rechercher devenv. exe
 Vous pouvez rechercher le fichier *devenv. exe* de chaque version à partir des valeurs de registre que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les programmes d’installation écrivent, en utilisant la table RegLocator et les tables AppSearch pour stocker les valeurs de registre en tant que propriétés. Pour plus d’informations, consultez [détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator les lignes de la table pour localiser devenv. exe à partir de différentes versions de Visual Studio

|Signature|Causes|Touche|Name|Tapez|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Lignes de table AppSearch pour les lignes de la table RegLocator correspondante

|Property|Signature|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Par exemple, le programme d’installation de Visual Studio écrit la valeur de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** en tant que *C:\VS2008\Common7\IDE\devenv.exe*, un chemin d’accès complet au fichier exécutable. le programme d’installation doit s’exécuter.

> [!NOTE]
> Étant donné que la colonne de type de la table RegLocator est 2, il n’est pas nécessaire de spécifier des informations de version supplémentaires dans la table de signatures.

## <a name="run-devenvexe"></a>Exécuter devenv. exe
 Après l’exécution de l’action standard AppSearch dans le programme d’installation, chaque propriété de la table AppSearch a une valeur qui pointe vers le fichier *devenv. exe* pour la version correspondante de Visual Studio. Si l’une des valeurs de Registre spécifiées n’est pas présente, car cette version de Visual Studio n’est pas installée, la propriété spécifiée a la valeur null.

 Windows Installer prend en charge l’exécution d’un exécutable auquel une propriété pointe via un type d’action personnalisé 50. L’action personnalisée doit inclure les options d’exécution dans le script, `msidbCustomActionTypeInScript` (1024) et `msidbCustomActionTypeCommit` (512), pour s’assurer que le VSPackage a été correctement installé avant de l’intégrer dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [options d’exécution du script de](/windows/desktop/msi/custom-action-in-script-execution-options)la [table CustomAction](/windows/desktop/msi/customaction-table) et de l’action personnalisée.

 Les actions personnalisées de type 50 spécifient la propriété contenant l’exécutable comme valeur de la colonne source et les arguments de ligne de commande dans la colonne cible.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Lignes de table CustomAction pour exécuter devenv. exe

|Action|Tapez|Source|une cible|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Les actions personnalisées doivent être créées dans la table InstallExecuteSequence pour les planifier pour exécution pendant l’installation. Utilisez la propriété correspondante dans chaque ligne de la colonne condition pour empêcher l’exécution de l’action personnalisée si cette version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’est pas installée sur le système.

> [!NOTE]
> Les propriétés dont la valeur est NULL sont évaluées à `False` lorsqu’elles sont utilisées dans les conditions.

 La valeur de la colonne Sequence pour chaque action personnalisée dépend d’autres valeurs de séquence dans votre package Windows Installer. Les valeurs de séquence doivent être telles que les actions personnalisées *devenv. exe* s’exécutent aussi près que possible juste avant l’action standard InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Table InstallExecuteSequence pour planifier les actions personnalisées devenv. exe

|Action|Condition|Séquence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Voir aussi
- [Installer les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)