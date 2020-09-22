---
title: Commandes qui doivent être exécutées après l’installation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840074"
---
# <a name="commands-that-must-be-run-after-installation"></a>Commandes à exécuter après l’installation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Si vous déployez votre extension par le biais d’un fichier. msi, vous devez exécuter `devenv /setup` dans le cadre de votre installation afin que Visual Studio puisse découvrir vos extensions.  
  
> [!NOTE]
> Les informations contenues dans cette rubrique s’appliquent à la recherche de DevEnv avec Visual Studio 2008 et versions antérieures. Pour plus d’informations sur la façon de découvrir DevEnv avec les versions ultérieures de Visual Studio, consultez détection de la [Configuration système requise](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Recherche d' devenv.exe  
 Vous pouvez rechercher les devenv.exe de chaque version à partir des valeurs de registre que les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] programmes d’installation écrivent, en utilisant la table RegLocator et la table AppSearch pour stocker les valeurs de registre en tant que propriétés. Pour plus d’informations, consultez détection de la [Configuration système requise](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator les lignes de la table pour rechercher devenv.exe à partir de différentes versions de Visual Studio  
  
|Signature_|Root|Clé|Nom|Type|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Lignes de table AppSearch pour les lignes de la table RegLocator correspondante  
  
|Propriété|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Par exemple, le programme d’installation de Visual Studio écrit la valeur de registre de **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** comme **C:\VS2008\Common7\IDE\devenv.exe**, un chemin d’accès complet à l’exécutable que le programme d’installation doit exécuter.  
  
 **Remarque** Étant donné que la colonne de type RegLocator est 2, il n’est pas nécessaire de spécifier des informations de version supplémentaires dans la table de signatures.  
  
## <a name="running-devenvexe"></a>Exécution de devenv.exe  
 Après l’exécution de l’action standard AppSearch dans le programme d’installation, chaque propriété de la table AppSearch a une valeur qui pointe vers le fichier devenv.exe pour la version correspondante de Visual Studio. Si l’une des valeurs de Registre spécifiées n’est pas présente, car cette version de Visual Studio n’est pas installée, la propriété spécifiée a la valeur null.  
  
 Windows Installer prend en charge l’exécution d’un exécutable auquel une propriété pointe via un type d’action personnalisé 50. L’action personnalisée doit inclure les options d’exécution in-script, msidbCustomActionTypeInScript (1024) et msidbCustomActionTypeCommit (512), pour s’assurer que le VSPackage a été correctement installé avant de l’intégrer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pour plus d’informations, consultez Options d’exécution du script de la table CustomAction et de l’action personnalisée.  
  
 Les actions personnalisées de type 50 spécifient la propriété contenant l’exécutable comme valeur de la colonne source et les arguments de ligne de commande dans la colonne cible.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Lignes de table CustomAction à exécuter devenv.exe  
  
|Action|Type|Source|Cible|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Les actions personnalisées doivent être créées dans la table InstallExecuteSequence pour les planifier pour exécution pendant l’installation. Utilisez la propriété correspondante dans chaque ligne de la colonne condition pour empêcher l’exécution de l’action personnalisée si cette version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] n’est pas installée sur le système.  
  
> [!NOTE]
> `Null` les propriétés sont évaluées à lorsqu’elles sont `False` utilisées dans les conditions.  
  
 La valeur de la colonne Sequence pour chaque action personnalisée dépend d’autres valeurs de séquence dans votre package Windows Installer. Les valeurs de séquence doivent être telles que les actions personnalisées devenv.exe s’exécutent aussi près que possible juste avant l’action standard InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Table InstallExecuteSequence pour planifier les actions personnalisées devenv.exe  
  
|Action|Condition|Séquence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
