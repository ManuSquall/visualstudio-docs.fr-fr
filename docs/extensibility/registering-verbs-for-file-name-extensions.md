---
title: L’inscription des verbes aux Extensions de nom de fichier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 692b94cc9bba5bf200d71f4356bef849ec2f3aae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138104"
---
# <a name="registering-verbs-for-file-name-extensions"></a>L’inscription des verbes aux Extensions de nom de fichier
L’association d’une extension de nom de fichier avec une application a généralement une action par défaut qui se produit lorsqu’un utilisateur double-clique sur un fichier. Cette action est liée à un verbe, par exemple ouvrir, qui correspond à l’action de préférence.  
  
 Vous pouvez inscrire les verbes qui sont associés à un identificateur programmatique (ProgID) d’une extension à l’aide de la clé de l’interpréteur de commandes située à HKEY_CLASSES_ROOT\\*progid*\shell. Pour plus d’informations, consultez [Types de fichiers](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>L’inscription des verbes Standard  
 Le système d’exploitation reconnaît les verbes standards suivants :  
  
-   Ouvrir  
  
-   Modifier  
  
-   Lecture  
  
-   Imprimer  
  
-   Preview  
  
 Chaque fois que possible, inscrivez un verbe standard. Le choix le plus courant est le verbe Open. Utilisez le verbe de modification uniquement s’il existe une différence entre l’ouverture du fichier et la modification du fichier. Par exemple, ouverture d’un fichier .htm affiche dans le navigateur, tandis que la modification d’un fichier .htm démarre un éditeur HTML. Les verbes standards sont localisés avec les paramètres régionaux du système d’exploitation.  
  
> [!NOTE]
>  Lorsque vous inscrivez des verbes standard, ne définissez pas la valeur par défaut pour ouvrir la clé. La valeur par défaut contient la chaîne d’affichage dans le menu. Le système d’exploitation fournit cette chaîne des verbes standard.  
  
 Fichiers de projet doivent être inscrits pour démarrer une nouvelle instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lorsqu’un utilisateur ouvre le fichier. L’exemple suivant illustre l’inscription d’une verbe standard pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projet.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Pour ouvrir un fichier dans une instance existante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], enregistrer une clé de DDEEXEC. L’exemple suivant illustre l’inscription d’une verbe standard pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] fichier .cs.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Définition de l’action par défaut  
 Le verbe par défaut est l’action qui est exécutée lorsqu’un utilisateur double-clique sur un fichier dans l’Explorateur Windows. Le verbe par défaut est le verbe spécifié en tant que la valeur par défaut pour le HKEY_CLASSES_ROOT\\*progid*\Shell clé. Si aucune valeur n’est spécifiée, le verbe par défaut est la première action spécifiée dans le HKEY_CLASSES_ROOT\\*progid*\Shell liste de clés.  
  
> [!NOTE]
>  Si vous envisagez de modifier l’action par défaut pour une extension dans un déploiement côte à côte, envisagez l’impact sur l’installation et la suppression. Lors de l’installation, la valeur par défaut d’origine est remplacée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)