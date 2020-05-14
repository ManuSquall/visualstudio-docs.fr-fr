---
title: Commandes qui doivent être exécutées après l’installation ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709470"
---
# <a name="commands-that-must-be-run-after-installation"></a>Commandes qui doivent être exécutées après l’installation
Si vous déployez votre extension via un fichier *.msi,* vous devez exécuter **devenv /configuration** dans le cadre de votre installation afin que Visual Studio découvre vos extensions.

> [!NOTE]
> L’information dans ce sujet s’applique à trouver *devenv.exe* avec Visual Studio 2008 et plus tôt. Pour plus d’informations sur la façon de découvrir *devenv.exe* avec des versions ultérieures de Visual Studio, voir [Détecter les exigences du système](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Trouver devenv.exe
 Vous pouvez localiser *devenv.exe* de chaque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] version à partir des valeurs de registre que les installateurs écrivent, en utilisant la table RegLocator et les tables AppSearch pour stocker les valeurs du registre comme propriétés. Pour plus d’informations, voir [Détecter les exigences du système](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Lignes de table RegLocator pour localiser devenv.exe de différentes versions de Visual Studio

|Signature|Root|Clé|Nom|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE-Microsoft-VisualStudio 7.0 -Setup-VS|EnvironnementPath|2|
|RL_DevenvExe_2003|2|SOFTWARE-Microsoft-VisualStudio-7.1-Setup-VS|EnvironnementPath|2|
|RL_DevenvExe_2005|2|SOFTWARE-Microsoft-VisualStudio 8.0 -Setup-VS|EnvironnementPath|2|
|RL_DevenvExe_2008|2|SOFTWARE-Microsoft-VisualStudio-9.0-Setup-VS|EnvironnementPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Lignes de table AppSearch pour les rangées de table RegLocator correspondantes

|Propriété|Signature|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Par exemple, l’installateur Visual Studio écrit la valeur du registre de **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0-Setup-VS-EnvironmentPath** comme *C: VS2008-Common7-IDE-devenv.exe*, un chemin complet vers l’exécutable de l’installateur doit fonctionner.

> [!NOTE]
> Étant donné que la colonne Type de la table RegLocator est 2, il n’est pas nécessaire de spécifier des informations de version supplémentaires dans le tableau Signature.

## <a name="run-devenvexe"></a>Exécuter devenv.exe
 Après l’action standard AppSearch fonctionne dans l’installateur, chaque propriété dans la table AppSearch a une valeur pointant vers le fichier *devenv.exe* pour la version correspondante de Visual Studio. Si l’une des valeurs de registre spécifiées n’est pas présente — parce que cette version de Visual Studio n’est pas installée — la propriété spécifiée est configurée à l’annulation.

 Windows Install prend en charge l’exécution d’un exécuteur auquel une propriété indique par le type d’action personnalisé 50. L’action personnalisée devrait inclure les `msidbCustomActionTypeInScript` options d’exécution en `msidbCustomActionTypeCommit` script, (1024) et (512), pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]s’assurer que le VSPackage a été installé avec succès avant de l’intégrer dans . Pour plus d’informations, voir [CustomAction table](/windows/desktop/msi/customaction-table) et [Custom action in-script options d’exécution](/windows/desktop/msi/custom-action-in-script-execution-options).

 Les actions personnalisées de type 50 spécifient la propriété contenant l’exécutable comme valeur de la colonne Source et des arguments de ligne de commande dans la colonne Cible.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Lignes de table CustomAction pour exécuter devenv.exe

|Action|Type|Source|Cible|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/configuration|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/configuration|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/configuration|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/configuration|

 Les actions personnalisées doivent être rédigées dans le tableau InstallExecuteSequence pour les planifier pour l’exécution pendant l’installation. Utilisez la propriété correspondante dans chaque rangée de la colonne Condition pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] empêcher l’action personnalisée d’être exécuté si cette version n’est pas installée sur le système.

> [!NOTE]
> Les propriétés de `False` valeur nulle évaluent lorsqu’elles sont utilisées dans des conditions.

 La valeur de la colonne Séquence pour chaque action personnalisée dépend des autres valeurs de séquence de votre package Windows Installer. Les valeurs de séquence doivent être telles que les actions *personnalisées devenv.exe* s’exécutent aussi près que possible de immédiatement avant l’action standard InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallerExecuteSequence table pour planifier les actions personnalisées devenv.exe

|Action|Condition|Séquence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Voir aussi
- [Installer VSPackages avec Installateur Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
