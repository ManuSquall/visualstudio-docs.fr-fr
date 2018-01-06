---
title: "Les commandes doivent être exécutés après l’Installation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ff4b1e572fd1e0c5c500fbd756d01063665bd1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>Commandes doivent être exécutés après l’Installation
Si vous déployez votre extension via un fichier .msi, vous devez exécuter `devenv /setup` dans le cadre de votre installation afin que Visual Studio de découvrir vos extensions.  
  
> [!NOTE]
>  Les informations contenues dans cette rubrique s’applique à la recherche de DevEnv avec Visual Studio 2008 et versions antérieures. Pour plus d’informations sur la façon de découvrir DevEnv avec les versions ultérieures de Visual Studio, consultez [détection configuration système requise du](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Recherche de devenv.exe  
 Vous pouvez localiser de chaque version devenv.exe à partir du Registre des valeurs que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écrivant des programmes d’installation, à l’aide de la RegLocator Table et AppSearch Table pour stocker les valeurs de Registre en tant que propriétés. Pour plus d’informations, consultez [détection configuration système requise du](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Lignes de la table RegLocator pour localiser devenv.exe à partir de différentes versions de Visual Studio  
  
|Signature_|racine|Touche|Name|Type|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Lignes de la table pour les lignes correspondantes de la table RegLocator AppSearch  
  
|Propriété|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Par exemple, le programme d’installation de Visual Studio écrit la valeur de Registre de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** en tant que **C:\VS2008\Common7\IDE\devenv.exe**, un chemin d’accès complet au fichier exécutable du programme d’installation doit s’exécuter.  
  
 **Remarque** , car la colonne de Type de RegLocator est 2, il n’est pas nécessaire de spécifier des informations de version supplémentaires dans la Table de la Signature.  
  
## <a name="running-devenvexe"></a>Devenv.exe en cours d’exécution  
 Après l’action standard s’exécute dans le programme d’installation AppSearch, chaque propriété de la table AppSearch a la valeur pointant vers le fichier devenv.exe pour la version correspondante de Visual Studio. Si une des valeurs de Registre spécifié ne sont pas présente, car cette version de Visual Studio n’est pas installée, la propriété spécifiée a la valeur null.  
  
 Prend en charge de Windows Installer un fichier exécutable vers laquelle pointe une propriété en cours d’exécution via l’action personnalisée tapez 50. L’action personnalisée doit inclure les options d’exécution de dans le script, msidbCustomActionTypeInScript (1024) et msidbCustomActionTypeCommit (512), pour vous assurer que le VSPackage a été installé avec succès avant d’intégrer dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez CustomAction Table et les Options de l’exécution dans le Script actions personnalisées.  
  
 Actions personnalisées de type 50 spécifient la propriété contenant l’exécutable en tant que la valeur de la colonne Source et les arguments de ligne de commande dans la colonne cible.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Lignes de la table CustomAction pour exécuter devenv.exe  
  
|Action|Type|Source|une cible|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Actions personnalisées doivent être créées dans la table InstallExecuteSequence à planifier leur exécution lors de l’installation. La propriété correspondante dans chaque ligne de la colonne de la Condition permet d’éviter que l’action personnalisée en cours d’exécution si cette version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’est pas installé sur le système.  
  
> [!NOTE]
>  `Null`pour évaluent les propriétés `False` lorsqu’il est utilisé dans les conditions.  
  
 La valeur de la colonne de séquence pour chaque action personnalisée dépend d’autres valeurs de séquence dans votre package de programme d’installation de Windows. Valeurs de séquence doivent être telles que les actions personnalisées devenv.exe exécuter en tant que près possible immédiatement avant l’action standard InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Table InstallExecuteSequence pour planifier les actions personnalisées devenv.exe  
  
|Action|Condition|Séquence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)